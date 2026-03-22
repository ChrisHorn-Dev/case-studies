# Physician Connection Platform

## 1. Overview

Physician Connection (PC) is a multi-role web application for **appointment coordination and operational workflows** between **pharmaceutical representatives** and **physician practices**. It is not “a scheduling form.” It is a system for **rep–practice coordination**: who can request what, how practices review and confirm visits, how logistics hang off real calendar state, and how each role sees **only what they need** to move work forward.

Practices operate through **practice administrators** and **physicians**; the product also includes **super-admin** tooling for onboarding, integrations, and operational oversight.

The product has to work **for both sides**. **Reps** need **guided paths**, **explicit rules** (who can be booked for which visit type), and **reliable booking flows** so attempts do not dead-end in ambiguous state—fewer “did that go through?” loops and fewer surprise rejections after work is already sunk. **Practices** need coordination that is **structured and predictable**, with **clinical operations and patient care** treated as primary: rep visits should land as **acknowledged, queueable work** on the practice side, not as random inbound disruption. PC aligns those goals instead of pitting them against each other.

I contributed through the stretch where PC moved from **incomplete workflows and fragile hosting** toward **MVP-ready, launchable software**—the kind of state where the team could credibly put the product in front of **real physician offices**, not just internal testers.

**Code and history:** Work began in a **private organization repository** (`pc-next`), where much of the implementation history and collaboration lives. The product **continues in a private repository on my GitHub account** (`physician-connection`), and my contributions span **both** lineages. Nothing here is public; this write-up is for portfolio purposes and avoids proprietary schemas, credentials, and client-specific data.

---

## 2. Problem Context

Before PC, coordination often lived in **ad hoc channels**—email threads, disconnected calendars, and informal approvals. That fails in healthcare settings for reasons that go beyond “missing software”:

- **Front desks and clinical staff** are interrupt-driven. Unclear pending states, ambiguous ownership, and surprise bookings create **operational drag** and can pull attention away from **patient-facing work**.
- **Reps** pay a parallel cost: **unclear constraints** invite booking attempts that should never have started, **half-finished** flows waste time in the field, and **opaque status** turns into extra calls and messages to practices—noise for everyone.
- Reps, practice staff, and physicians need **different slices** of the same visit: what is requested, what needs approval, what is confirmed, and what still needs logistics follow-through (**hosted meals**, resources, etc.).
- **Scheduling** has to respect **who is allowed** to book, change, or cancel on behalf of a practice—without turning every exception into a manual rescue.

“Good” for this product meant:

- **Practices and physicians** could see **action vs done** clearly—in **dashboard and calendar** form—so coordination work queues naturally instead of spilling into side channels.
- **Reps** could move through **guided flows** with **visible prerequisites** (practice, visit type, required logistics) so successful bookings are **expected and acknowledged** on the practice side—not “maybe it went through” guesses.
- Rep requests did not strand users or leave **ambiguous partial state**; the system favored **fewer attempts, higher completion quality**, and **less back-and-forth** after submit.
- The system could **integrate with a scheduling engine** for availability and bookings while still owning **permissions, companies/practices, and invariants** in PC’s own data model.
- **Super-admins** could **seed, debug, and recover** integration state well enough to support **real office rollout**, not a single demo tenant.
- Behind all of that: **patient care stays central**—the product is designed so rep logistics do not become a constant disruption to how the office runs.

---

## 3. System Overview

PC is a **Next.js** application using the **App Router**, **React**, and **TypeScript**. The UI is organized by **role**, with route groups and layouts under a shared authenticated shell (`rep`, `physician`, `practice-admin`, `super-admin`).

**Primary surfaces (high level):**

- **Representative:** dashboards and calendars oriented to **pending work** and **upcoming visits**; a **multi-step appointment request** entry from global navigation; subscription gating for access.
- **Practice admin:** practice-level **calendar** and **dashboard**; tools tied to **visit logistics** (for example hosted-meal details surfaced on events); **office resources** shared as a role-appropriate surface.
- **Physician:** **calendar**, **dashboard**, **messaging**, and **connections**—scoped to what a physician should see and act on, without exposing unnecessary rep-side complexity.
- **Super-admin:** **analytics-style dashboard**, **user/company management**, **integrations** (including provisioning hooks for the scheduling integration), **error ingestion and resolution**, and **danger-zone** style operations where appropriate.

**Scheduling:** The product uses **Cal.com** as the scheduling engine (including embedded UI atoms for availability and connection flows), with **server-side booking APIs** and careful handling of **hosts**, **teams/event types**, and **metadata** on bookings (for example logistics fields that do not always round-trip through list endpoints). For launch readiness, Cal.com runs as a **self-hosted** deployment (see **Delivery** below), not only as a disconnected third-party sketch.

**Data and auth:** Application data is modeled in **PostgreSQL** (via **Neon**) using **Drizzle ORM**, with migrations and scripts for schema work and test seeding. Authentication and sessions use **Better Auth**, with **role-aware** server and client boundaries and **protected routes** enforced at the app layout and API layers.

**Delivery (current vs earlier):** The platform **previously ran** in a **private Oracle-hosted** environment. I helped **migrate the application off that setup** into a **more production-oriented model**: the **Next.js application on Vercel**, with **self-hosted Cal.com on Railway**. That migration was not a cosmetic hosting change—it was part of making the stack **easier to ship, observe, and support** as the product moved toward **MVP-ready deployment** and **real-office launch**. CI/release automation (for example **GitHub Actions**) remained part of how changes were validated and promoted; the shift was in **where and how** the running system lived.

---

## 4. Core Workflows

### A. Representative visit request (guided, resilient to partial state)

Reps initiate requests from **global navigation** using a **three-step dialog** before landing on the dedicated request page:

1. **Choose practice** — selects where the visit applies.
2. **Choose visit type** — distinguishes hosted-meal paths (with different confirmation rules) from a direct **physician meeting** path.
3. **Confirm or supply required logistics input** — for some hosted-meal paths, the flow requires a **group order link** (or equivalent) before continuing; the dialog only **redirects** to `/rep/request` after this step completes, so deep links and refreshes do not strand users mid-flow.

On the request page, the UI filters **who can be booked** based on practice and mode (for example **physicians vs practice admins** depending on visit type). Catering-related dialogs pass through **URL-derived parameters** so the request surface stays consistent with what the user confirmed in the nav flow.

That combination is deliberate: reps operate inside **clear guardrails** instead of guessing eligibility, and practices see requests that **match the path the rep completed**—closer to **warm, expected** coordination than surprise drop-ins.

This workflow matters because small ordering bugs (early redirect, missing params, wrong table columns for role) showed up as **production failures** on the rep side—and rep-side friction directly increases **random inbound pressure** on practices.

### B. Practice-side calendar operations and visit lifecycle

On the practice side, calendars must reflect **pending vs confirmed** reality and support **operational follow-through** without forcing staff to reverse-engineer state from email:

- Bookings move through states that matter for UX: **actionable pending**, **confirmed upcoming/past**, **expired**, etc. The product derives **lifecycle buckets** from booking status and normalized timestamps (including cases where end times must be inferred from duration).
- Event detail surfaces expose **logistics** that practices need at a glance; some fields depend on **merging** provider responses because metadata is not always returned consistently from list APIs.
- Practice admins sometimes need to act as **calendar host** for cancellation flows; the server-side booking layer includes **host-scoped cancellation** behavior aligned with the provider’s API, rather than assuming a single generic “delete booking” path.

The goal is **structured coordination**: practices can process visits in **chunks of real work**, with less ambiguity about what is waiting on them versus what is already settled.

### C. Cross-role coordination and notifications

Visit decisions and updates surface through **in-app notifications** and **messaging-capable** areas (physician-facing messaging exists as a first-class module). The intent is not “a chat app,” but **tight coupling** between **scheduling state** and **who needs to see what next**—so practices are not left inferring status from rep behavior, and reps get **signal instead of ping-pong** when something changes.

---

## 5. Architecture & Technical Design

**Application structure:** Feature code is split between **Next.js route segments** (role layouts and pages) and **modules** (for example a large **calendar** module with contexts, dialogs, DnD, and server actions). Calendar concerns are intentionally isolated behind **actions** and **types** so UI work does not scatter provider details everywhere.

**Auth model:** Better Auth is the **system of record for sessions**; the app combines that with **role checks** and server actions that validate **who can mutate** a booking or user record. A notable theme in hardening work was making failure modes **explicit**—redirects, toasts, and **permission retry** behavior rather than silent blank screens.

**Scheduling integration:** Cal.com is integrated at two levels: **embedded atoms** (loaded carefully—dynamic imports were required to avoid dev/runtime instability) and **server modules** that create bookings, manage teams/memberships, and normalize API quirks (for example host assignment rules: **physicians must remain host** for certain booking paths).

**Data layer:** Drizzle schemas and migrations back **user/practice/company** modeling. One meaningful evolution was **moving company records off a provider-centric representation into PC’s database** so the product could enforce invariants and admin workflows without being limited by what the scheduling provider exposes.

**Observability and supportability:** PC includes **client error reporting** plumbing, **server-side error logging**, and a **super-admin error log** with **resolution tracking** (including migration-backed fields where needed). That is part of **launch readiness**: when something breaks in a real office, the team can **triage and close the loop** instead of flying blind.

**Testing:** The codebase gained a **Vitest** unit suite and **Playwright** smoke coverage, with tests around **auth routing**, **booking helpers**, **dashboard data**, **subscription gating**, and **error log resolution**—guardrails on the areas that had already failed during hardening.

---

## 6. Key Engineering Contributions (what I owned)

The following is grounded in **commits authored by me** and the **implementation history** across the project’s **private repositories** (the original organization `pc-next` codebase and the continuing private **`physician-connection`** repository on my GitHub account). It is not a claim of sole ownership of the entire product; other engineers contributed substantially in the earlier organization repository.

**Rep-side product flows**

- Reworked the **representative request experience** into a **single, stepwise nav dialog** and aligned the **`/rep/request`** page so redirects only occur after the flow is actually complete; refactored shared dialog logic to reduce duplication between navigation and page-level entry points.
- Iterated on **catering / hosted-meal** request flows, including **office resources** entry points and calendar/detail surfaces needed for practice operators to see **catering context** on events.
- Adjusted **subscription gating** behavior (including a **time-bounded free access window** for new reps) so monetization rules did not block onboarding toward live use.

**Lifecycle-aware UX across dashboards**

- Refactored **rep, practice-admin, and physician dashboards** to be **action-first**: pending work and upcoming visits surfaced in ways that match how each role prioritizes tasks, backed by shared **appointment lifecycle** derivation logic.

**Scheduling integration hardening**

- Extended and fixed **Cal.com booking** utilities: **practice-admin cancellation as host**, **token recovery** tooling and **debug routes** (tightly scoped), and robustness around **metadata** and **calendar load** typing issues that were breaking **production builds**.
- Implemented **company migration** from a provider-centric model into **PC’s database**, plus **super-admin danger zone** hardening around destructive operations.

**Super-admin operational tooling**

- Built out **super-admin dashboard** sections (activity/analytics/quick actions) and expanded **error log** APIs and UI to **resolve** issues, not just record them.
- Added **integrations-oriented seeding/provisioning** support to make environments repeatable as the product approached real-office rollout.

**Infrastructure and delivery**

- Drove the move from the **Oracle-hosted** deployment model to **Vercel (Next.js app)** and **Railway (self-hosted Cal.com)** as part of pushing the product toward **MVP-ready, launchable hosting**—clearer promotion paths, better fit for the team’s operational reality, and a setup aligned with **production** rather than a bespoke private VM story.

**Quality, correctness, and release pressure**

- Added the initial **automated test suite** (unit + smoke e2e), tightened **auth** and **redirect** behavior, reduced **client-side noise**, and improved **error UX** (toasts, boundaries, logging providers) during the push toward launch readiness.
- Landed multiple **production build fixes** and **type tightenings** in calendar and notification code paths where “almost right” types were masking real nullability bugs.

---

## 7. Constraints & Tradeoffs

- **MVP scope:** The goal was not feature parity with every edge case in enterprise scheduling; it was **reliable execution** of the visit patterns real offices depend on, while keeping workflows **respectful of practice throughput**. That meant saying no to “nice-to-have” calendar features when they risked destabilizing core booking.
- **Provider coupling:** Cal.com is powerful but **opinionated**. We accepted integration complexity (hosts, teams, metadata inconsistencies) in exchange for not rebuilding scheduling from scratch under time pressure—while still **owning** practice/rep domain data in PC where it matters.
- **Operational realism vs polish:** We invested in **error logs, resolution workflows, and logging discipline** because **launch support** beats pixel-perfect marketing when something breaks during a real office pilot.
- **Dual sources of truth:** Moving **company** data into PC’s DB was an explicit trade: more application responsibility (migrations, admin tooling) for **clearer invariants** and less dependence on provider-side representations.
- **Hosting migration tradeoffs:** Moving off Oracle to Vercel/Railway improved **shipping and supportability**, but required disciplined handling of **environment configuration**, **integration endpoints**, and **release hygiene** so scheduling and app deploys did not drift.

---

## 8. System Maturity & Delivery

When I was contributing, PC was **past prototype** and actively moving toward **MVP-ready, real-office launch**—not “infinite internal iteration.”

The work was not generic cleanup. It included **substantial product and workflow engineering** (rep flows, practice-facing dashboards, lifecycle modeling, integration hardening) and **meaningful infrastructure migration** (Oracle-hosted environment → **Vercel + Railway**) so the product could sit in a **modern, supportable** hosting posture.

“Done” for that phase meant:

- Primary rep and practice flows were **coherent end-to-end** (request → booking → visibility on calendars/dashboards).
- Roles had **credible dashboards** that matched operational priority (pending vs upcoming vs historical): **practice-side clarity** on what needs action, and **rep-side clarity** on what is pending vs confirmed—so neither side is working from stale assumptions.
- The scheduling integration had **documented sharp edges** and **server behavior** that matched those edges (host rules, cancellations, metadata merges), with **self-hosted Cal.com** in the launch path.
- The platform had **basic automated tests** and **error visibility** suitable for **live operational use**, not just demos.
- Hosting and deploy paths matched **what a team can actually run and support** while onboarding **real physician offices**.

---

## 9. Lessons / Engineering Takeaways

- **Role-based SaaS** fails in the seams: navigation, redirects, and “blank screen” auth states are where users decide the product is broken. Fixing those is as important as feature work—especially when the buyer is a **busy practice**.
- **Scheduling providers** are integrations, not databases. If your product language talks about **companies, practices, and permissions**, you eventually need **your own model**—even if events still live in a provider.
- **Launch readiness** is **product + hosting + support**: migrating off a constrained private environment can be as important as UI polish when the goal is **real offices**, not a single controlled tenant.
- **Healthcare-adjacent coordination** needs an explicit **“do no harm to clinic throughput”** product stance: structured queues, clear ownership, and fewer surprise states beat raw “more features”—and **reps benefit** when those same structures remove ambiguity from their own workflows.

---

## Tech stack (factual summary)

Next.js (App Router) · React · TypeScript · Tailwind CSS · Drizzle ORM · PostgreSQL (Neon) · Better Auth · Cal.com (`@calcom/atoms` + server APIs; self-hosted on Railway) · Stripe (subscription gating) · Vitest · Playwright · GitHub Actions (CI / automation) · Vercel (application hosting)

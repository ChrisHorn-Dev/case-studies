# Brand Revamp Execution Plan

**Owner:** Chris Horn (`ChrisHorn-Dev`)  
**Last updated:** 2026-06-09  
**Purpose:** Per-project execution checklist for the personal branding revamp across GitHub, case studies, ChrisOS, LinkedIn, and resume materials.

**Canonical registry:** See `BRAND_PROJECT_REGISTRY.md` for machine-readable metadata.

---

## Global Status (2026-06-08 audit)

| Workstream | Completed | Pending |
|------------|-----------|---------|
| GitHub hygiene | Private repos created/pushed for `remember-me-app`, `regen-profits-sales-app`, `pathbound-mobile`; Elite Touch portal + proposals pushed | Push case-study drafts to public `case-studies` repo |
| README quality | Physician Connection root README, Visual Conversations README, ChrisHorn-Dev profile README updated | Genesis Mastery `.env.example` |
| ChrisOS content | Project cards + deep-dive stubs in `resume-os/content/projects.ts` | Deep-dive sections for flagship apps beyond media-auth-api |
| Case studies | Full: Physician Connection, Elite Touch, Cape Fear; Draft: SiteOS, Regen Profits, Remember Me, Media Auth API | Polish drafts; add user role + metrics placeholders |
| Screenshots | Scripts exist (Elite Touch, Physician Connection); `first-week-siteos` PNG bundle locally | Capture and commit marketing assets per `BRAND_ASSET_REQUESTS.md` |
| LinkedIn | — | Apply headline/About/Featured from `LINKEDIN_UPDATE_PACKET.md` |

---

## 1. Elite Touch Cleaning Companion App / Client Portal

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/elite-touch-client-portal` |
| **GitHub** | `https://github.com/ChrisHorn-Dev/elite-touch-client-portal` — **Private**, exists, synced |
| **Branch** | `production` |
| **Stack** | Next.js 15, React 19, TypeScript, Prisma, Twilio, Resend, HubSpot CRM API, Playwright |
| **Status** | MVP-ready / client ops |

### Tasks Completed
- [x] Private repo initialized and pushed (2026-06-08)
- [x] Published case study — `case-studies/elite-touch-cleaning.md`
- [x] ChrisOS featured card + case-study link in `resume-os/content/projects.ts`
- [x] Launch-readiness scripts (`check:launch-readiness`, `check:twilio`, Playwright e2e)
- [x] Mock integration mode for safe demos (`MOCK_INTEGRATIONS`)
- [x] Profile README featured section

### Tasks Pending
- [ ] Capture client launcher, SOS, admin queue screenshots
- [ ] Run `capture:sms-terms` and any remaining marketing captures
- [ ] Confirm production Postgres cutover documentation for client handoff
- [ ] Add Elite Touch Proposal App section cross-link polish in case study

### Screenshot Checklist
| # | View | Filename | Status |
|---|------|----------|--------|
| 1 | Client home / launcher | `elite-touch-01-client-launcher.png` | Pending |
| 2 | Request modal flow | `elite-touch-02-request-flow.png` | Pending |
| 3 | SOS emergency flow | `elite-touch-03-sos-flow.png` | Pending |
| 4 | Threaded messages | `elite-touch-04-message-thread.png` | Pending |
| 5 | Admin triage queue | `elite-touch-05-admin-queue.png` | Pending |
| 6 | Mobile client view | `elite-touch-06-mobile-client.png` | Optional |

### Case Study Angle
**Operations system, not a contact form.** Mobile-first client portal + admin ops layer replacing fragmented phone/email workflows with structured requests, separate feedback track, dedicated SOS pipeline, Twilio/Resend notification audit trail, and HubSpot sync.

### LinkedIn Angle
*"I built a service operations system for a commercial cleaning company — typed client requests, emergency SOS broadcasts, and an admin triage queue with SMS/email audit logging."*  
Emphasize: operational reliability, mockable integrations, mobile-first UX.

### ChrisOS Placement
- **Featured card** (flagship client work)
- Deep-dive sections: pending (stub exists)
- Link: case study on GitHub

### Privacy Notes
- **Private repo** — code never public
- Sanitize client names, phone numbers, SMS content in all screenshots
- Do not expose HubSpot tokens, Twilio credentials, or production `ADMIN_PASSWORD`
- Case study is architecture/implementation focused — no tenant data

---

## 2. Elite Touch Proposal App

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/elite-touch-proposals` |
| **GitHub** | `https://github.com/ChrisHorn-Dev/elite-touch-proposals` — **Private**, exists, synced |
| **Branch** | `master` |
| **Stack** | Next.js 16, Prisma, `@react-pdf/renderer`, NextAuth v5, Playwright |
| **Status** | Internal MVP |

### Tasks Completed
- [x] Private repo pushed (2026-06-08)
- [x] ChrisOS supporting card (non-featured) in `projects.ts`
- [x] Master audit and scope-catalog alignment docs in-repo
- [x] Neon/Vercel deployment path documented

### Tasks Pending
- [ ] PDF/proposal flow screenshots
- [ ] Dedicated case study section or appendix in Elite Touch study (outline pending)
- [ ] Playwright capture for branded PDF output

### Screenshot Checklist
| # | View | Filename | Status |
|---|------|----------|--------|
| 1 | Proposal dashboard | `elite-touch-proposals-01-dashboard.png` | Pending |
| 2 | PDF preview | `elite-touch-proposals-02-pdf-preview.png` | Optional |

### Case Study Angle
**Internal sales/onboarding accelerator** — structured scope-of-work data model, branded PDF generation, approval-oriented flows. Position as **companion** to client portal, not standalone flagship.

### LinkedIn Angle
Supporting mention under Elite Touch ecosystem post — *"paired with an internal proposal builder that generates branded scope-of-work PDFs."*

### ChrisOS Placement
- **Supporting card** (not featured)
- Links to Elite Touch client portal case study

### Privacy Notes
- Internal client tool — no public repo
- PDFs may contain client pricing — sanitize all proposal screenshots

---

## 3. Physician Connection

| Field | Value |
|-------|-------|
| **Local path (source of truth)** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/physician-connection` |
| **Related (do not duplicate in branding)** | `ServerlessPros/pc-next` (org duplicate), `cal-web-railway-deploy` (Cal.com transport mirror) |
| **GitHub** | `https://github.com/ChrisHorn-Dev/physician-connection` — **Private**, exists |
| **Branch** | `main` |
| **Stack** | Next.js 16, Drizzle ORM, Better Auth, Cal.com, PostgreSQL (Neon), Stripe, Sentry, Vercel, Railway |
| **Status** | Beta-ready |

### Tasks Completed
- [x] Published case study — `case-studies/physician-connection.md`
- [x] Root README upgraded (was 2/5, now actionable)
- [x] ChrisOS featured card
- [x] Demo capture script — `pnpm demo:capture`
- [x] Production hardening docs in `docs/` (auth, Cal.com, Neon transactions, migration)
- [x] Profile README featured section

### Tasks Pending
- [ ] Sanitized screenshots (rep dashboard, practice calendar, booking flow)
- [ ] Architecture diagram asset
- [ ] ChrisOS deep-dive sections (currently stub)
- [ ] Confirm public-safe wording for hosting migration narrative

### Screenshot Checklist
| # | View | Filename | Status |
|---|------|----------|--------|
| 1 | Rep dashboard | `physician-connection-01-rep-dashboard.png` | Pending |
| 2 | Practice calendar | `physician-connection-02-practice-calendar.png` | Pending |
| 3 | Booking flow | `physician-connection-03-booking-flow.png` | Pending |
| 4 | Super-admin | `physician-connection-04-super-admin.png` | Optional |
| 5 | Architecture diagram | `physician-connection-05-architecture.png` | Pending |

### Case Study Angle
**Healthcare multi-tenant SaaS** for rep–practice appointment coordination. Role-partitioned Next.js surfaces, Cal.com integration (self-hosted Railway), Drizzle on Neon, production stabilization toward real-office launch.

### LinkedIn Angle
*"Stabilized a healthcare scheduling SaaS from fragile workflows to beta-ready — multi-role dashboards, Cal.com integration, auth boundaries, and Oracle → Vercel/Railway migration."*

### ChrisOS Placement
- **Featured card**
- Deep-dive: media-auth-api and physician-connection have partial content; PC deep-dive stub pending expansion

### Privacy Notes
- **HIPAA-adjacent** — fully anonymize PHI, practice names, rep territories
- Private repo; `cal-web-railway-deploy` and `pc-next` are **not** for public branding
- Do not cite user counts or office counts without approval — use `[METRIC: practices onboarded]`

---

## 4. SiteOS

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/siteos` |
| **Related** | `siteos-signal-engine`, `first-week-siteos` (screenshot bundle) |
| **GitHub** | `https://github.com/ChrisHorn-Dev/siteos` — **Private**, exists |
| **Branch** | `main` |
| **Stack** | FastAPI, Celery, Redis, PostgreSQL/Supabase, TimescaleDB, Next.js 14, Expo, scikit-learn, YOLOv8, Claude API |
| **Status** | Active development / demo-ready areas |

### Tasks Completed
- [x] Draft case study — `case-studies/siteos.md`
- [x] ChrisOS featured card
- [x] Master audit plan + capability docs in `siteos/docs/audit/`
- [x] Docker-compose local full stack
- [x] Profile README featured section
- [x] `first-week-siteos` PNG bundle available locally for stakeholder email

### Tasks Pending
- [ ] Fill `[Needs user input]` role/timeline/metrics in case study draft
- [ ] Copy curated PNGs from `first-week-siteos` into case-studies assets
- [ ] Architecture diagram for public materials
- [ ] ChrisOS deep-dive content
- [ ] Signal engine flow diagram (subcomponent)

### Screenshot Checklist
| # | View | Filename | Status |
|---|------|----------|--------|
| 1 | Executive dashboard | `siteos-01-executive-dashboard.png` | Local ref in `first-week-siteos/` |
| 2 | Project intelligence | `siteos-02-project-intelligence.png` | Local ref |
| 3 | Signal engine view | `siteos-03-signal-engine.png` | Optional |
| 4 | Mobile field workflow | `siteos-04-mobile-field-workflow.png` | Pending |
| 5 | Architecture diagram | `siteos-05-architecture-diagram.png` | Pending |

### Case Study Angle
**Construction execution intelligence platform** — field signals to executive dashboards. Full-stack: FastAPI + Celery workers, TimescaleDB, multi-persona Next.js dashboards, Expo mobile, ML/CV and LLM-assisted workflows.

### LinkedIn Angle
*"Building SiteOS — a construction intelligence platform connecting field activity, project signals, and persona-specific dashboards across API services, workers, and mobile."*

### ChrisOS Placement
- **Featured card** (flagship R&D)
- Signal engine mentioned in card details, not separate flagship

### Privacy Notes
- Private repo — public proof via case study only
- Demo seed data only in screenshots
- Do not invent project counts or ROI — use `[METRIC: demo projects]` / `[METRIC: personas shipped]`

---

### 4a. SiteOS Signal Engine (subcomponent)

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/siteos-signal-engine` |
| **GitHub** | `https://github.com/ChrisHorn-Dev/siteos-signal-engine` — **Private** |
| **Stack** | Python 3.11+, FastAPI, SQLAlchemy, Alembic |
| **Status** | Foundation / early |

**Tasks Pending:** Signal flow diagram (`siteos-signal-engine-01-flow.png`). Covered in SiteOS case study — not a separate flagship.

---

### 4b. SiteOS First-Week Showcase Bundle

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/first-week-siteos` |
| **Git** | No repo (artifact folder) |
| **Role** | Screenshot source for SiteOS stakeholder materials |

**Tasks Pending:** Rename/copy PNGs to `siteos-01-*` convention; use in case study and LinkedIn.

---

## 5. Regen Profits Sales App

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/dev/regen-profits-sales-app` |
| **GitHub** | `https://github.com/ChrisHorn-Dev/regen-profits-sales-app` — **Private**, created 2026-06-08 |
| **Branch** | `main` |
| **Staging URL** | `https://regen-profits-sales-app.vercel.app` |
| **Stack** | Next.js 16, Supabase (`@supabase/ssr`), Tailwind v4, PWA |
| **Status** | Staging live — client review |

### Tasks Completed
- [x] Private repo created and initial push (2026-06-08)
- [x] Draft case study — `case-studies/regen-profits-sales-app.md`
- [x] ChrisOS featured card with staging link
- [x] Extensive QA/demo docs in `docs/`
- [x] `.env.example` only in repo (secret-safe push verified)

### Tasks Pending
- [ ] Client approval for anonymized public case study
- [ ] Confirm staging URL may be linked on LinkedIn
- [ ] Mobile rep dashboard + leaderboard screenshots
- [ ] Fill outcome placeholders in case study draft

### Screenshot Checklist
| # | View | Filename | Status |
|---|------|----------|--------|
| 1 | Mobile rep dashboard | `regen-profits-01-mobile-rep-dashboard.png` | Pending |
| 2 | Leaderboard | `regen-profits-02-leaderboard.png` | Pending |
| 3 | Sales entry | `regen-profits-03-sales-entry.png` | Pending |
| 4 | Admin command center | `regen-profits-04-admin-command-center.png` | Pending |
| 5 | PWA install prompt | `regen-profits-05-pwa-install.png` | Optional |

### Case Study Angle
**Mobile-first sales PWA** for distributed reps — dashboards, leaderboards, sales logging, admin command center. PWA-first to avoid app store cycle; Supabase RLS for rep vs admin boundaries.

### LinkedIn Angle
*"Shipped a mobile-first sales PWA on Vercel with Supabase auth — rep dashboards, leaderboards, and an admin command center for distributed team accountability."*  
Default to **anonymized** client naming.

### ChrisOS Placement
- **Featured card** with `staging` label and live staging URL
- Privacy label: "Client work — anonymize publicly"

### Privacy Notes
- **Client work** — confirm approval before public screenshots or naming
- Do not publish Supabase credentials or test passwords
- No invented rep counts — `[METRIC: active reps]` / `[METRIC: sales logged per week]`

---

## 6. Remember Me

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/remember-me-app` |
| **GitHub** | `https://github.com/ChrisHorn-Dev/remember-me-app` — **Private**, created 2026-06-08 |
| **Stack** | Next.js 16, Supabase SSR, Tailwind v4, localStorage demo mode |
| **Status** | MVP / demo mode |
| **Live URL** | `[DEPLOY URL — not verified at audit time]` |

### Tasks Completed
- [x] Private repo created and pushed (2026-06-08)
- [x] Draft case study — `case-studies/remember-me.md`
- [x] ChrisOS featured card
- [x] Demo mode (`/demo`) with honest Phase 1 scope disclaimers
- [x] Figma-aligned design tokens documented

### Tasks Pending
- [ ] Deploy demo environment and verify URL
- [ ] Landing, dashboard, Thinking of You flow screenshots
- [ ] Fill outcome placeholders in case study draft

### Screenshot Checklist
| # | View | Filename | Status |
|---|------|----------|--------|
| 1 | Landing page | `remember-me-01-landing.png` | Pending |
| 2 | Dashboard | `remember-me-02-dashboard.png` | Pending |
| 3 | Thinking of You flow | `remember-me-03-thinking-of-you.png` | Pending |
| 4 | Demo mode banner | `remember-me-04-demo-mode.png` | Optional |
| 5 | Mobile layout | `remember-me-05-mobile.png` | Pending |

### Case Study Angle
**Relationship gifting MVP** with honest scope — wishlists, reminders, events, Thinking of You drafts. No payments/delivery in Phase 1; demo mode for stakeholder walkthroughs without Supabase.

### LinkedIn Angle
*"Built Remember Me — a calm gifting MVP with honest Phase 1 boundaries, Supabase auth when configured, and a first-class demo mode for stakeholder walkthroughs."*

### ChrisOS Placement
- **Featured personal product** card
- Label: `mvp`

### Privacy Notes
- Personal product — safer to show UI than client work
- Demo mode uses localStorage — no real user data in `/demo` screenshots
- No user metrics — `[METRIC: beta signups]` if/when deployed

---

## 7. ChrisOS / resume-os

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/resume-os` |
| **GitHub** | `https://github.com/ChrisHorn-Dev/resume-os` — **Public** |
| **Live URL** | `https://chrisos.dev` |
| **Stack** | Next.js 16, Zustand, Framer Motion, Tailwind v4 |
| **Status** | Live public portfolio |

### Tasks Completed
- [x] Project cards updated in `content/projects.ts` (2026-06-08 revamp)
- [x] Deep-dive content for media-auth-api, physician-connection, chrisos
- [x] Mobile shell + desktop shell
- [x] Homepage updated on GitHub
- [x] Public repo README

### Tasks Pending
- [ ] Desktop + mobile shell marketing screenshots
- [ ] Expand deep-dive sections for SiteOS, Elite Touch, Regen Profits, Remember Me
- [ ] Project deep-dive screenshot for portfolio README

### Screenshot Checklist
| # | View | Filename | Status |
|---|------|----------|--------|
| 1 | Desktop shell | `chrisos-01-desktop-shell.png` | Pending |
| 2 | Mobile shell | `chrisos-02-mobile-shell.png` | Pending |
| 3 | Project deep dive | `chrisos-03-deep-dive.png` | Optional |

### Case Study Angle
**Interactive portfolio as product** — OS-inspired desktop shell, window manager, terminal, mobile launcher. Demonstrates frontend systems thinking and content/presentation decoupling.

### LinkedIn Angle
*"My portfolio is an app, not a PDF — ChrisOS at chrisos.dev treats projects, resume, and stack as first-class applications in a windowed shell."*

### ChrisOS Placement
- Self-referential — **Featured** on profile README and LinkedIn Featured #1

### Privacy Notes
- Public repo and live site — no client data
- Legacy private client cards (Thank You For Dying, Regal Rides, Ronald Wayne) show title/description only — no deep dives

---

## 8. Media Authenticity API

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/media-auth-api` |
| **GitHub** | `https://github.com/ChrisHorn-Dev/media-auth-api` — **Public** |
| **Stack** | Next.js API routes, TypeScript, Hugging Face Inference API, Vitest, HMAC-SHA256 signing |
| **Status** | Shipped public API |

### Tasks Completed
- [x] Public repository with tests
- [x] Case study overview — `case-studies/media-auth-api.md`
- [x] ChrisOS featured card + full deep-dive in `projectDeepDives.ts`
- [x] Built-in test UI for manual verification

### Tasks Pending
- [ ] README screenshots (test UI, verify response)
- [ ] API flow diagram asset
- [ ] `[METRIC: API requests]` if deployed with telemetry

### Screenshot Checklist
| # | View | Filename | Status |
|---|------|----------|--------|
| 1 | Test UI | `media-auth-01-test-ui.png` | Pending |
| 2 | API flow diagram | `media-auth-02-api-flow-diagram.png` | Pending |
| 3 | Verify response | `media-auth-03-verify-response.png` | Optional |

### Case Study Angle
**Verification-oriented media API** — detector registry, caching, HMAC-signed authenticity records, independent `POST /api/verify`. Public code as proof.

### LinkedIn Angle
*"Open-sourced a media authenticity API with signed responses — because teams need verifiable results, not just model scores."*

### ChrisOS Placement
- **Featured card** with public repo link
- **Full deep-dive** (only flagship with complete sections today)

### Privacy Notes
- Public — safe to link repo and show test UI
- Do not expose `SIGNING_SECRET` or API keys in screenshots

---

## 9. Cape Fear Web Co

| Field | Value |
|-------|-------|
| **Canonical local path** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/Cape-Fear-Web-Co-Web` |
| **Superseded** | `cape-fear-web-co-website` (older marketing-only — do not use) |
| **GitHub** | `https://github.com/ChrisHorn-Dev/Cape-Fear-Web-Co-Web` — **Private** |
| **Live URL** | `https://capefearweb.co` |
| **Stack** | Vite, React, TypeScript, Tailwind, TanStack Query, Supabase, Vercel Functions |
| **Status** | Live |

### Tasks Completed
- [x] Published case study — `case-studies/cape-fear-web-co.md`
- [x] ChrisOS featured card with live link
- [x] Build-time sitemap + JSON-LD
- [x] Site audit doc in-repo

### Tasks Pending
- [ ] Homepage hero screenshot
- [ ] Confirm case-study cross-links from live site `cases.ts`

### Screenshot Checklist
| # | View | Filename | Status |
|---|------|----------|--------|
| 1 | Homepage hero | `cape-fear-01-homepage-hero.png` | Pending |

### Case Study Angle
**Studio acquisition + delivery system** — marketing, SEO content cluster, typed case summaries linking to GitHub writeups, unified Vite SPA deploy.

### LinkedIn Angle
*"Built capefearweb.co as one system — marketing, SEO, and proof — with case summaries linking to public architecture writeups."*

### ChrisOS Placement
- **Featured card** with `live` label

### Privacy Notes
- Live public site — marketing content only
- Client names in cases are anonymized by design in `cases.ts`

---

## 10. Cape Fear Client Portal

| Field | Value |
|-------|-------|
| **Relationship** | Subproject of `Cape-Fear-Web-Co-Web` at `/portal/*` |
| **Separate GitHub repo** | No — documented in Cape Fear case study |
| **Stack** | Supabase Auth (magic link), Postgres RLS, Storage, Vercel `api/notify.ts` |
| **Status** | Live (companion to studio site) |

### Tasks Completed
- [x] Portal routes: messages, requests, files, activity feed
- [x] RLS + migrations in `supabase/migrations/`
- [x] Covered in Cape Fear case study delivery layer section

### Tasks Pending
- [ ] Sanitized portal screenshots (messages, requests)
- [ ] Confirm Resend notify path documented for ops

### Screenshot Checklist
| # | View | Filename | Status |
|---|------|----------|--------|
| 1 | Portal messages | `cape-fear-portal-01-messages.png` | Pending |
| 2 | Portal requests | `cape-fear-portal-02-requests.png` | Optional |

### Case Study Angle
**Delivery companion, not full SaaS** — structured client communication (threads, typed requests, files, activity) scoped honestly; contracts/invoices stay off-portal.

### LinkedIn Angle
Mention under Cape Fear post — *"authenticated /portal for messages, requests, and files — companion to delivery, not a billing replacement."*

### ChrisOS Placement
- Covered under Cape Fear Web Co card (not separate card)

### Privacy Notes
- Sanitize all client org names, project titles, file names
- Portal login is `noindex` — screenshots from test/staging org only

---

## 11. Genesis Mastery

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/genesis-mastery` |
| **GitHub** | `https://github.com/ChrisHorn-Dev/genesis-mastery` — **Private**, exists |
| **Stack** | Next.js 16, Prisma 7, NextAuth v5, PostgreSQL, shadcn/ui, Recharts |
| **Status** | Scaffold / EdTech MVP |

### Tasks Completed
- [x] Repo pushed
- [x] README with setup, seed, curriculum structure
- [x] ChrisOS optional card (non-featured)

### Tasks Pending
- [ ] Add `.env.example` to repo
- [ ] Promote on ChrisOS/LinkedIn only if polished
- [ ] Course admin CMS screenshots (optional)

### Screenshot Checklist
| # | View | Filename | Status |
|---|------|----------|--------|
| 1 | Course dashboard | `genesis-mastery-01-dashboard.png` | Optional |
| 2 | Lesson view | `genesis-mastery-02-lesson.png` | Optional |

### Case Study Angle
EdTech scaffold — Master's-level Genesis curriculum with quizzes, progress, discussions, instructor CMS. **Hold** until product-ready.

### LinkedIn Angle
Defer until polished — or brief *"building an interactive theology curriculum platform"* without overclaiming.

### ChrisOS Placement
- Optional non-featured card
- Label: `private`, status: Scaffold

### Privacy Notes
- EdTech content — no public repo
- Seeded demo users only in screenshots

---

## 12. Wilmington Engine

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/wilmington-news` |
| **Aliases** | `wilmington-engine`, WilmingtonEngine |
| **GitHub** | Private — exists |
| **Stack** | Next.js monorepo, Neon, pipeline workers |
| **Status** | Experimental / automation R&D (pre-build audit v0.1) |

### Tasks Completed
- [x] Master audit planning package in `docs/`
- [x] ChrisOS experimental card (non-featured)

### Tasks Pending
- [ ] Keep private — do not overemphasize in public brand
- [ ] Optional lab card only if/when Phase 1 ships

### Screenshot Checklist
Defer — optional `wilmington-engine-01-pipeline.png` only if promoted.

### Case Study Angle
**Personal lab** — policy-driven local media automation engine. Pre-build audit complete; media company first, software second.

### LinkedIn Angle
Do not feature in 30-day plan unless Phase 1 milestone reached.

### ChrisOS Placement
- Experimental non-featured card
- Privacy label: "Experimental automation"

### Privacy Notes
- Keep private; no public case study
- Automation/scraping narratives need careful public framing

---

## 13. Visual Conversations

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/visual-conversations` |
| **Package name** | `ui-intent-assistant` |
| **GitHub** | Private — exists |
| **Stack** | TypeScript, Chrome Extension MV3, OpenAI API, Node CLI (`tsx`) |
| **Status** | Experimental dev tool |

### Tasks Completed
- [x] README added in brand revamp (was 1/5)
- [x] ChrisOS experimental card

### Tasks Pending
- [ ] Extension popup + CLI output screenshots
- [ ] Add `.env.example` if missing

### Screenshot Checklist
| # | View | Filename | Status |
|---|------|----------|--------|
| 1 | Extension popup | `visual-conversations-01-extension-popup.png` | Optional |
| 2 | CLI session | `visual-conversations-02-cli-session.png` | Optional |

### Case Study Angle
Experimental UI intent assistant — DOM-aware Chrome extension + CLI with pluggable LLM brain layer.

### LinkedIn Angle
Optional dev-tool post — *"experimenting with a Chrome extension that captures UI context for intent-aware dev workflows."*

### ChrisOS Placement
- Experimental non-featured card

### Privacy Notes
- Never show `OPENAI_API_KEY`
- DOM digests may contain page content — use localhost demo pages only

---

## 14. Pathbound Mobile

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/pathbound-mobile` |
| **GitHub** | `https://github.com/ChrisHorn-Dev/pathbound-mobile` — **Private**, created 2026-06-08 |
| **Stack** | Godot 4.6+ (active), GDScript; Expo prototype archived |
| **Status** | In progress game lab — Haven Clearing vertical slice |

### Tasks Completed
- [x] Private repo created and pushed (2026-06-08)
- [x] Godot foundation scripts, map composer tooling, master audit
- [x] ChrisOS experimental card
- [x] `.env` gitignored — safe push verified

### Tasks Pending
- [ ] Gameplay GIF if promoted
- [ ] Gate milestones per `docs/gates/`

### Screenshot Checklist
| # | View | Filename | Status |
|---|------|----------|--------|
| 1 | Gameplay loop | `pathbound-01-gameplay.gif` | Optional |
| 2 | Haven Clearing map | `pathbound-02-haven-clearing.png` | Optional |

### Case Study Angle
Personal game lab — dark-fantasy 2D top-down MMO-lite. Godot pivot from archived Expo prototype; map composer + PixelLab art pipeline.

### LinkedIn Angle
Optional personality signal — *"side project: building a Godot 4 top-down RPG prototype with procedural dungeon tooling."*

### ChrisOS Placement
- Experimental non-featured card
- Privacy label: "Personal game lab"

### Privacy Notes
- Private repo
- Third-party asset licenses documented in `assets/licenses/`

---

## 15. Other Projects & Infrastructure

### 15a. case-studies (public repo)

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/case-studies` |
| **GitHub** | `https://github.com/ChrisHorn-Dev/case-studies` — **Public** |
| **Role** | Public proof channel for private work |

**Completed:** README index, full studies (PC, Elite Touch, Cape Fear), drafts (SiteOS, Regen, Remember Me, Media Auth)  
**Pending:** Push draft updates; add asset folder for screenshots; link from all ChrisOS cards

---

### 15b. ChrisHorn-Dev (profile README)

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/ChrisHorn-Dev/ChrisHorn-Dev` |
| **GitHub** | `https://github.com/ChrisHorn-Dev/ChrisHorn-Dev` — **Public** |

**Completed:** Featured work sections, stack, case-study links (2026-06-08 revamp)  
**Pending:** Add screenshot badges when assets land; sync Featured order with LinkedIn packet

---

### 15c. style-sculptors-inc

| Field | Value |
|-------|-------|
| **GitHub** | Private, **archived** |
| **Public-brand role** | Deprioritize — do not feature |

**Action:** No case study, no LinkedIn posts, no ChrisOS card.

---

### 15d. rsps-lab

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/rsps-lab` |
| **Git** | Submodules only (no root repo) |
| **Public-brand role** | Personal lab — not professional flagship |

**Action:** Omit from LinkedIn Featured; optional mention only if RuneScape private server hobby is desired.

---

### 15e. cal-web-railway-deploy

| Field | Value |
|-------|-------|
| **Relationship** | Physician Connection Cal.com transport mirror |
| **Public-brand role** | Archive/deprioritize |

**Action:** Document in PC case study only; never duplicate as standalone brand item.

---

### 15f. pc-next (ServerlessPros)

| Field | Value |
|-------|-------|
| **Local path** | `/Users/chorn/Desktop/Local-Dev/ServerlessPros/pc-next` |
| **Remote** | `ServerlessPros/pc-next` |
| **Public-brand role** | Org duplicate — not ChrisHorn-Dev source of truth |

**Action:** All branding points to `physician-connection` only.

---

### 15g. Legacy ChrisOS Private Client Cards

| Project | ChrisOS card | Public case study |
|---------|--------------|-------------------|
| Thank You For Dying | Yes (private) | No |
| Regal Rides | Yes (private) | No |
| Ronald G. Wayne Website | Yes (private) | No |

**Action:** Keep as private cards showing title/stack only. No screenshots, no LinkedIn posts, no resume bullets unless user explicitly requests.

---

## Execution Priority Queue

| Priority | Action | Projects |
|----------|--------|----------|
| P0 | Capture required screenshots | Elite Touch, Physician Connection, SiteOS (from `first-week-siteos`), ChrisOS |
| P0 | Client approval for public materials | Regen Profits |
| P1 | Polish and publish case study drafts | SiteOS, Regen Profits, Remember Me |
| P1 | Apply LinkedIn packet | Profile-wide |
| P2 | Expand ChrisOS deep-dives | SiteOS, Elite Touch, PC |
| P3 | Optional lab promotion | Pathbound, Visual Conversations, Genesis, Wilmington |

---

## Cross-Reference Index

| Document | Purpose |
|----------|---------|
| `BRAND_PROJECT_REGISTRY.md` | Canonical metadata |
| `BRAND_ASSET_REQUESTS.md` | Asset filenames and destinations |
| `LINKEDIN_UPDATE_PACKET.md` | Headlines, About, 30-day content plan |
| `RESUME_PROJECT_BULLET_BANK.md` | Resume bullets per app |
| `case-studies/` | Public architecture proof |

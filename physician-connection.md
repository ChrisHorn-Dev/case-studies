# Physician Connection Platform

## 1. Overview

Physician Connection (PC) is a multi-role web application for **appointment coordination and operational workflows** between **pharmaceutical representatives** and **physician practices**.

This is not a simple scheduling interface — it is a system for **rep–practice coordination**: who can request what, how practices review and confirm visits, how logistics attach to real calendar state, and how each role sees only what they need to move work forward.

Practices operate through **practice administrators** and **physicians**, while **super-admin tooling** supports onboarding, integrations, and operational oversight.

I contributed during the phase where PC moved from **incomplete workflows and fragile hosting** to **MVP-ready, launchable software** — the point where the system could be used by **real physician offices**, not just internal testers.

**Code and history:** Work began in a private organization repository and continues in a private repository on my GitHub. This write-up is non-proprietary and focuses on system design and engineering decisions.

---

## 2. Problem Context

Before PC, coordination lived in **fragmented systems** — email threads, disconnected calendars, and informal approvals.

This created real-world problems:

- **Practice staff** operate in interrupt-heavy environments — unclear requests and ambiguous states create operational drag and interfere with patient care  
- **Reps** face unclear constraints, wasted booking attempts, and poor visibility into outcomes  
- Different roles require **different views of the same visit lifecycle**  
- Scheduling must respect **permissions and ownership**, not just availability  

The system needed to:

- Provide **structured, predictable workflows** for practices  
- Give reps **guided, constraint-aware booking paths**  
- Eliminate ambiguous or partial states  
- Integrate with a scheduling engine while maintaining **domain ownership** in PC  
- Support **real-world rollout**, not just demo usage  

---

## 3. System Overview

PC is built with **Next.js (App Router)**, **React**, and **TypeScript**, with role-based UI segmentation.

### Core surfaces

- **Representative:** guided request flows, dashboards, and calendars  
- **Practice admin:** lifecycle visibility, scheduling oversight, operational tools  
- **Physician:** scoped calendar, messaging, and connections  
- **Super-admin:** user/company management, integrations, error handling, and system controls  

### Scheduling

- Powered by **Cal.com** (embedded UI + server APIs)  
- Handles teams, hosts, event types, and metadata  
- Self-hosted via **Railway** for production control  

### Data & Auth

- **PostgreSQL (Neon)** with **Drizzle ORM**  
- **Better Auth** for sessions and role-based access  
- Server actions enforce mutation boundaries  

### Infrastructure

- Migrated from **Oracle-hosted environment** → **Vercel (app) + Railway (Cal.com)**  
- Improved deployability, observability, and operational support  

---

## 4. Core Workflows

### Representative request flow

- Multi-step guided flow:
  1. Select practice  
  2. Select visit type  
  3. Provide required logistics  

- Redirect only occurs after completion → prevents partial state  
- UI filters valid booking targets  

**Goal:** reduce failed attempts and eliminate ambiguity  

---

### Practice-side lifecycle management

- Booking states: pending, confirmed, expired  
- Lifecycle derived from timestamps and provider state  
- Event detail surfaces include operational context  
- Admins can act as host when required  

**Goal:** convert inbound requests into structured work queues  

---

### Cross-role coordination

- Notifications and messaging tied to scheduling state  

**Goal:** reduce coordination overhead  

---

## 5. Architecture & Technical Design

- Feature isolation through modules (e.g. calendar system)  
- Server actions abstract provider complexity  
- Role-based auth enforced at mutation boundaries  

### Scheduling integration

- Embedded UI required dynamic loading fixes  
- Server utilities normalize API inconsistencies  
- Host rules enforced explicitly  

### Data model evolution

- Company/practice data moved into PC database  

### Observability

- Server + client error reporting  
- Super-admin error logs with resolution tracking  

### Testing

- **Vitest** (unit)  
- **Playwright** (smoke e2e)  

---

## 6. Key Engineering Contributions

- Rebuilt rep request flow into structured, step-based system  
- Refactored dashboards to surface actionable state  
- Fixed scheduling integration issues (host logic, metadata handling)  
- Migrated company data into PC database  
- Built super-admin tooling for error handling and provisioning  
- Led migration from Oracle → Vercel + Railway  
- Added test coverage and resolved production build/type issues  

---

## 7. Production Hardening (Critical Work)

The following work cut across multiple areas above and focused specifically on stabilizing the system for real-world use.

### Database transaction failures (Neon + Drizzle)

Using Drizzle ORM’s `transaction()` API with Neon’s HTTP driver caused failures because the HTTP driver does not support interactive transactions.

**Symptoms:**
- Hard-to-diagnose failures in production (e.g. generic Next.js digest errors)  
- Delayed failures on multi-step operations  
- Inconsistent behavior across execution paths  

**Resolution:**
- Replaced transactional patterns with **sequential database operations**  
- Added **failure-safe cleanup logic** for partial writes  
- Reserved use of `transaction()` only where supported (e.g. Cal Postgres pool), not on the Neon HTTP app DB  

---

### Authentication boundary issues

**Resolution:**
- Enforced explicit session validation on server actions  
- Removed invalid server-side auth flows  
- Strengthened role-based access boundaries  

---

### Observability gaps

**Resolution:**
- Added **targeted Sentry capture** on critical server paths (e.g. provisioning, practice setup, Cal proxy)  
- Improved logging and surfaced errors through admin tooling  
- Reduced opaque failure states  

---

### External dependency stabilization (Cal.com)

**Resolution:**
- Hardened booking logic to match provider constraints  
- Added fallback and debugging paths  
- Aligned system behavior with real provider responses  

---

### Outcome

The system transitioned from:

> feature-complete but unstable  

to:

> stable, observable, and ready for controlled beta  

---

## 8. Constraints & Tradeoffs

- Prioritized reliability over feature breadth  
- Accepted provider complexity instead of rebuilding scheduling  
- Focused on operational support over polish  
- Introduced dual data ownership for stronger invariants  
- Required disciplined deployment after infrastructure migration  

---

## 9. System Maturity & Delivery

At this stage, the system:

- Supports full rep → practice workflows  
- Provides role-appropriate dashboards  
- Handles scheduling integration realistically  
- Includes testing and observability  
- Runs on production-aligned infrastructure  

---

## 10. Lessons Learned

- Most failures occur at system boundaries, not features  
- Scheduling providers require adaptation, not assumption  
- Production readiness includes observability and support  
- Predictability matters more than flexibility in real workflows  

---

## Tech Stack

Next.js · React · TypeScript · Tailwind CSS  
Drizzle ORM · PostgreSQL (Neon) · Better Auth  
Cal.com (self-hosted) · Stripe  
Vitest · Playwright · GitHub Actions  
Vercel · Railway

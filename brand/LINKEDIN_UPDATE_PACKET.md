# LinkedIn Update Packet

**Owner:** Chris Horn  
**Last updated:** 2026-06-09  
**Status:** Draft — review before publishing  
**Profile:** [linkedin.com/in/chris-horn-5b70ab369](https://linkedin.com/in/chris-horn-5b70ab369)

**Rule:** Do not publish invented metrics. Replace `[METRIC: …]` and `[DRAFT]` placeholders before posting.

---

## Base Headline

```
Product-Minded Full-Stack Engineer · SaaS Platforms & Operational Systems · Next.js · TypeScript · Python
```

---

## Headline Variants (pick one)

### Variant 1 — Base (recommended default)
```
Product-Minded Full-Stack Engineer · SaaS Platforms & Operational Systems · Next.js · TypeScript · Python
```

### Variant 2 — Healthcare + ops emphasis
```
Full-Stack Engineer · Healthcare SaaS & Client Operations Platforms · Next.js · TypeScript · FastAPI
```

### Variant 3 — Construction intelligence hook
```
Product-Minded Engineer · SaaS & Operational Systems · SiteOS · Next.js · TypeScript · Python · FastAPI
```

### Variant 4 — Studio + client delivery
```
Full-Stack Engineer · Custom SaaS · Client Portals & Workflow Systems · Next.js · Supabase · TypeScript
```

### Variant 5 — Public proof angle
```
Full-Stack Engineer · Private SaaS, Public Architecture · Case Studies at chrisos.dev · Next.js · TypeScript
```

---

## About Section — Draft A (recommended)

**[DRAFT]**

I build SaaS platforms and operational systems — the kind of software that replaces phone calls, spreadsheets, and ambiguous workflows with structured data, clear roles, and reliable notifications.

Most of my strongest work lives in **private repositories** (healthcare scheduling, client ops portals, construction intelligence, sales PWAs). I publish **architecture-focused case studies** and an interactive portfolio at [chrisos.dev](https://chrisos.dev) so technical peers and hiring managers can see how I think about product, system design, and tradeoffs — without exposing client code.

**What I work on:**
- Multi-tenant SaaS with role-based surfaces (reps, admins, clients, super-admins)
- Client and operations portals with SMS/email integrations (Twilio, Resend, HubSpot)
- Full-stack platforms spanning Next.js frontends, FastAPI/Celery backends, Supabase/Neon/Prisma data layers
- Scheduling and workflow systems (Cal.com, Better Auth, Drizzle ORM)
- Public APIs with verifiable responses (Media Authenticity API — open source)

**Stack:** Next.js · React · TypeScript · Python · FastAPI · PostgreSQL · Supabase · Prisma · Drizzle · Vercel · Railway

**Links:**
- Portfolio: [chrisos.dev](https://chrisos.dev)
- Case studies: [github.com/ChrisHorn-Dev/case-studies](https://github.com/ChrisHorn-Dev/case-studies)
- Open source: [github.com/ChrisHorn-Dev/media-auth-api](https://github.com/ChrisHorn-Dev/media-auth-api)

Open to conversations about SaaS systems, operational software, and product engineering.

---

## About Section — Draft B (shorter)

**[DRAFT]**

Full-stack engineer focused on **SaaS platforms and operational systems** — client portals, healthcare scheduling, construction intelligence, and sales tooling.

A lot of my work is private or client-sensitive, so I share **public architecture case studies** and an interactive portfolio at [chrisos.dev](https://chrisos.dev).

**Stack:** Next.js · TypeScript · Python · FastAPI · PostgreSQL · Supabase · Prisma · Drizzle · Celery · Vercel

**Featured work:** Physician Connection (healthcare SaaS) · SiteOS (construction intelligence) · Elite Touch ops portal · Cape Fear Web Co · Media Authenticity API (public)

---

## About Section — Draft C (product-minded narrative)

**[DRAFT]**

I care about the gap between "we need an app" and "we need a system." Phone calls don't scale. Spreadsheets don't notify anyone. Email threads aren't auditable. I build software that makes operational work **explicit, structured, and recoverable**.

Recent focus areas:
- **Healthcare SaaS** — rep–practice scheduling with Cal.com, multi-role dashboards, production hardening
- **Service operations** — mobile client portals with SOS paths, admin triage, Twilio/Resend audit trails
- **Construction intelligence** — FastAPI + Celery platform with multi-persona dashboards and field mobile
- **Studio delivery** — marketing site + Supabase client portal as one coherent system (capefearweb.co)

I also ship public proof: open-source [Media Authenticity API](https://github.com/ChrisHorn-Dev/media-auth-api) and case studies for private work at [github.com/ChrisHorn-Dev/case-studies](https://github.com/ChrisHorn-Dev/case-studies).

Portfolio: [chrisos.dev](https://chrisos.dev)

---

## Featured Section — Recommended Order

| # | Title | URL | Type |
|---|-------|-----|------|
| 1 | ChrisOS — Interactive Portfolio | `https://chrisos.dev` | Live site |
| 2 | Case Studies — Public Architecture Writeups | `https://github.com/ChrisHorn-Dev/case-studies` | GitHub repo |
| 3 | Physician Connection — Case Study | `https://github.com/ChrisHorn-Dev/case-studies/blob/main/physician-connection.md` | Case study |
| 4 | Elite Touch Cleaning — Case Study | `https://github.com/ChrisHorn-Dev/case-studies/blob/main/elite-touch-cleaning.md` | Case study |
| 5 | Media Authenticity API | `https://github.com/ChrisHorn-Dev/media-auth-api` | Public repo |
| 6 | Cape Fear Web Co | `https://capefearweb.co` | Live site |
| 7 | SiteOS — Case Study (draft) | `https://github.com/ChrisHorn-Dev/case-studies/blob/main/siteos.md` | Case study |
| 8 | Regen Profits Sales App (staging) | `https://regen-profits-sales-app.vercel.app` | Staging — confirm client approval before featuring |

**Defer:** Remember Me (until deploy URL verified), Pathbound, Visual Conversations, Genesis, Wilmington Engine.

---

## Experience Bullets — Per App

Use under current role or "Selected Projects" custom section. All `[METRIC]` placeholders require real data.

### Physician Connection
- Stabilized multi-tenant healthcare SaaS (Next.js 16, Drizzle, Better Auth, Cal.com) from fragile workflows toward beta-ready launch for real physician offices
- Implemented role-partitioned surfaces for pharmaceutical reps, practice admins, physicians, and super-admins with explicit access boundaries
- Hardened Cal.com integration on self-hosted Railway stack; improved Neon/Drizzle transaction reliability and Sentry observability on critical paths
- Led hosting migration from legacy Oracle deployment toward Vercel + Railway architecture documented for controlled rollout
- **[METRIC: practices in beta]** · **[METRIC: scheduling requests processed]**

### SiteOS
- Building construction execution intelligence platform — FastAPI, Celery, Redis, PostgreSQL/TimescaleDB, multi-persona Next.js dashboards, Expo mobile field app
- Architected signal ingestion pipeline with county-level foundation service (`siteos-signal-engine`) for continuity scoring and project intelligence
- Integrated ML/CV (scikit-learn, YOLOv8) and Claude API workflows for document analysis and operational prediction surfaces
- Maintained demo-ready Docker-compose full stack with audit documentation and stakeholder screenshot deliverables
- **[METRIC: personas/dashboards shipped]** · **[METRIC: demo projects seeded]**

### Elite Touch Cleaning Companion App
- Built mobile-first client portal + admin ops layer replacing fragmented phone/email workflows with structured Prisma-backed requests
- Designed separate SOS emergency pipeline with distinct priority, notification fan-out, and audit logging via `NotificationEvent` persistence
- Integrated Twilio SMS and Resend email with `MOCK_INTEGRATIONS` mode for safe demos; HubSpot CRM read/sync path for client records
- Shipped Playwright e2e smoke suite and launch-readiness verification scripts for client handoff confidence
- **[METRIC: request types supported]** · **[METRIC: notification channels]**

### Elite Touch Proposal App
- Built internal proposal builder (Next.js 16, Prisma, `@react-pdf/renderer`) generating branded scope-of-work PDFs for sales and onboarding
- Structured proposal data model with NextAuth v5 and Playwright e2e coverage for critical document flows

### Regen Profits Sales App
- Delivered mobile-first sales PWA (Next.js 16, Supabase SSR, Tailwind v4) with rep dashboards, leaderboards, and admin command center
- Implemented Supabase Auth with row-level security boundaries between rep and admin roles
- Deployed staging environment on Vercel (`regen-profits-sales-app.vercel.app`) with documented QA checklists for client review
- **[METRIC: active reps]** · **[METRIC: staging review status]** — confirm client approval before citing

### Remember Me
- Built Phase 1 relationship gifting MVP (Next.js 16, Supabase) — wishlists, reminders, events, Thinking of You drafts with honest scope boundaries
- Implemented first-class demo mode (`/demo`) with localStorage store for stakeholder walkthroughs without backend dependency
- Aligned UI to Figma design tokens; documented Phase 1 exclusions (no payments, no delivery) in product copy

### ChrisOS / resume-os
- Designed and shipped interactive desktop-style portfolio (Next.js 16, Zustand, Framer Motion) at chrisos.dev — window manager, terminal, mobile shell
- Decoupled project content from presentation via structured `content/projects.ts` and deep-dive model for architecture storytelling

### Media Authenticity API
- Open-sourced image authenticity API with Hugging Face detector registry, TTL caching, and HMAC-SHA256 signed records
- Built independent `POST /api/verify` endpoint so downstream systems can confirm results were not tampered with
- Vitest coverage for analyze and verify paths; built-in test UI for manual integration testing

### Cape Fear Web Co + Client Portal
- Built live studio site (Vite, React, Supabase) at capefearweb.co — marketing, SEO (JSON-LD, sitemap), blog, typed case summaries
- Implemented Supabase-backed `/portal` delivery layer: threaded messages, typed client requests, file storage, activity feed, RLS
- Vercel serverless notify API with JWT-verified Resend email glue; portal scoped as delivery companion, not billing replacement

### Genesis Mastery
- Scaffolded EdTech platform (Next.js 16, Prisma 7, NextAuth v5) for interactive Genesis curriculum — quizzes, progress, instructor CMS

### Wilmington Engine
- Authored pre-build audit and architecture planning package for policy-driven local media automation engine (Next.js monorepo, Neon, pipeline workers)

### Visual Conversations
- Built experimental UI intent assistant — Chrome Extension MV3 + TypeScript CLI with pluggable OpenAI brain layer and session store

### Pathbound Mobile
- Active Godot 4.6+ development for dark-fantasy 2D top-down prototype; archived Expo exploration; map composer tooling and art pipeline docs

---

## Skills List (LinkedIn — top 50 ordered by relevance)

**Primary (pin top 3):** Next.js · TypeScript · React

**Full list — copy/paste and trim to 50:**

```
Next.js
TypeScript
React
Node.js
Python
FastAPI
PostgreSQL
Supabase
Prisma
Drizzle ORM
Tailwind CSS
SaaS Development
Full-Stack Development
System Architecture
API Development
Progressive Web Apps (PWA)
Celery
Redis
Vercel
Railway
Docker
Better Auth
NextAuth
Cal.com
Twilio
Resend
HubSpot
Stripe
Sentry
Expo
React Native
Vitest
Playwright
Hugging Face
Machine Learning
Framer Motion
Zustand
Vite
TanStack Query
SQL
Row-Level Security (RLS)
Healthcare IT
Operational Systems
Product Engineering
Technical Writing
Case Studies
Godot
GDScript
Chrome Extensions
OpenAI API
```

---

## 30-Day Content Plan

**Cadence:** 2 posts/week (8 total) + 1 optional personality/lab post  
**Format:** Text + image (screenshot or diagram) or carousel for architecture posts  
**Hashtags (use sparingly, 3–5 max):** `#SaaS` `#NextJS` `#TypeScript` `#FullStack` `#HealthTech` `#ConstructionTech` `#ProductEngineering`

---

### Week 1

#### Post 1 — ChrisOS launch / portfolio refresh [DRAFT]
**Day:** Mon  
**Asset:** `chrisos-01-desktop-shell.png`

```
I rebuilt my portfolio as an app, not a PDF.

ChrisOS (chrisos.dev) is a desktop-style interface in the browser — window manager, dock, terminal, and a mobile shell that share the same project model.

Why? Static resumes flatten systems thinking. I wanted a front door that shows how I approach product surfaces, shared state, and architecture storytelling.

Built with Next.js 16, Zustand, and Framer Motion. Project deep dives link to public case studies for private SaaS work.

→ chrisos.dev
→ github.com/ChrisHorn-Dev/resume-os

#NextJS #TypeScript #ProductEngineering
```

#### Post 2 — Private SaaS, public proof [DRAFT]
**Day:** Thu  
**Asset:** `case-studies-02-proof-model.svg` or case studies README screenshot

```
A lot of my strongest work can't be open-sourced — healthcare clients, service ops, construction platforms.

So I publish architecture case studies instead of code dumps.

New index: github.com/ChrisHorn-Dev/case-studies

Each write-up covers:
→ Problem context (what was actually broken)
→ System architecture (stack, boundaries, integrations)
→ Engineering decisions and tradeoffs
→ Honest scope (what's shipped vs scaffolded)

No invented metrics. No proprietary implementation details.

If you're evaluating engineers who've shipped real operational software, this is how I show the work.

#SaaS #SystemArchitecture #FullStack
```

---

### Week 2

#### Post 3 — Physician Connection [DRAFT]
**Day:** Mon  
**Asset:** `physician-connection-01-rep-dashboard.png` + `physician-connection-05-architecture.png`

```
Healthcare scheduling is not "pick a time slot."

For Physician Connection, I worked on a multi-tenant SaaS coordinating pharmaceutical reps and physician practices — different roles, different views of the same visit lifecycle, and scheduling that respects permissions—not just availability.

Stack: Next.js 16 · Drizzle ORM · Better Auth · Cal.com (self-hosted) · Neon · Vercel · Railway

Work included production hardening — auth boundaries, database transaction fixes, Cal.com stabilization, and hosting migration toward beta-ready rollout.

Full architecture write-up (no proprietary code):
→ github.com/ChrisHorn-Dev/case-studies/blob/main/physician-connection.md

[METRIC: practices in beta] — add when approved for public citation.

#HealthTech #SaaS #NextJS
```

#### Post 4 — Elite Touch operations system [DRAFT]
**Day:** Thu  
**Asset:** `elite-touch-03-sos-flow.png` or `elite-touch-05-admin-queue.png`

```
This isn't a contact form. It's a service operations system.

For a commercial cleaning company, I built:
→ Mobile-first client portal with typed requests (issues, notes, supplies, feedback)
→ A separate SOS path for emergencies — own priority, own notification pipeline
→ Admin triage queue with threaded messages and attachment support
→ Twilio SMS + Resend email with per-recipient audit logging

Stack: Next.js 15 · Prisma · Twilio · Resend · HubSpot

Mock integration mode lets us demo safely without hitting production SMS.

Case study: github.com/ChrisHorn-Dev/case-studies/blob/main/elite-touch-cleaning.md

#SaaS #OperationalSystems #TypeScript
```

---

### Week 3

#### Post 5 — SiteOS construction intelligence [DRAFT]
**Day:** Mon  
**Asset:** `siteos-01-executive-dashboard.png`

```
Construction ops data is fragmented — spreadsheets, delayed RFIs, executive views that lag field reality.

I'm building SiteOS: a construction execution intelligence platform connecting field signals to persona-specific dashboards.

Architecture spans:
→ FastAPI + Celery workers
→ PostgreSQL / TimescaleDB
→ Next.js multi-persona dashboards
→ Expo mobile field app
→ ML/CV + Claude API integration points
→ County-level signal engine (separate FastAPI microservice)

Draft case study: github.com/ChrisHorn-Dev/case-studies/blob/main/siteos.md

[METRIC: dashboards shipped] — placeholder until confirmed.

#ConstructionTech #Python #FastAPI #NextJS
```

#### Post 6 — Media Authenticity API (public repo) [DRAFT]
**Day:** Thu  
**Asset:** `media-auth-01-test-ui.png` or `media-auth-02-api-flow-diagram.png`

```
Teams exploring media authenticity need more than a model score — they need verifiable API responses.

I open-sourced Media Authenticity API:
→ Upload image → detector orchestration (Hugging Face)
→ HMAC-signed authenticity record returned
→ POST /api/verify lets clients confirm the result wasn't tampered with

Stack: Next.js API routes · TypeScript · Vitest

Repo: github.com/ChrisHorn-Dev/media-auth-api
Overview: github.com/ChrisHorn-Dev/case-studies/blob/main/media-auth-api.md

Honest scope: image path implemented; audio/video stubbed for future work.

#OpenSource #API #TypeScript
```

---

### Week 4

#### Post 7 — Cape Fear Web Co studio system [DRAFT]
**Day:** Mon  
**Asset:** `cape-fear-01-homepage-hero.png`

```
Small studios face a structural problem: the website is both marketing and a credibility filter.

For Cape Fear Web Co (capefearweb.co), I built one coherent system:
→ Marketing + SEO (JSON-LD, build-time sitemap, topic anchor pages)
→ Typed case summaries linking to long-form GitHub writeups
→ Supabase client portal at /portal (messages, requests, files, activity)

Same Vite SPA. Different modes. Portal scoped as delivery companion — not a billing replacement.

Case study: github.com/ChrisHorn-Dev/case-studies/blob/main/cape-fear-web-co.md

#WebDevelopment #Supabase #SaaS
```

#### Post 8 — Regen Profits sales PWA [DRAFT]
**Day:** Thu  
**Asset:** `regen-profits-01-mobile-rep-dashboard.png`  
**Gate:** Client approval required before posting

```
[DRAFT — confirm client approval + anonymization]

Shipped a mobile-first sales PWA for distributed reps:
→ Daily sales logging from phone
→ Leaderboards and funnel views
→ Admin command center for oversight
→ Installable PWA — no app store release cycle

Stack: Next.js 16 · Supabase (auth + RLS) · Tailwind v4 · Vercel

Staging: regen-profits-sales-app.vercel.app

[METRIC: rep count] · [METRIC: client review status]

#PWA #Supabase #NextJS
```

---

### Optional Bonus Posts (Month 2 backlog)

#### Remember Me MVP [DRAFT]
**Asset:** `remember-me-03-thinking-of-you.png`
```
Phase 1 MVP for relationship gifting — wishlists, reminders, events, and "Thinking of You" drafts.

Honest scope: no payments, no delivery in Phase 1. Demo mode runs full walkthroughs without Supabase.

[Deploy URL when live]
```

#### Pathbound game lab [DRAFT]
**Asset:** `pathbound-01-gameplay.gif`
```
Side project: pivoting a dark-fantasy top-down prototype from React Native to Godot 4.

Haven Clearing vertical slice — walk, touch controls, intro quest loop.

Personal lab, not day-job positioning — but it keeps engineering fun.
```

---

## Metric Placeholder Registry

Do not publish until filled with real, approved data.

| Placeholder | Project | Source |
|-------------|---------|--------|
| `[METRIC: practices in beta]` | Physician Connection | Client/product owner |
| `[METRIC: scheduling requests processed]` | Physician Connection | Analytics |
| `[METRIC: personas/dashboards shipped]` | SiteOS | Internal audit |
| `[METRIC: demo projects seeded]` | SiteOS | Repo seed scripts |
| `[METRIC: request types supported]` | Elite Touch | Prisma schema / product doc |
| `[METRIC: notification channels]` | Elite Touch | Integration config |
| `[METRIC: active reps]` | Regen Profits | Client — requires approval |
| `[METRIC: staging review status]` | Regen Profits | Client comms |
| `[METRIC: API requests]` | Media Auth API | Deployment telemetry if exists |
| `[METRIC: beta signups]` | Remember Me | Post-deploy analytics |

---

## Pre-Publish Checklist

- [ ] Headline variant selected
- [ ] About draft reviewed (A, B, or C)
- [ ] Featured section links verified (live URLs return 200)
- [ ] Client approval for Regen Profits post and Featured link
- [ ] Screenshots sanitized (no PHI, PII, pricing, API keys)
- [ ] All `[METRIC]` and `[DRAFT]` placeholders resolved or removed
- [ ] Staging URL still valid before Regen Profits post

---

## Cross-References

- `BRAND_REVAMP_EXECUTION_PLAN.md` — per-project task status
- `BRAND_ASSET_REQUESTS.md` — screenshot filenames
- `RESUME_PROJECT_BULLET_BANK.md` — resume-formatted bullets
- `BRAND_PROJECT_REGISTRY.md` — repo visibility and paths

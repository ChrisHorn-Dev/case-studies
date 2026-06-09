# Resume Project Bullet Bank

**Owner:** Chris Horn  
**Last updated:** 2026-06-09  
**Format:** `Built X using Y to solve Z` — 3–6 bullets per major app  
**Status:** Draft — replace `[METRIC: …]` with real data before resume submission

**Usage:** Copy bullets into resume, ChrisOS, or LinkedIn. Tailor 2–3 bullets per role application. Do not use all bullets for every project.

---

## Physician Connection

**Stack:** Next.js 16 · React · TypeScript · Drizzle ORM · Better Auth · Cal.com · PostgreSQL (Neon) · Stripe · Sentry · Vercel · Railway  
**Proof:** Private repo · [Public case study](https://github.com/ChrisHorn-Dev/case-studies/blob/main/physician-connection.md)

1. Built a multi-tenant healthcare SaaS using Next.js 16, Drizzle ORM, and Better Auth to coordinate appointment workflows between pharmaceutical reps and physician practices with explicit role-based access boundaries.
2. Built role-partitioned application surfaces using Next.js App Router to give reps, practice admins, physicians, and super-admins distinct views of the same visit lifecycle without leaking cross-role data.
3. Built Cal.com-backed scheduling integration using self-hosted Railway deployment to handle teams, event types, and domain-specific booking behavior instead of reinventing a scheduling engine.
4. Built production hardening improvements using Neon transaction fixes, Sentry instrumentation, and auth boundary enforcement to move the platform from fragile demo usage toward beta-ready real-office launch.
5. Built hosting migration path using Vercel + Railway architecture to replace legacy Oracle deployment with documented, controlled rollout procedures.
6. Built operational super-admin tooling using in-app seeding, error-log surfaces, and API-driven cleanup to reduce dependence on direct database access for support workflows.

**Metrics (fill before use):** `[METRIC: physician practices in beta]` · `[METRIC: roles supported]` · `[METRIC: scheduling states in lifecycle]`

---

## SiteOS — Construction Intelligence Platform

**Stack:** FastAPI · Celery · Redis · PostgreSQL/Supabase · TimescaleDB · Next.js 14 · Expo · scikit-learn · YOLOv8 · Claude API · Vercel · Railway  
**Proof:** Private repo · [Draft case study](https://github.com/ChrisHorn-Dev/case-studies/blob/main/siteos.md)

1. Built a construction execution intelligence platform using FastAPI, Celery, and PostgreSQL/TimescaleDB to connect field activity and project signals to multi-persona executive and foreman dashboards.
2. Built background job infrastructure using Celery and Redis to run scraping, ingestion, and ML preprocessing workloads without blocking API request paths.
3. Built multi-persona Next.js dashboard surfaces using role-specific views for general contractors, foremen, and executives to replace fragmented spreadsheet-based operational reporting.
4. Built an Expo mobile field app using React Native to give foremen jobsite-accessible workflows tied to the same backend project and signal model as web dashboards.
5. Built ML/CV and LLM integration points using scikit-learn, YOLOv8, and Claude API to support document analysis, computer vision workflows, and operational prediction surfaces.
6. Built a county-level signal foundation microservice (`siteos-signal-engine`) using FastAPI and SQLAlchemy to normalize geographic signals and continuity scoring feeding the main platform.

**Metrics (fill before use):** `[METRIC: dashboard personas implemented]` · `[METRIC: backend services in docker-compose stack]` · `[METRIC: demo projects seeded]`

---

## Elite Touch Cleaning Companion App / Client Portal

**Stack:** Next.js 15 · React 19 · TypeScript · Prisma · Twilio · Resend · HubSpot CRM API · Playwright  
**Proof:** Private repo · [Public case study](https://github.com/ChrisHorn-Dev/case-studies/blob/main/elite-touch-cleaning.md)

1. Built a mobile-first client operations portal using Next.js 15 and Prisma to replace fragmented phone and email workflows with structured, auditable service requests for a commercial cleaning company.
2. Built typed client request flows using modal-based launcher UI and persisted threads to separate operational issues, supply requests, notes, and feedback into distinct, trackable channels.
3. Built a dedicated SOS emergency pipeline using distinct request type, priority level, and notification fan-out to prevent urgent incidents from competing with routine operational queue items.
4. Built centralized ops notification system using Twilio SMS and Resend email with per-recipient `NotificationEvent` audit logging to create a durable record of every delivery attempt.
5. Built mock integration mode using environment-gated `MOCK_INTEGRATIONS` to enable safe client demos and Playwright e2e testing without sending production SMS or email.
6. Built HubSpot CRM sync path using read/upsert API routes and `HubSpotSyncRecord` persistence to align portal client records with existing sales contact data.

**Metrics (fill before use):** `[METRIC: request types in schema]` · `[METRIC: admin queue states]` · `[METRIC: notification channels configured]`

---

## Elite Touch Proposal App

**Stack:** Next.js 16 · Prisma · `@react-pdf/renderer` · NextAuth v5 · Playwright  
**Proof:** Private repo · Section in Elite Touch case study

1. Built an internal proposal builder using Next.js 16 and Prisma to generate branded scope-of-work PDFs and reduce manual assembly time during Elite Touch sales and onboarding.
2. Built PDF rendering pipeline using `@react-pdf/renderer` to produce consistent, client-ready proposal documents from structured proposal data models.
3. Built authenticated proposal lifecycle flows using NextAuth v5 to gate internal sales and approval-oriented document generation.
4. Built Playwright end-to-end tests to verify critical proposal and PDF output paths before client-facing deployment on Neon/Vercel.

**Metrics (fill before use):** `[METRIC: proposal templates]` · `[METRIC: PDF generation time improvement]` — do not invent

---

## Regen Profits Sales App

**Stack:** Next.js 16 · TypeScript · Supabase (`@supabase/ssr`) · Tailwind CSS v4 · PWA · Vercel  
**Proof:** Private repo · Staging: `regen-profits-sales-app.vercel.app` · [Draft case study](https://github.com/ChrisHorn-Dev/case-studies/blob/main/regen-profits-sales-app.md)  
**Note:** Anonymize client name in public resume versions; confirm client approval.

1. Built a mobile-first sales performance PWA using Next.js 16 and Supabase to give distributed sales reps fast phone-based logging without an app store release cycle.
2. Built rep-facing dashboards using leaderboard, sales funnel, and competition surfaces to support daily accountability and performance visibility in the field.
3. Built admin command center using role-gated `/admin` routes and Supabase row-level security to separate rep self-service from managerial oversight in one application.
4. Built installable PWA experience using service worker and web manifest to deliver native-app-like mobile access from a single Next.js deployment on Vercel.
5. Built staging-first client review workflow using documented QA checklists and verification docs to support Phase 1.9 demo readiness before gamification features.

**Metrics (fill before use):** `[METRIC: active sales reps]` · `[METRIC: admin surfaces shipped]` · `[METRIC: client staging approval status]`

---

## Remember Me

**Stack:** Next.js 16 · TypeScript · Supabase SSR · Tailwind CSS v4 · localStorage demo mode  
**Proof:** Private repo · [Draft case study](https://github.com/ChrisHorn-Dev/case-studies/blob/main/remember-me.md)

1. Built a relationship gifting MVP using Next.js 16 and Supabase to centralize wishlists, reminders, events, and gift draft flows that previously scattered across notes apps and messages.
2. Built "Thinking of You" draft flow using honest Phase 1 scope boundaries to let users compose gift-card drafts without overpromising payments or delivery infrastructure not yet built.
3. Built first-class demo mode using `/demo` route, cookie flag, and localStorage store to run full stakeholder walkthroughs without Supabase configuration or backend dependency.
4. Built Figma-aligned design token system using `lib/design-tokens.ts` to keep UI consistent between marketing pages and authenticated dashboard surfaces.
5. Built explicit Phase 1 disclaimers in UI copy and README to document intentional exclusions (no payments, no automated imports, no notifications) and prevent stakeholder scope creep.

**Metrics (fill before use):** `[METRIC: Phase 1 features shipped]` · `[METRIC: deploy URL]` — add post-launch only

---

## ChrisOS / resume-os

**Stack:** Next.js 16 · TypeScript · Zustand · Framer Motion · Tailwind CSS v4  
**Proof:** Public repo · Live: [chrisos.dev](https://chrisos.dev) · [github.com/ChrisHorn-Dev/resume-os](https://github.com/ChrisHorn-Dev/resume-os)

1. Built an interactive desktop-style portfolio using Next.js 16 and Zustand to present projects, resume, and tech stack as first-class applications inside a browser-based window manager at chrisos.dev.
2. Built shared window state model using Zustand store and WindowContext to let desktop shell, mobile shell, dock, and terminal open and focus the same app abstraction with consistent behavior.
3. Built mobile portfolio shell using dedicated launcher and full-screen terminal overlay to deliver the same project deep dives without maintaining a separate content codebase.
4. Built structured content layer using `content/projects.ts` and `projectDeepDives.ts` to decouple architecture storytelling from presentation components across desktop and mobile surfaces.
5. Built terminal command interface using shared command definitions to expose portfolio navigation as a narrative device mapping to real `openApp` window management behavior.

**Metrics (fill before use):** `[METRIC: projects catalogued]` · `[METRIC: deep-dive sections complete]` — count from repo, not invented

---

## Media Authenticity API

**Stack:** Next.js API routes · TypeScript · Hugging Face Inference API · Vitest · HMAC-SHA256  
**Proof:** [Public repo](https://github.com/ChrisHorn-Dev/media-auth-api) · [Case study overview](https://github.com/ChrisHorn-Dev/case-studies/blob/main/media-auth-api.md)

1. Built a public image authenticity API using Next.js API routes and Hugging Face detectors to analyze uploaded media and return structured likely-synthetic vs likely-authentic verdicts.
2. Built HMAC-SHA256 signing layer using canonical payload construction to produce tamper-evident authenticity records verifiable by downstream systems without trusting client-side results.
3. Built independent verification endpoint using `POST /api/verify` and constant-time signature comparison to let clients confirm analysis results originated from this service unmodified.
4. Built detector orchestration layer using explicit registry pattern to support single-detector and ensemble modes without coupling HTTP routes to specific model implementations.
5. Built file-hash TTL cache using in-memory or file-backed storage to avoid re-analyzing identical uploads while keeping cache behavior simple to reason about and test.
6. Built Vitest test suite covering analyze and verify paths plus built-in localhost test UI to support manual integration testing without external client setup.

**Metrics (fill before use):** `[METRIC: detectors in registry]` · `[METRIC: API endpoints shipped]` · `[METRIC: test coverage scope]`

---

## Cape Fear Web Co

**Stack:** Vite · React 18 · TypeScript · Tailwind CSS · TanStack Query · Supabase · Vercel Functions · Resend  
**Proof:** Live: [capefearweb.co](https://capefearweb.co) · [Public case study](https://github.com/ChrisHorn-Dev/case-studies/blob/main/cape-fear-web-co.md)

1. Built a studio marketing site using Vite and React to position custom operational software services with topic anchor pages, markdown blog, and typed on-site case summaries at capefearweb.co.
2. Built SEO infrastructure using build-time sitemap generation, canonical URLs, and JSON-LD builders (`SoftwareCompany`, `BlogPosting`, `Article`) to compound crawlable depth without a CMS.
3. Built proof layer using TypeScript `cases.ts` records linking to long-form public GitHub case studies to give technical buyers credible architecture receipts without duplicating content in CMS pages.
4. Built unified SPA architecture using React Router to serve public marketing routes and authenticated portal routes from one deploy with shared design language and reduced operational overhead.

**Metrics (fill before use):** `[METRIC: case studies indexed on site]` · `[METRIC: blog posts published]`

---

## Cape Fear Client Portal

**Stack:** Supabase Auth · PostgreSQL RLS · Supabase Storage · Vercel serverless API · Resend  
**Proof:** Subproject of Cape-Fear-Web-Co-Web · Covered in Cape Fear case study

1. Built a client delivery portal using Supabase Auth and Postgres RLS to move routine project communication out of email threads into structured, permission-scoped project records.
2. Built threaded messaging and typed client request workflows using Supabase direct client queries to give studio clients visibility into request status without building a full project management SaaS.
3. Built private file storage using Supabase Storage bucket with `{organization_id}/{project_id}/` path convention and RLS policies to keep client uploads scoped to authorized project members.
4. Built activity feed using database triggers on messages, requests, and files to give clients a chronological project timeline without manual status update emails.
5. Built Vercel serverless notify API using JWT-verified Bearer tokens and optional Resend email to alert studio staff of portal activity without exposing Supabase service role to the browser.

**Metrics (fill before use):** `[METRIC: portal route surfaces]` · `[METRIC: RLS policy count]` — from migrations, not invented

---

## Genesis Mastery

**Stack:** Next.js 16 · Prisma 7 · NextAuth v5 · PostgreSQL · shadcn/ui · Recharts · react-markdown  
**Proof:** Private repo · Optional ChrisOS card

1. Built an EdTech curriculum platform scaffold using Next.js 16 and Prisma 7 to structure Master's-level Genesis modules with lessons, quizzes, and progress tracking.
2. Built instructor admin CMS patterns using NextAuth v5 credentials provider and role-modeled routes to support course seeding, content management, and formative assessment workflows.
3. Built auto-graded quiz and progress record system using Prisma relations and server actions to track student performance without manual instructor scoring for formative checks.
4. Built lesson rendering pipeline using react-markdown and remark-gfm to deliver scholarly content with citation support inside authenticated course views.

**Metrics (fill before use):** `[METRIC: seeded modules]` · `[METRIC: quiz types]` — from seed data only

---

## Wilmington Engine

**Stack:** Next.js monorepo · Neon · TypeScript · pipeline workers  
**Proof:** Private repo · Pre-build audit docs

1. Built a pre-build architecture audit package using structured planning documents to evaluate viability of a Wilmington-first local media automation platform before committing to full implementation.
2. Built monorepo scaffold using Next.js and Neon to support policy-driven content pipeline workers and web admin surfaces for human-in-the-loop publishing workflows.
3. Built honest scope framing using master audit verdict to separate viable media-company-first strategy from over-scoped "autonomous 50-city platform" marketing narrative.

**Metrics:** Omit from client-facing resume unless Phase 1 ships — no invented traction metrics.

---

## Visual Conversations

**Stack:** TypeScript · Chrome Extension Manifest V3 · OpenAI API · Node CLI (`tsx`) · esbuild  
**Proof:** Private repo · Experimental

1. Built a UI intent assistant CLI using TypeScript and OpenAI API to explore design-intent workflows from terminal sessions with pluggable brain layer and offline mock mode.
2. Built Chrome Extension MV3 using content script DOM digest capture and popup-driven intent flow to connect live page context with LLM-backed session summaries.
3. Built session store and intent model using lightweight `src/session/` modules to persist conversation context across CLI and extension surfaces during development experiments.

**Metrics:** Omit unless promoted — experimental dev tool.

---

## Pathbound Mobile

**Stack:** Godot 4.6+ · GDScript · map composer tooling · Cainos pixel art  
**Proof:** Private repo · Created 2026-06-08

1. Built a Godot 4 top-down game prototype using GDScript and Cainos pixel art to deliver a playable Haven Clearing vertical slice with walk, touch controls, and intro quest loop.
2. Built map composer tooling using JSON room templates and dungeon grammar examples to support procedural map iteration without hand-editing every tile placement.
3. Built documented engine pivot using archived Expo/React Native prototype and direction-reset docs to preserve exploration history while committing to Godot for 2D MMO-lite goals.

**Metrics:** Omit from professional resume unless applying to game roles — optional personality signal.

---

## case-studies (Public Proof Channel)

**Stack:** Markdown · GitHub  
**Proof:** [github.com/ChrisHorn-Dev/case-studies](https://github.com/ChrisHorn-Dev/case-studies)

1. Built a public case studies repository using architecture-focused markdown writeups to demonstrate private SaaS work without exposing proprietary client code or production data.
2. Built consistent case study structure using problem context, system overview, stack tables, engineering decisions, and honest shipped-vs-scaffolded scope across healthcare, ops, and platform projects.

---

## ChrisHorn-Dev Profile README

**Stack:** GitHub profile markdown  
**Proof:** [github.com/ChrisHorn-Dev/ChrisHorn-Dev](https://github.com/ChrisHorn-Dev/ChrisHorn-Dev)

1. Built a GitHub profile README using featured work sections and stack summary to route visitors to ChrisOS, public case studies, and open-source Media Authenticity API from a single landing page.

---

## Resume Assembly Guide

### Flagship projects (pick 3–4 for most applications)

| Priority | Project | Best for |
|----------|---------|----------|
| 1 | Physician Connection | Healthcare SaaS, multi-tenant, production hardening roles |
| 2 | SiteOS | Platform/full-stack, Python + Next.js, data pipeline roles |
| 3 | Elite Touch Client Portal | Operational systems, integrations, client-facing product roles |
| 4 | Cape Fear Web Co + Portal | Agency/studio, full-stack delivery, Supabase roles |
| 5 | Media Authenticity API | API/platform, open-source signal, ML-adjacent roles |
| 6 | ChrisOS | Frontend craft, portfolio, product-minded engineering culture |

### Supporting projects (pick 0–2)

- Regen Profits Sales App (PWA, Supabase, client delivery)
- Remember Me (consumer MVP, demo mode, product scope discipline)
- Elite Touch Proposal App (PDF generation, internal tooling)

### Omit unless relevant

- Genesis Mastery (EdTech scaffold)
- Wilmington Engine (pre-build R&D)
- Visual Conversations (experimental)
- Pathbound Mobile (game lab)
- Legacy private cards (Thank You For Dying, Regal Rides, Ronald Wayne)
- style-sculptors-inc (archived)
- rsps-lab (personal lab)
- cal-web-railway-deploy, pc-next (duplicates — never list separately)

### Bullet selection formula per application

1. **Lead bullet** — strongest project match for job description (Built X using Y to solve Z)
2. **Architecture bullet** — stack breadth (DB, auth, integrations, workers)
3. **Production bullet** — hardening, testing, deployment, observability
4. **Product bullet** — role-based UX, scope honesty, client/stakeholder outcomes
5. **Metric bullet** — only if `[METRIC]` filled with real approved data

---

## Cross-References

- `BRAND_REVAMP_EXECUTION_PLAN.md` — task and screenshot status per project
- `BRAND_ASSET_REQUESTS.md` — visual asset filenames
- `LINKEDIN_UPDATE_PACKET.md` — social-formatted bullets and 30-day posts
- `BRAND_PROJECT_REGISTRY.md` — canonical paths, repo visibility, stack

# Cape Fear Web Co — acquisition and delivery system

## Context

A small studio selling custom operational software faces a structural problem: the **website is both marketing and a credibility filter**. Typical agency sites optimize for volume—broad claims, thin proof, contact forms that dump everyone into the same inbox. That produces noisy inbound, misaligned expectations, and a gap between what the homepage promises and how delivery actually runs.

Parallel issues:

- **Lead quality**: Without explicit positioning and proof, you attract buyers who want a page or a funnel, not a system.
- **Marketing vs delivery**: Sales narrative and how work is executed drift apart when there is no shared artifact (structured content, portal, written principles).
- **No compounding**: One-off pages do not build crawlable depth; there is no durable internal linking or long-form cluster around the problems you solve.
- **Fragmented communication**: Email-only delivery scales poorly; context lives in threads instead of next to the project record.

This project is the response: **one coherent system**—public surface (positioning, SEO, case summaries), proof (GitHub writeups, anonymized shipped work), and a **client portal** scoped as a delivery companion—not a replacement for contracts or payments.

## Goals

- Pull **higher-signal inbound** by stating problems, tradeoffs, and engagement shape honestly.
- Reflect **systems-level positioning** (internal tools, workflow systems, integrations) in copy, routes, and structured data—not only in hero text.
- **Compound** through topic anchors, a markdown blog, and cross-links between cases and notes.
- **Reduce coordination overhead** by moving routine client communication into a structured portal (messages, requests, files, activity).
- **Unify acquisition → delivery** so the same mental model (explicit state, permissions, operational software) appears on the marketing site and in how clients interact during an engagement.

## System Overview

The implementation reads as four layers that share configuration and types—not four disconnected products.

1. **Marketing layer** — React SPA (Vite): homepage, topic pages (`/internal-tools`, `/workflow-systems`, `/custom-software`), case study index and detail, blog index and posts, legal/privacy. Navigation and modals (e.g. project brief, contact) live in the same app shell.
2. **Proof layer** — On-site case summaries are backed by **`src/content/cases.ts`** (typed records: challenge, architecture bullets, engagement shape, link to long-form notes). Deep technical writeups intentionally live in a **public GitHub markdown repo** linked from each case—not duplicated as CMS pages.
3. **Delivery layer** — **`/portal/*`**: Supabase-backed auth (magic link), per-organization projects, threaded messages, typed client requests, private file storage, and an activity feed derived from database triggers.
4. **Internal structure** — `siteConfig` centralizes brand facts; **`Seo`** wraps `react-helmet-async` for title, description, canonical, Open Graph/Twitter, and JSON-LD; **`scripts/generate-sitemap.mjs`** emits `public/sitemap.xml` and updates `robots.txt` on build from static routes, case slugs, and blog frontmatter.

The point is intentional: **positioning, crawlable content, and delivery mechanics share one repository and one deploy**, with clear boundaries (public routes vs authenticated portal, marketing copy vs portal RLS).

## Architecture

| Area | Implementation |
|------|----------------|
| **Frontend** | React 18, TypeScript, Vite, React Router 6, Tailwind, shadcn-style UI primitives, TanStack Query for portal data fetching. |
| **Content — cases** | `src/content/cases.ts`: structured `CaseStudy` objects rendered by `/case-studies` and `/case-studies/:slug`. |
| **Content — blog** | Markdown under `content/blog/*.md`, loaded at build time via `import.meta.glob` + `gray-matter` in `src/content/loadBlog.ts`. |
| **SEO** | `Seo` component: canonical URLs from `VITE_SITE_URL` (with documented fallback origin), OG/Twitter tags, optional `noindex` for portal login. JSON-LD builders in `src/lib/schema.ts` (e.g. `SoftwareCompany`, `BlogPosting`, `Article` for cases, `BreadcrumbList`). |
| **Sitemap** | `prebuild` runs `generate-sitemap.mjs`: static routes, case slugs (kept in sync with `cases.ts`), blog paths from frontmatter `slug` / `date` / `updated`. |
| **Supabase** | Auth (email OTP), Postgres schema for orgs, members (`client` \| `studio`), projects, threads/messages, `client_requests`, `project_files`, `activity_events`. Private bucket `portal-files` with path convention `{organization_id}/{project_id}/…`. RLS and triggers in `supabase/migrations/001_portal_companion.sql`. |
| **Portal routes** | `PortalApp`: `/portal/login`, authenticated layout with dashboard, settings, and `projects/:projectId` with nested `overview`, `messages`, `requests`, `files`. |
| **API** | Vercel serverless `api/notify.ts`: validates Bearer JWT via Supabase service role, checks `organization_members`, optionally sends email through Resend when env vars are set; otherwise logs and returns 200. |

**Connection graph**: The browser talks to Supabase directly for portal CRUD (anon key + RLS). Client-side `dispatchStudioNotification` POSTs to **`/api/notify`** with the user’s access token so the server can verify identity without exposing the service role. Email is optional glue; the database remains the source of truth for messages, requests, and files.

## Key Design Decisions

- **Marketing vs portal in one SPA, different modes** — Same deploy and design language; portal routes are behind auth and can be `noindex`. Keeps operational overhead low versus splitting into two apps prematurely.
- **Portal as companion, not full SaaS** — Documented explicitly in the repo README: contracts, invoices, and payments stay on **Contra**; the portal handles delivery communication. That avoids rebuilding billing and keeps scope honest.
- **GitHub for long-form proof** — Case pages on the site are summaries and structured fields; technical depth links out to markdown in `ChrisHorn-Dev/case-studies`. Version-controlled, diffable, and credible to engineers without maintaining a CMS.
- **Minimal portal UI** — Dashboard-style density is deliberately avoided in favor of short status lines, phase labels, and small activity lists. The goal is legibility for busy clients, not feature parity with Jira.
- **No fabricated metrics** — `cases.ts` comments and copy emphasize anonymized context and “implementation receipt” language instead of vanity numbers. Aligns marketing with how technical buyers evaluate risk.

## Portal System (Delivery Layer)

**What exists (as implemented):**

- **Messaging** — Threads per project; messages carry a category enum (`question`, `update`, `issue`). Authors are Supabase `auth.users`.
- **Requests / tickets** — `client_requests` with type (`bug`, `change`, `question`, `asset_needed`), status workflow (`submitted` → `reviewing` → `in_progress` → `resolved`), optional priority (`normal` / `urgent`).
- **Files** — Uploads to private storage; metadata in `project_files` with optional link to a request.
- **Activity** — `activity_events` table with enum types such as `message_created`, `request_created`, `request_status_changed`, `file_uploaded`; triggers log events; the project overview queries the latest rows for a lightweight timeline.
- **Notifications** — `dispatchStudioNotification` sends a typed payload (`message` | `request` | `file`) to `/api/notify` in production (or logs in dev unless `VITE_NOTIFY_IN_DEV=true`). Server verifies membership, then Resend email if configured. No SMS in this path today—the abstraction is documented as swappable.

**What is intentionally simple:**

- Role model is **`client` vs `studio`** at the organization level—not granular per-project RBAC in the UI.
- No in-app billing, SLAs, or automation builders—by design.
- Email to the studio is optional; if Resend env vars are missing, the handler still succeeds and logs—operators should know that means **no outbound alert**.

## SEO + Content System

- **Anchor pages** — `/internal-tools`, `/workflow-systems`, and `/custom-software` give crawlers and humans stable entry points aligned with service language. They appear in the generated sitemap with explicit priorities.
- **Blog cluster** — Posts live as markdown with frontmatter (`slug`, `title`, `description`, `date`, optional `category`, `relatedCaseSlugs`). `loadBlog.ts` sorts by date; related posts prefer same category.
- **Internal linking** — `caseRelatedBlog.ts` maps case slugs to related blog slugs; case detail pages resolve and render those links. Blog frontmatter can declare `relatedCaseSlugs` for the reverse direction—data-driven cross-linking without a CMS graph UI.
- **Structured data** — Organization JSON-LD (`SoftwareCompany`) with conservative `knowsAbout` / `serviceType` lists; blog posts emit `BlogPosting`; case pages emit `Article` plus `BreadcrumbList`.
- **Sitemap** — Build-time generation keeps `lastmod` for posts when dates are valid ISO prefixes—reduces drift between routes and XML.

**Why this supports long-term inbound:** Search engines get clear topical hubs, article metadata, and internal links between problems (blog) and proof (cases). The studio does not depend on a single landing page for all queries.

## Tradeoffs

- **No CMS** — All public content changes go through git. Editors who do not work in the repo cannot ship copy alone; conversely, there is no WordPress attack surface or sync drift.
- **Portal minimalism** — Clients get structure, not a productized “agency OS.” Some buyers expect Kanban-heavy UX; this implementation optimizes for clarity and low maintenance.
- **No billing/contracts in-app** — Commercial workflow stays on Contra (or elsewhere). The portal will never show invoice state unless someone builds it—explicit non-goal.
- **Slower non-engineer content iteration** — New posts require markdown + build; case studies require TypeScript list updates **and** sitemap slug list alignment (`generate-sitemap.mjs` duplicates case slugs by design comment).
- **No SSR** — Vite SPA + Helmet means crawlers that execute JavaScript see meta tags; edge cases (some social scrapers, strict latency budgets) may still favor pre-rendered HTML. The README documents `VITE_SITE_URL` for canonicals; local dev falls back to a documented production origin for SEO helpers.

Stating these plainly matters: the system is optimized for **truthful positioning and sustainable operations**, not for pretending to be a mature SaaS platform.

## Outcome

No conversion percentages or revenue claims—those are not verified in code.

What the system **does** achieve, by construction:

- **Alignment** between homepage principles (`siteConfig` trust band), topic routes, JSON-LD keywords, and portal data model (explicit request state, activity log).
- **A single pipeline** from “read how we work” to “open the portal and continue the conversation” without re-platforming the client.
- **Unified communication** for delivery: fewer “which thread was that?” loops when messages and requests are project-scoped and time-ordered.
- **Operational clarity** for the studio: one notification hook, one Supabase project, one Vercel app—bounded moving parts.

## What I’d Improve Next

- **SSR or prerender** for critical marketing URLs if analytics or crawler behavior justifies it—likely incremental static generation or a small subset of routes, not a full framework migration without cause.
- **Notification depth** — Extend `dispatchStudioNotification` / `api/notify` to additional channels (SMS, webhook) once volume warrants it; the types already allow `meta` hints.
- **More case studies and clusters** — Each addition strengthens internal linking; GitHub writeups stay the long-form channel.
- **Portal enhancements** — Optional studio-facing admin UI (today much is SQL/bootstrap), richer request assignment, or read receipts—only where clients ask and complexity stays bounded.

## Links

- **Live site:** [capefearweb.co](https://capefearweb.co)
- **Related case studies (this repo):** [Physician Connection](./physician-connection.md) · [Elite Touch Cleaning — client & ops portal](./elite-touch-cleaning.md)

The marketing application and client portal ship from a private Vite/React repository; **this file is the public technical overview** of the system as implemented.

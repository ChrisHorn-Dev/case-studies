# Product Case Studies

This repository contains selected case studies of SaaS platforms, product systems, and web applications I’ve contributed to.

Some projects are private and owned by employers or clients, so source code cannot be shared publicly. These write-ups focus on architecture, technical responsibilities, and product outcomes rather than proprietary implementation details.

## Case Studies

### Physician Connection Platform

Production SaaS platform for rep–practice appointment coordination, calendars, and operational workflows.

**Stack**

Next.js · React · TypeScript · Drizzle ORM · Better Auth · Cal.com · PostgreSQL (Neon) · Vercel · Railway

**Highlights**

- Multi-role surfaces for representatives, practice staff, physicians, and super-admins
- Guided rep request flows and practice-side lifecycle visibility on calendars and dashboards
- Cal.com integration with self-hosted scheduling stack; auth and protected routes across roles
- Hosting migration and hardening toward MVP-ready, real-office launch

→ **[Read the full case study](./physician-connection.md)**

---

### Elite Touch Cleaning — Client & Operations Portal

Mobile-first **client portal** and **operations MVP** for a commercial cleaning services company: structured requests (issues, notes, supplies, feedback), **SOS** broadcasting, **Twilio/Resend** ops alerts with mock mode, **Prisma** persistence, and **admin-driven HubSpot** contact sync.

**Stack**

Next.js · React · TypeScript · Prisma · Twilio · Resend · HubSpot CRM API

**Highlights**

- Client launcher with modal task flows; separate SOS pipeline with emergency priority and broadcast notifications
- Admin request queue (open / urgent / closed), detail threads, attachments, status and priority controls
- Manual SMS check-in sender; HubSpot upsert sync; integration mocks for safe demos

→ **[Read the full case study](./elite-touch-cleaning.md)**

---

### Cape Fear Web Co — Acquisition & delivery system

End-to-end **studio website** plus **client delivery portal**: marketing, SEO (JSON-LD, sitemap generation), markdown blog, typed on-site case summaries linking here for long-form notes, and a **Supabase**-backed `/portal` for messages, structured requests, private file uploads, activity history, and optional **Resend** alerts via a **Vercel** serverless API.

**Stack**

React · TypeScript · Vite · React Router · Tailwind · TanStack Query · Supabase (Auth, Postgres, Storage, RLS) · Vercel Functions

**Highlights**

- One SPA: public routes and authenticated portal; clear separation without two deploy pipelines
- Build-time sitemap + structured data (`SoftwareCompany`, `BlogPosting`, `Article`, breadcrumbs)
- Content model: TypeScript case records + blog markdown with cross-links to shipped-work narratives
- Delivery layer: threaded messages, typed client requests with status workflow, storage-backed files, DB-driven activity timeline, JWT-verified notify endpoint

→ **[Read the full case study](./cape-fear-web-co.md)**

---

Additional case studies will be added over time as I’m able to share more work publicly.

# Product Case Studies

Architecture write-ups for software I've built and shipped. Source code for many projects is private, so these focus on what the system does, how it's built, what was hard, and what tradeoffs were made — not proprietary implementation details.

**Portfolio:** [chrisos.dev](https://chrisos.dev) · **GitHub:** [@ChrisHorn-Dev](https://github.com/ChrisHorn-Dev)

---

## Flagship

### [Elite Touch Cleaning — Proposals & Operations Portal](./elite-touch-cleaning.md)

Proposal/PDF workflow plus live client/ops portal (typed requests, SOS, triage, SMS/email) and HubSpot audit-first discovery.

**Stack:** Next.js · TypeScript · Prisma · Twilio · Resend · HubSpot · React PDF

---

### [Regen Profits — Sales Ops, Territory & Portal](./regen-profits.md)

Field sales PWA, CRM-backed territory map (national ZCTA geometry), and owned website/portal stack handed to client infrastructure.

**Stack:** Next.js · Supabase · GoHighLevel · Clerk · Neon · Vercel

---

### [Physician Connection Platform](./physician-connection.md)

Multi-role healthcare SaaS for rep–practice appointment coordination — production hardening for Cal.com conversion, reconcile, and concurrency (not a founding-engineer claim).

**Stack:** Next.js · TypeScript · Drizzle ORM · Better Auth · Cal.com · PostgreSQL (Neon) · Vercel · Railway

---

### [SiteOS — Construction Intelligence Platform](./siteos.md)

Construction portfolio and project intelligence — ingestion pipelines, executive dashboards, document intelligence. Private repo; public architecture write-up. Expo field app is **not** claimed as shipped.

**Stack:** FastAPI · Celery · PostgreSQL · TimescaleDB · Next.js · Redis

---

## Additional

### [Cape Fear Web Co — Studio site & client portal](./cape-fear-web-co.md)

Marketing site plus Supabase-backed client delivery portal for a custom software studio.

**Stack:** React · TypeScript · Vite · Tailwind · Supabase · Vercel

Live site: [capefearweb.co](https://capefearweb.co)

---

### [Media Authenticity API](./media-auth-api.md)

Signed image analysis with a verification endpoint — explore tamper-evident authenticity results instead of opaque model scores.

**Stack:** Next.js API · TypeScript · Hugging Face · Vitest

Repo: [media-auth-api](https://github.com/ChrisHorn-Dev/media-auth-api)

---

## Private work (portfolio only)

These appear in [chrisos.dev](https://chrisos.dev) but do not have finished long-form public case studies yet:

- **Remember Me** — consumer MVP for reminders and wishlists (private repo)

Regen Profits now has a short public write-up: [regen-profits.md](./regen-profits.md).

---

## About these write-ups

I publish case studies when code cannot be public — the same material I'd use in a design review: problem context, system boundaries, infrastructure decisions, and lessons learned. No invented metrics; no client secrets.

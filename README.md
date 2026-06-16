# Product Case Studies

Architecture write-ups for software I've built and shipped. Source code for many projects is private, so these focus on what the system does, how it's built, what was hard, and what tradeoffs were made — not proprietary implementation details.

**Portfolio:** [chrisos.dev](https://chrisos.dev) · **GitHub:** [@ChrisHorn-Dev](https://github.com/ChrisHorn-Dev)

---

## Flagship

### [Physician Connection Platform](./physician-connection.md)

Multi-role healthcare SaaS for rep–practice appointment coordination — guided booking, role-based dashboards, Cal.com integration, and production migration off Oracle-hosted infrastructure.

**Stack:** Next.js · TypeScript · Drizzle ORM · Better Auth · Cal.com · PostgreSQL (Neon) · Vercel · Railway

---

### [SiteOS — Construction Intelligence Platform](./siteos.md)

Construction portfolio and project intelligence — field workflows, ingestion pipelines, executive dashboards, document intelligence, and mobile capture. Private repo; public architecture write-up.

**Stack:** FastAPI · Celery · PostgreSQL · TimescaleDB · Next.js · Expo · Redis

---

### [Elite Touch Cleaning — Client & Operations Portal](./elite-touch-cleaning.md)

Client ops portal for typed service requests, SOS path, admin triage, notifications, and CRM sync. Proposal/PDF generator in the same client ecosystem.

**Stack:** Next.js · TypeScript · Prisma · Twilio · Resend · HubSpot

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

These appear in [chrisos.dev](https://chrisos.dev) but do not have finished public case studies yet:

- **Regen Profits Sales App** — mobile sales PWA (private repo, client work)
- **Remember Me** — consumer MVP for reminders and wishlists (private repo)

---

## About these write-ups

I publish case studies when code cannot be public — the same material I'd use in a design review: problem context, system boundaries, infrastructure decisions, and lessons learned. No invented metrics; no client secrets.

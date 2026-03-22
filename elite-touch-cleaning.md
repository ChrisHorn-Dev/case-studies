# Elite Touch Cleaning — Client & Operations Portal (MVP)

## 1. Overview

This is not a contact form. It is a **service operations system** for **Elite Touch Cleaning Services**: a **mobile-first client portal** paired with an **internal operations layer** where facility contacts create **typed work** (issues, notes, supply requests), submit **feedback** on a separate track, and use a dedicated **SOS** path for emergencies.

Submissions persist as **structured data** (Prisma schema targets relational Postgres; **SQLite** in the default checkout). Operations are notified via **SMS** and **email** using environment-configured recipient lists, with each delivery attempt recorded as a **`NotificationEvent`**.

The code lives in a **private** repository (`elite-touch-client-portal`). This write-up reflects the **implementation** and a **client MVP status document**, excluding credentials, tenant data, and internal business processes.

---

## 2. Problem Context

Without a system, client communication fragments across **phone calls, inbox threads, and ad hoc messages**. Nothing becomes a **durable record** by default. **Feedback** mixes with **operational issues**, **urgency** is ambiguous, and follow-up depends on **individual memory** rather than system behavior.

This fails in predictable ways:

- **No system of record** — issues are not consistently tracked or auditable.
- **Lost or delayed feedback** — smaller problems go unreported or surface too late.
- **Mixed signal** — feedback, requests, and emergencies share the same channels.
- **Reactive operations** — follow-up depends on who saw what, not a defined lifecycle.

The MVP replaces that with:

- **Structured requests** with persisted threads.
- A **separate feedback channel** outside the operational queue.
- A **distinct SOS path** with its own type, priority, and notification handling.

The goal is not feature expansion. It is replacing **invisible, inconsistent workflows** with something **explicit and reliable**.

---

## 3. System Overview

**Stack:** Next.js App Router, React 19, TypeScript, Tailwind, Prisma.

The default datasource is **SQLite** for local development. **Production is intended to use PostgreSQL** via `DATABASE_URL` and switching the Prisma datasource provider in `schema.prisma`, as documented in **`.env.example`** and schema comments—**not** an automated migration pipeline shipped in this repository.

**Implemented end-to-end**

- Route handlers under `app/api/*` for auth, contact requests, SOS, feedback, check-ins, and HubSpot sync.
- **Cookie-based sessions:**
  - Client session via known email → **httpOnly** cookie with client id.
  - Admin session via shared **`ADMIN_PASSWORD`**.
- **Client UI:** Launcher + modal-based actions (`components/client/*`); gated `/client/*` routes.
- **Admin UI:** Request queue (open / urgent / closed); request detail (thread, attachments, notifications); feedback list and check-in panel.
- **Notifications:** Centralized fan-out (`notify-ops.ts`) to Twilio (SMS) and Resend (email), gated by **`MOCK_INTEGRATIONS`**; per-recipient **`NotificationEvent`** persistence.
- **HubSpot:** Read + upsert via `POST /api/hubspot/sync`; **`Client`** + **`HubSpotSyncRecord`** persistence.

**Scaffolded or not wired**

- **`OpsUser`** model exists but is **not** used for authentication or RBAC.

**Stubbed / placeholder**

- Twilio webhook (`/api/webhooks/twilio`): logs payload only; returns empty TwiML.
- HubSpot webhook: logs request only.
- **`firstResponseAt`** exists but is **not** written by application code.
- Check-in **“responded”** state is defined in the enum but **not** updated by the webhook.

---

## 4. Core Workflows

### A. Standard requests (issue, note, supplies)

**Input:** Client submits **multipart** to `/api/contact-requests` (session required). **Zod** validation enforces `type`, `subject`, and `message`.

**System behavior:**

- Creates **`ContactRequest`** (`open`, `normal` priority).
- Creates initial **`ContactMessage`** (`senderType: client`).
- Optional image attachment stored via `lib/uploads.ts` → `public/uploads`; **`Attachment`** linked to request and message.

**Downstream:**

- **`notifyOpsNewRequest`** sends SMS + email to configured recipients.
- Each attempt recorded as a **`NotificationEvent`**.

**UI mapping:**

- Report issue → `service_issue`
- Note → `general` with fixed subject
- Supplies → `update` with derived subject

### B. SOS (emergency path)

**Input:** `POST /api/sos` with `{ message, confirmed: true }`.

**System behavior:**

- Creates **`ContactRequest`** (`type: emergency`, `priority: emergency`).
- Creates initial message.
- Triggers **`notifyOpsEmergency`** with distinct notification copy.

This path bypasses normal request handling semantics—**urgency is encoded in both data and notification behavior**.

### C. Feedback (separate track)

**Input:** `POST /api/feedback` with rating (1–5) and optional comment.

**System behavior:**

- Inserts **`Feedback`** row.
- Rating **5** → `routedToPublicReview: true`.

**UX distinction:**

- `/client/feedback` can show a **Google review** link when `NEXT_PUBLIC_GOOGLE_REVIEW_URL` is configured.
- Modal-based feedback submission **does not** include that CTA.

Feedback is **intentionally not** part of the request lifecycle.

### D. Admin triage

**Input:** `PATCH /api/contact-requests/[id]` with optional `status`, `priority`, `opsNote`.

**System behavior:**

- Updates request state.
- Sets **`closedAt`** when closed.
- Appends ops note as **`ContactMessage`** (`senderType: ops`).

**Surface:**

- Filtered queues (open / urgent / closed).
- Detail view: message thread, attachments, notification history.

**`firstResponseAt` is not populated** by this flow.

### E. HubSpot sync

**Input:** `POST /api/hubspot/sync` with `hubspotContactId` or `email`.

**System behavior:**

- If token missing (or mock mode) → **422** response from the route with a clear error body.
- Otherwise: fetch or search contact, **upsert** `Client`, persist **`HubSpotSyncRecord`** with raw payload.

**No** background processing or automation layer.

### F. Check-in SMS

**Input:** `POST /api/checkins/send` with `clientId`.

**System behavior:**

- Creates **`CheckInEvent`** (`queued` → `sent` / `failed`).
- Requires **`Client.phone`**.
- Sends fixed SMS template.
- Logs **`NotificationEvent`**.

**No** cron, scheduling, or inbound parsing.

---

## 5. Architecture & Technical Design

**Routing / gating:** `middleware.ts` enforces access control for `/client/*` and `/admin/*`.

**Sessions:** Cookie-based (`getClientIdFromCookies`, `getAdminFromCookies`); route handlers **re-check** permissions before mutations.

**Validation:** Shared **Zod** schemas (`lib/schemas/api.ts`).

**Notifications:** Central module (`notify-ops.ts`) manages fan-out + persistence; provider wrappers isolate **Twilio** and **Resend**.

**Data model:** Prisma models encode request type / status / priority, message sender type, notification channel / status, check-in lifecycle. **`Client`** is the identity anchor.

---

## 6. Key Engineering Contributions

- **Implemented the request lifecycle:** typed `ContactRequest` + threaded `ContactMessage` model; attachment linkage for issue reporting; admin mutation flows with state transitions.
- **Established a distinct emergency path:** dedicated `/api/sos` route; emergency-specific enums and **`notifyOpsEmergency`** logic.
- **Built the notification pipeline:** configurable recipient lists; per-recipient logging (`NotificationEvent`); **mock mode** for provider isolation.
- **Developed the client-side action model:** launcher + modal flows; query-param entry (`?open=`).
- **Delivered admin triage surfaces:** filtered queues; thread + attachment visibility; notification audit context.
- **Integrated HubSpot read + sync path:** admin-triggered upsert; audit record persistence (`HubSpotSyncRecord`).
- **Implemented manual check-in:** API + UI backed by **`CheckInEvent`**.
- **Scoped non-MVP areas explicitly:** webhooks, RBAC, and automation left as **stubs** rather than half-finished behavior.

---

## 7. Constraints & Tradeoffs

- **Shared admin authentication:** single **`ADMIN_PASSWORD`**; **no RBAC** or per-user audit beyond `senderType: ops` on messages.
- **Broadcast notifications:** all recipients receive all alerts; **no routing logic** in code.
- **SQLite default:** chosen for **local/dev simplicity**; Postgres is a **configuration-level** swap, not migration-driven in-repo.
- **Disk-based uploads:** stored under `public/uploads`; **no** external object storage or scanning.
- **Partial HubSpot integration:** read + manual sync only; **no** webhook-driven updates.
- **Unused data model elements:** `OpsUser`, `firstResponseAt`, and check-in response state **not wired** into runtime behavior.

---

## 8. System Maturity & Delivery

**MVP-complete in this repository:**

- Client authentication via known email.
- Structured request + SOS + feedback persistence.
- Admin triage workflows with threaded context.
- Outbound notifications with per-attempt logging.
- Optional live integrations (Twilio, Resend).
- HubSpot-assisted client synchronization.
- Manual check-in messaging.

**Scaffolded or future-facing:**

- Webhook processing (Twilio, HubSpot).
- Response tracking (`firstResponseAt`, check-in reply state).
- Role-based admin model.

The result is **operationally usable** for a **bounded** environment: **MVP-ready**, not positioned as a fully scaled production system.

---

## 9. Lessons / Engineering Takeaways

- **Structured communication systems** outperform informal channels when operations require **accountability**.
- **Emergency paths** should be separated at **data and notification** layers—not only in UI.
- **Mockable integrations** enable realistic development and demos **without** hard provider dependency.

---

## Tech stack (from repository)

Next.js (App Router) · React · TypeScript · Tailwind CSS · Prisma · SQLite (default) / PostgreSQL (production target) · Twilio · Resend · HubSpot CRM API · Zod

# Elite Touch Cleaning — Proposals & Operations Portal

## Overview

Elite Touch Cleaning Services needed more than a contact form. Cape Fear Web Co delivered **two complementary systems**:

1. An **internal proposal builder** that turns structured service inputs into **branded multi-section PDFs**.
2. A **live client and operations portal** on a **custom client domain** for typed requests, SOS emergencies, ops triage, SMS/email notifications, and audit history.

A separate **read-only HubSpot forensic audit** mapped CRM risk before any destructive cleanup.

This write-up reflects **current shipped maturity** (not the earlier shared-password MVP framing). Credentials, tenant data, and private commercial terms are excluded.

**Private repos:** `elite-touch-proposals`, `elite-touch-client-portal`.

---

## The situation

The business operated across:

- Excel / Word / PDF proposal reference packets
- Phone and email for client issues and emergencies
- HubSpot as a large, complex system of record

Not every workflow was broken — but quoting and client ops were expensive, inconsistent, and hard to audit.

---

## Before → Intervention → After

### Problem 1 — Proposal creation

**Before:** Staff assembled proposals from spreadsheet specs and document templates. Packets were hard to keep consistent; contract/scope edits were easy to get wrong.

**Intervention:** Shipped an authenticated proposal wizard (client → location → type → property → scope → pricing → contract → review) with scope catalogs derived from Elite Touch Excel reference work, role-aware contract controls, and `@react-pdf/renderer` export for draft (watermarked) vs client-ready PDFs.

**After:** Proposal creation became a **repeatable software workflow** rather than ad-hoc document assembly.

**Honesty:** Proposal **pricing lines remain manual** in production. Pricing automation was researched with the client; it was **not shipped**. Do not claim Proposify (or any vendor) was replaced unless separately confirmed.

---

### Problem 2 — Client operations

**Before:** Service issues, feedback, and emergencies mixed across phone and inbox. Follow-up depended on who saw which thread.

**Intervention:** Built a production portal with:

- Client access (magic link / session flows)
- Typed requests (issues, notes, supplies) with threads and attachments
- Distinct **SOS** path with dedicated notification behavior
- Ops triage queues (open / urgent / closed), assignment, notes, CSV export
- **Twilio** SMS (including check-in loops and inbound handling) after **US toll-free verification approved**
- **Resend** email
- Notification attempt logging
- PWA install path for ops/clients
- Live on the client’s **custom domain**

**After:** Client issues and emergencies became **durable records** with triage and notification history — not inbox archaeology.

---

### Problem 3 — CRM visibility

**Before:** HubSpot held a large footprint (contacts, companies, deals, workflows, ownership quirks). Mutating it without a map was high-risk.

**Intervention:** Ran a **read-only** complete-current-state discovery (zero mutations required) and designed a phased remediation plan with hard gates.

**Scale observed (point-in-time snapshot class):** roughly **14k contacts**, **~4.6k companies**, **~2.2k deals**, and **dozens of workflows**.

**After:** The business has an evidence-based cleanup design. **Audit/remediation design ≠ cleanup completed** — no merges/deletes/stage moves without written approval.

---

## Verified

- Live client/ops portal on a custom client domain
- Branded multi-section proposal PDFs from a structured wizard
- Twilio US toll-free verification reached approved status
- Resend used for authentication/notification email
- HubSpot read-only discovery at the scale class above
- No HubSpot mutations until written gate approval
- Proposal pricing in production remains manual (automation not shipped)
- The two apps are complementary but architecturally separate (no shared proposal↔portal deal IDs)

## Still measuring

- Minutes per proposal before vs after
- Monthly proposal throughput / win-rate change
- SOS time-to-first-response improvement
- Employee hours saved

---

## Stack (representative)

Next.js · TypeScript · Prisma · PostgreSQL · Twilio · Resend · HubSpot · React PDF · Vercel

---

## CTA

If your team still quotes from spreadsheets or runs client issues through phone/email, send a project brief to Cape Fear Web Co — we’ll say what we’d audit, automate, or build.

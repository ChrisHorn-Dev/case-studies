# SiteOS — Construction Intelligence Platform

## 1. Overview

SiteOS is a **construction portfolio and project intelligence platform** for high-end and custom residential builders. It is not a generic contractor admin tool or a full construction ERP replacement.

The product combines **tenant project data**, **field input**, **external market signals** (federal awards, labor/material benchmarks, weather), and **document intelligence** into dashboards and workflows leadership can actually use in a weekly review — with honest labeling of data grain and confidence.

Work spans a **Python/FastAPI backend** with Celery workers, a **Next.js dashboard layer**, an **Expo mobile client** for field workflows, and ingestion pipelines that land structured data in PostgreSQL and time-series stores.

The codebase lives in a **private** repository. This write-up is non-proprietary and focuses on system design, architectural decisions, and product tradeoffs.

---

## 2. Problem Context

Custom builders often run projects across a messy stack: Dropbox folders, email threads, texts, spreadsheets, and memory for what is pending or at risk.

That creates predictable failure modes:

- **No single operational picture** — portfolio health and project risk are reconstructed manually each week.
- **Field signal is lost** — daily reports, weather delays, and site photos do not compound into decision support.
- **External context is disconnected** — macro cost/demand signals live in separate tabs, not next to tenant project state.
- **Client-facing decisions are ad hoc** — RFIs, change orders, and approvals lack a structured, citable record.

SiteOS targets builders who need an **intelligence layer** on top of how they already work — not another system of record to re-key the entire job into.

---

## 3. System Overview

SiteOS is a multi-surface platform with a shared data model and ingestion backbone.

### Core surfaces

- **Executive / portfolio:** health, exposure, demand/cost context, signal freshness
- **Project manager:** schedule, RFIs, invoices, document ingest, project Q&A with citations
- **Cost intelligence:** benchmark comparison with explicit national vs regional labeling
- **Signal coverage:** collector health, freshness, and operator-visible ingestion status
- **Field mobile (Expo):** daily reports, site context, lightweight capture workflows

### Backend platform

- **FastAPI** REST API + WebSockets for live updates
- **Celery + Redis** for scraping, ingestion, and long-running analysis jobs
- **PostgreSQL (Supabase)** for relational tenant and project data
- **TimescaleDB** for weather, telemetry, and time-series workloads
- **Cloudflare R2** for photos, documents, and ML artifacts
- **Claude API** and rules/templates for explainable document and RFI analysis where keys are configured

### Frontend & mobile

- **Next.js 14** persona dashboards with streaming-friendly layouts for weak job-site connectivity
- **Expo / React Native** field app aligned to the same project and daily-report model

### Infrastructure

- **Vercel** (frontend) + **Railway** (backend/workers) on current deployment paths
- Docker Compose for local full-stack development and demo runbooks

---

## 4. Data Architecture

SiteOS uses a layered model so scraped and tenant data do not mix casually.

**Layer 1 — Raw ingest queue**  
Everything collected lands here first as unvalidated JSON. Nothing in this layer is trusted.

**Layer 2 — Validation pipeline**  
Format checks, business rules, and anomaly detection. Failures quarantine with error detail; passes promote downstream.

**Layer 3 — Benchmark tables**  
Normalized public/reference data (labor, materials, safety, permits) available for cross-tenant comparison with explicit grain labels.

**Layer 4 — Tenant project data**  
Client-owned projects, daily reports, RFIs, invoices, learning events, and AI generation logs — isolated per builder.

This separation keeps **demo/market signals** honest while **tenant workflows** stay authoritative for operational decisions.

---

## 5. Product Wedge

> The main competitor is not only Procore — it is **Dropbox + email + texts + spreadsheets + memory**.

SiteOS wins when a builder gets session-one clarity on:

1. What changed on a project
2. What needs a decision now
3. What to tell the client — with sources

The platform is positioned as a **lighter intelligence layer**, not a Procore replacement.

---

## 6. Engineering Decisions

| Decision | Why |
|---|---|
| **Python backend** | Scraping, ML, and document pipelines share one ecosystem (FastAPI, Celery, pandas, CV/LLM tooling). |
| **PostgreSQL over document store** | Construction data is relational; JSONB handles unstructured scrape payloads without giving up joins. |
| **Supabase** | Managed Postgres, RLS for tenant isolation, auth, and real-time without standing up bespoke infra. |
| **TimescaleDB** | Weather and telemetry at scale without crushing OLTP query performance. |
| **Celery over cron** | Retries, queues, priorities, and Flower monitoring for data-dependent jobs. |
| **Cloudflare R2** | S3-compatible storage without egress fees on photo-heavy dashboards. |
| **Next.js App Router** | SSR/streaming for dashboards on slow connections; parallel section loading matters in the field. |

---

## 7. Core Workflows

### Portfolio signal desk

Leadership opens a weekly (or pre-bid) review combining federal demand signals, macro cost posture, portfolio execution state, and collector health — one narrative instead of four browser tabs.

### Project knowledge & document ingest

Builders organize messy project material (folder ingest, PDF/TXT/DOCX). Extracted facts are reviewable; project Q&A and intelligence surfaces cite sources rather than presenting opaque model output.

### Field → platform loop

Daily reports, weather flags, and mobile capture feed the same longitudinal project record ingestion and UI both read — so usage compounds instead of resetting each session.

### Decision packets

Client-ready decision packaging via share flows — structured outputs for approvals and next steps, not raw internal notes.

---

## 8. Constraints & Tradeoffs

- **Intelligence over ERP parity** — no legal e-signature, certified pay apps, or full PM replacement in v1.
- **Explainability over magic** — rules, templates, and cited LLM outputs beat “AI that reads everything” without review.
- **Honest data grain** — national vs state benchmarks and demo/sample labels are product requirements, not footnotes.
- **Breadth vs coherence** — inactive persona surfaces are not marketed as shipped; v1 anchors on a named portfolio review workflow.
- **Private codebase** — public proof is architecture and product reasoning, not proprietary ingest contracts or tenant data.

---

## 9. System Maturity

At this stage, the platform includes:

- Multi-surface Next.js dashboards with investor-demo navigation paths
- FastAPI backend with documented ingestion and public-data routes
- Celery workers, beat scheduling, and operator-visible job monitoring patterns
- Document intelligence, project knowledge, and decision-packet product phases on `main`
- Local Docker stack and demo runbooks for reproducible environments
- Mobile field client aligned to shared project/daily-report models

---

## 10. Lessons Learned

- Builders buy **clarity under chaos**, not feature checklists — the UI must feel calm, sourced, and expensive.
- External signals only help when **grain and freshness** are visible next to tenant state.
- Field input is only valuable when it **feeds the same record** dashboards and intelligence read.
- Platform work fails at **boundaries** — ingest validation, tenant isolation, and job observability matter as much as dashboards.

---

## Tech Stack

Python 3.11 · FastAPI · Celery · Redis · PostgreSQL · Supabase · TimescaleDB  
Next.js 14 · React · TypeScript · Expo · React Native  
scikit-learn · XGBoost · Claude API · Cloudflare R2  
Docker · Vercel · Railway · Upstash

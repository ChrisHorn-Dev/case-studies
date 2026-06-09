# SiteOS — Construction Execution Intelligence from Field Signals to Executive Dashboards

**Status:** Draft — architecture-focused case study for a private repository  
**Repo:** Private — `ChrisHorn-Dev/siteos`  
**Related:** `siteos-signal-engine` (county-level signal foundation), `first-week-siteos` (screenshot bundle)  
**Public code:** Not shared — this document is the public proof  
**Screenshot status:** Placeholders below — assets available in `first-week-siteos/` locally

---

## Overview

SiteOS is a **construction intelligence platform** positioned as an operating system for construction execution intelligence. It connects field activity, project signals, and operational data to **multi-persona dashboards** for general contractors, foremen, and executives, with a mobile field app and backend services for ingestion, background jobs, and ML-assisted workflows.

This is not a single dashboard — it is a **platform** spanning API services, workers, time-series data, file storage, and persona-specific frontends.

---

## Problem

Construction operations often run on fragmented tools: spreadsheets, disconnected jobsite photos, delayed RFIs, and executive views that lag field reality. Teams need:

- A **single operational picture** across projects and roles  
- **Signal continuity** from permits, weather, jobsite activity, and project milestones  
- **Actionable dashboards** rather than static reporting  
- Infrastructure that can grow from MVP demos toward production workloads  

---

## My Role

**[Needs user input]**

Suggested placeholders to fill in:

- Solo vs team contribution  
- Areas owned: backend API, frontend dashboards, mobile, ML integration, DevOps, product scoping  
- Timeline of involvement  

---

## Product Goals

- Provide **persona-specific dashboards** (GC, foreman, executive, etc.)  
- Ingest and normalize **construction-related signals** (including county-level foundation via signal engine)  
- Support **demo-ready project intelligence** with seeded demo projects  
- Enable **ML/CV and LLM-assisted workflows** for document analysis and operational prediction  
- Maintain a **credible full-stack architecture** on modern hosting (Vercel + Railway patterns documented in repo)  

---

## System Architecture

| Layer | Technology | Purpose |
|-------|------------|---------|
| Backend API | FastAPI (Python 3.11) | REST + WebSockets |
| Job scheduler | Celery + Redis | Scraping + background jobs |
| Primary DB | PostgreSQL (Supabase) | Core data |
| Time-series | TimescaleDB | Weather, telemetry |
| Cache/queue | Redis (Upstash) | Cache + Celery broker |
| Storage | Cloudflare R2 | Photos, docs, ML artifacts |
| ML/CV | scikit-learn, XGBoost, YOLOv8 | Predictions + computer vision |
| LLM | Claude API (Anthropic) | Document analysis, RFIs |
| Frontend | Next.js 14 + React | Multi-persona dashboards |
| Mobile | React Native + Expo | Field foreman app |
| Hosting | Vercel + Railway | Documented deployment paths |

**Related subproject:** `siteos-signal-engine` — independent FastAPI service for county-FIPS normalization, raw ledger, and continuity scoring. Public positioning: **part of SiteOS architecture**, not a separate flagship.

```
Field / external signals
        │
        ▼
┌───────────────────┐     ┌────────────────────┐
│ Signal Engine     │────▶│ FastAPI backend    │
│ (county signals)  │     │ + Celery workers   │
└───────────────────┘     └─────────┬──────────┘
                                      │
                    ┌─────────────────┼─────────────────┐
                    ▼                 ▼                 ▼
              PostgreSQL         TimescaleDB      Cloudflare R2
                    │                 │
                    └────────┬────────┘
                             ▼
              Next.js dashboards + Expo mobile
```

---

## Key Features

- Multi-persona **dashboard surfaces** with demo project seeding  
- **Docker-compose local stack** for full development parity  
- **Alembic migrations** and structured backend modules  
- **Demo runbooks** and investor/demo readiness documentation in-repo  
- **Signal engine API** endpoints for county-level intelligence foundation  
- ML/CV and LLM integration points for operational workflows (RFIs, predictions)  

---

## Technical Decisions

- **Monorepo with clear backend/frontend split** — keeps API contracts explicit while allowing independent deploy paths  
- **Celery for long-running ingestion** — avoids blocking HTTP workers on scrape/ML tasks  
- **TimescaleDB for telemetry-class data** — separates time-series concerns from relational core  
- **Demo-first seed projects** — enables stakeholder walkthroughs without production data  
- **Signal engine as separate service** — allows independent evolution of ingestion normalization  

---

## Challenges

**[Needs user input — suggested prompts]**

- Hardest integration or data source?  
- Demo vs production gap?  
- Performance or infra constraints on Railway/Vercel free tiers?  
- ML/CV workflow reliability?  

---

## Outcome

No fabricated metrics. Document only verified outcomes:

- Platform architecture implemented across backend, workers, frontend, and mobile paths  
- Demo readiness documented in `docs/demo/` and audit materials  
- Active development as of 2026-06-06  

**Placeholders:**

- [insert user count]  
- [insert demo milestone]  
- [insert live URL if any]  
- [insert measurable outcome]  

---

## What I'd Improve Next

- Expand production hardening beyond demo seed paths  
- SSR/prerender for critical dashboard URLs if analytics justify it  
- Deeper observability across Celery workers and ML pipelines  
- Consolidate screenshot/deliverable assets into a single brand-ready folder  

---

## Screenshots Needed

| File | Description | Priority |
|------|-------------|----------|
| `siteos-01-executive-dashboard.png` | Executive dashboard | Required |
| `siteos-02-project-intelligence.png` | Project detail / intel view | Required |
| `siteos-03-signal-engine.png` | Signal/data view | Helpful |
| `siteos-04-mobile-field-workflow.png` | Mobile/field workflow | Required |
| `siteos-05-architecture-diagram.png` | Architecture diagram | Required |
| `siteos-demo-60s.mp4` | Walkthrough video | Optional |

Local reference: `/Users/chorn/Desktop/first-week-siteos/` contains PNGs aligned to these names.

---

## Links

- **Private repo:** `github.com/ChrisHorn-Dev/siteos` (private)  
- **Related private repo:** `github.com/ChrisHorn-Dev/siteos-signal-engine`  
- **Portfolio:** [chrisos.dev](https://chrisos.dev)  
- **Other case studies:** [Physician Connection](./physician-connection.md) · [Elite Touch](./elite-touch-cleaning.md) · [Cape Fear Web Co](./cape-fear-web-co.md)

---

## Questions for Chris

1. What percentage of SiteOS did you personally build?  
2. Is any part live beyond local/docker demo?  
3. Can investor/client names appear in public materials?  
4. What outcome are you most proud of (even without metrics)?  
5. Any sections that must **not** mention ML, scrapers, or specific data sources?

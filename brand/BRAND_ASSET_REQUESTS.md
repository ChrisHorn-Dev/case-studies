# Brand Asset Requests

**Owner:** Chris Horn  
**Last updated:** 2026-06-09  
**Purpose:** Centralized screenshot, video, and diagram checklist for GitHub READMEs, case studies, ChrisOS, LinkedIn, and resume materials.

**Safety rule:** Do not commit client PII, PHI, production credentials, API keys, or unsanitized pricing. Use mock/demo modes where available.

---

## Naming Conventions

### File pattern

```
{project-slug}-{nn}-{short-description}.{ext}
```

| Component | Rule | Examples |
|-----------|------|----------|
| `project-slug` | Lowercase kebab-case matching repo or brand slug | `siteos`, `elite-touch`, `physician-connection`, `cape-fear-portal` |
| `nn` | Two-digit sequence, zero-padded | `01`, `02`, `03` |
| `short-description` | Kebab-case, 2–4 words max | `executive-dashboard`, `sos-flow` |
| `ext` | `png` for UI; `gif` for gameplay; `mp4` for video; `svg` for diagrams | `.png`, `.gif`, `.mp4`, `.svg` |

### Subproject prefixes

| Project | Slug prefix |
|---------|-------------|
| Elite Touch Client Portal | `elite-touch-` |
| Elite Touch Proposals | `elite-touch-proposals-` |
| Physician Connection | `physician-connection-` |
| SiteOS | `siteos-` |
| SiteOS Signal Engine | `siteos-signal-engine-` |
| Regen Profits Sales App | `regen-profits-` |
| Remember Me | `remember-me-` |
| ChrisOS | `chrisos-` |
| Media Authenticity API | `media-auth-` |
| Cape Fear Web Co (marketing) | `cape-fear-` |
| Cape Fear Client Portal | `cape-fear-portal-` |
| Genesis Mastery | `genesis-mastery-` |
| Wilmington Engine | `wilmington-engine-` |
| Visual Conversations | `visual-conversations-` |
| Pathbound Mobile | `pathbound-` |

### Storage locations

| Destination | Path | Notes |
|-------------|------|-------|
| Case studies repo | `case-studies/assets/{project-slug}/` | Public-safe only |
| ChrisOS | `resume-os/public/assets/projects/{project-slug}/` | Optimize for web |
| GitHub READMEs | Relative in each repo `docs/assets/` or `public/` | Match repo convention |
| LinkedIn | Export from above — 1200×627 crop for link posts | No repo commit required |
| Local working | `~/Desktop/brand-assets/{project-slug}/` | Pre-sanitization staging |

### Capture settings

- **Resolution:** 1440×900 desktop; 390×844 mobile (iPhone 14 Pro frame optional)
- **Browser:** Chrome, light mode unless app is dark-only
- **Font smoothing:** Default; no OS UI chrome unless demonstrating PWA install
- **Annotations:** None on raw captures; annotate in Figma if needed for diagrams only

---

## Where Assets Are Used

| Channel | Asset types | Priority projects |
|---------|-------------|-------------------|
| **GitHub README** | Hero screenshot, architecture diagram | media-auth-api, physician-connection, siteos, resume-os |
| **Case study** | Full flow screenshots, architecture diagrams | All flagship private work |
| **ChrisOS** | Card thumbnails, deep-dive hero images | Featured cards in `projects.ts` |
| **LinkedIn** | Mobile-first UI, before/after diagrams, 60s demo clips | Elite Touch, PC, SiteOS, Regen Profits, ChrisOS |
| **Resume** | 1 hero image per flagship + architecture diagram | PC, SiteOS, Elite Touch, Cape Fear |
| **Profile README** | Badge-style thumbnails in featured sections | Top 4 flagships + ChrisOS |

---

## Priority Legend

| Level | Meaning |
|-------|---------|
| **Required** | Blocks case study publish, LinkedIn flagship post, or README 5/5 |
| **Helpful** | Improves credibility; ship within 30 days |
| **Optional** | Only if project promoted beyond current ChrisOS card |

---

## 1. Elite Touch Cleaning Companion App

**Repo:** `elite-touch-client-portal` (private)  
**Capture mode:** `MOCK_INTEGRATIONS=true`, local SQLite, Playwright `e2e:smoke` or manual  
**Scripts:** `capture:sms-terms`, Playwright specs in `e2e/`

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Client home / launcher | `elite-touch-01-client-launcher.png` | PNG | Case study, ChrisOS, LinkedIn, resume | **Required** |
| Request modal flow (issue/note/supply) | `elite-touch-02-request-flow.png` | PNG | Case study | **Required** |
| SOS emergency flow | `elite-touch-03-sos-flow.png` | PNG | Case study, LinkedIn | **Required** |
| Threaded messages on request detail | `elite-touch-04-message-thread.png` | PNG | Case study | **Required** |
| Admin triage queue (open/urgent/closed) | `elite-touch-05-admin-queue.png` | PNG | Case study, resume | **Required** |
| Mobile client view | `elite-touch-06-mobile-client.png` | PNG | LinkedIn | Helpful |
| HubSpot sync admin panel | `elite-touch-07-hubspot-sync.png` | PNG | Case study appendix | Optional |
| Notification audit log | `elite-touch-08-notification-events.png` | PNG | Case study technical section | Optional |
| System flow diagram | `elite-touch-09-system-flow.svg` | SVG | Case study, resume | Helpful |

**Privacy:** Sanitize client names, phone numbers, SMS/email content, HubSpot record IDs.

---

## 2. Elite Touch Proposal App

**Repo:** `elite-touch-proposals` (private)

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Proposal builder dashboard | `elite-touch-proposals-01-dashboard.png` | PNG | Elite Touch case study section | Helpful |
| Branded PDF preview | `elite-touch-proposals-02-pdf-preview.png` | PNG | LinkedIn (ecosystem post) | Optional |
| Scope catalog alignment view | `elite-touch-proposals-03-scope-catalog.png` | PNG | Case study technical section | Optional |

**Privacy:** Redact client names, pricing, and proprietary scope rates.

---

## 3. Physician Connection

**Repo:** `physician-connection` (private)  
**Script:** `pnpm demo:capture` → `scripts/capture-demo-screenshots.ts`

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Rep dashboard | `physician-connection-01-rep-dashboard.png` | PNG | Case study, ChrisOS, LinkedIn | **Required** |
| Practice calendar view | `physician-connection-02-practice-calendar.png` | PNG | Case study | **Required** |
| Guided booking flow | `physician-connection-03-booking-flow.png` | PNG | LinkedIn, resume | **Required** |
| Super-admin operational surface | `physician-connection-04-super-admin.png` | PNG | Case study | Helpful |
| Platform architecture diagram | `physician-connection-05-architecture.png` | PNG/SVG | Case study, resume, LinkedIn | **Required** |
| Role routing diagram | `physician-connection-06-role-routing.svg` | SVG | Case study | Helpful |
| Cal.com integration sequence | `physician-connection-07-calcom-flow.svg` | SVG | Case study technical section | Optional |

**Privacy:** HIPAA-adjacent — anonymize all PHI, practice names, physician names, territories. Use seeded test data only.

---

## 4. SiteOS

**Repo:** `siteos` (private)  
**Local reference:** `/Users/chorn/Desktop/first-week-siteos/*.png`

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Executive dashboard | `siteos-01-executive-dashboard.png` | PNG | Case study, profile README, LinkedIn | **Required** |
| Project intelligence view | `siteos-02-project-intelligence.png` | PNG | Case study | **Required** |
| Signal engine / county signals | `siteos-03-signal-engine.png` | PNG | SiteOS case study | Helpful |
| Mobile field workflow (Expo) | `siteos-04-mobile-field-workflow.png` | PNG | Case study | **Required** |
| Full platform architecture | `siteos-05-architecture-diagram.png` | PNG/SVG | Case study, LinkedIn, resume | **Required** |
| Celery worker / job queue diagram | `siteos-06-worker-pipeline.svg` | SVG | Case study technical section | Helpful |
| Demo walkthrough video | `siteos-demo-60s.mp4` | MP4 | LinkedIn | Optional |

**Action:** Copy/rename existing `first-week-siteos` PNGs to `siteos-01-*` convention before publishing.

---

## 5. SiteOS Signal Engine

**Repo:** `siteos-signal-engine` (private) — subcomponent of SiteOS

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Signal ingestion flow | `siteos-signal-engine-01-flow.png` | PNG/SVG | SiteOS case study | Helpful |
| County FIPS normalization diagram | `siteos-signal-engine-02-county-fips.svg` | SVG | Case study technical section | Optional |

---

## 6. Regen Profits Sales App

**Repo:** `regen-profits-sales-app` (private)  
**Staging:** `https://regen-profits-sales-app.vercel.app`

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Mobile rep dashboard | `regen-profits-01-mobile-rep-dashboard.png` | PNG | Case study, ChrisOS, LinkedIn | **Required** |
| Leaderboard | `regen-profits-02-leaderboard.png` | PNG | LinkedIn | **Required** |
| Daily sales entry form | `regen-profits-03-sales-entry.png` | PNG | Case study | **Required** |
| Admin command center | `regen-profits-04-admin-command-center.png` | PNG | Case study, resume | **Required** |
| PWA install prompt | `regen-profits-05-pwa-install.png` | PNG | LinkedIn (technical post) | Helpful |
| Supabase RLS diagram | `regen-profits-06-rls-boundaries.svg` | SVG | Case study | Optional |

**Privacy:** Confirm client approval before any public use. Default to anonymized naming. No Supabase keys or test passwords in frame.

---

## 7. Remember Me

**Repo:** `remember-me-app` (private)  
**Capture mode:** `/demo` path (localStorage, no Supabase required)

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Landing page | `remember-me-01-landing.png` | PNG | ChrisOS, case study | **Required** |
| Dashboard (wishlists/reminders) | `remember-me-02-dashboard.png` | PNG | Case study | **Required** |
| Thinking of You draft flow | `remember-me-03-thinking-of-you.png` | PNG | LinkedIn | **Required** |
| Demo mode banner | `remember-me-04-demo-mode.png` | PNG | Case study (technical decision proof) | Helpful |
| Mobile responsive layout | `remember-me-05-mobile.png` | PNG | LinkedIn | **Required** |
| Phase 1 scope diagram | `remember-me-06-phase-boundaries.svg` | SVG | Case study | Optional |

---

## 8. ChrisOS / resume-os

**Repo:** `resume-os` (public) · **Live:** `https://chrisos.dev`

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Desktop shell (windows + dock) | `chrisos-01-desktop-shell.png` | PNG | GitHub README, LinkedIn Featured | **Required** |
| Mobile shell (launcher) | `chrisos-02-mobile-shell.png` | PNG | resume-os README | **Required** |
| Project deep-dive view | `chrisos-03-deep-dive.png` | PNG | Case study optional, LinkedIn | Helpful |
| Terminal interaction | `chrisos-04-terminal.png` | PNG | GitHub README | Optional |
| Window manager diagram | `chrisos-05-architecture.svg` | SVG | README technical section | Helpful |

---

## 9. Media Authenticity API

**Repo:** `media-auth-api` (public)

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Built-in test UI (localhost) | `media-auth-01-test-ui.png` | PNG | GitHub README, case study | **Required** |
| API pipeline flow diagram | `media-auth-02-api-flow-diagram.png` | PNG/SVG | Case study, LinkedIn | **Required** |
| Verify endpoint response | `media-auth-03-verify-response.png` | PNG | README, case study | Helpful |
| Detector registry module map | `media-auth-04-module-map.svg` | SVG | Case study | Optional |

**Privacy:** No `SIGNING_SECRET`, `HUGGINGFACE_API_KEY`, or real API keys in screenshots.

---

## 10. Cape Fear Web Co

**Repo:** `Cape-Fear-Web-Co-Web` (private) · **Live:** `https://capefearweb.co`

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Homepage hero | `cape-fear-01-homepage-hero.png` | PNG | Case study, LinkedIn Featured | **Required** |
| Case studies index | `cape-fear-02-case-studies-index.png` | PNG | Case study | Helpful |
| Topic anchor page (e.g. internal-tools) | `cape-fear-03-topic-page.png` | PNG | LinkedIn | Optional |
| SEO / JSON-LD diagram | `cape-fear-04-seo-structure.svg` | SVG | Case study technical section | Helpful |
| SPA architecture (marketing + portal modes) | `cape-fear-05-spa-modes.svg` | SVG | Case study | Helpful |

---

## 11. Cape Fear Client Portal

**Subproject of Cape-Fear-Web-Co-Web** at `/portal/*`

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Portal messages thread | `cape-fear-portal-01-messages.png` | PNG | Case study | **Required** |
| Typed client requests | `cape-fear-portal-02-requests.png` | PNG | Case study | Helpful |
| File uploads view | `cape-fear-portal-03-files.png` | PNG | Case study | Optional |
| Activity feed | `cape-fear-portal-04-activity.png` | PNG | Case study | Optional |
| Portal RLS / auth diagram | `cape-fear-portal-05-rls-auth.svg` | SVG | Case study technical section | Helpful |

**Privacy:** Use test organization only. Sanitize client org names, project titles, filenames.

---

## 12. Genesis Mastery

**Repo:** `genesis-mastery` (private) — promote only when polished

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Student dashboard | `genesis-mastery-01-dashboard.png` | PNG | ChrisOS (if promoted) | Optional |
| Lesson reader | `genesis-mastery-02-lesson.png` | PNG | LinkedIn | Optional |
| Instructor CMS | `genesis-mastery-03-admin-cms.png` | PNG | Case study (if written) | Optional |

---

## 13. Wilmington Engine

**Repo:** `wilmington-news` (private) — deprioritize for brand

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Pipeline architecture diagram | `wilmington-engine-01-pipeline.svg` | SVG | ChrisOS lab card only | Optional |
| Content queue admin stub | `wilmington-engine-02-admin-stub.png` | PNG | — | Optional |

---

## 14. Visual Conversations

**Repo:** `visual-conversations` (private)

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Chrome extension popup | `visual-conversations-01-extension-popup.png` | PNG | ChrisOS, LinkedIn dev-tool post | Optional |
| CLI session output | `visual-conversations-02-cli-session.png` | PNG | GitHub README | Optional |
| DOM digest → LLM flow | `visual-conversations-03-flow.svg` | SVG | README | Optional |

**Privacy:** Use localhost pages only; no production site DOM content.

---

## 15. Pathbound Mobile

**Repo:** `pathbound-mobile` (private)

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Gameplay loop GIF | `pathbound-01-gameplay.gif` | GIF | LinkedIn personality post | Optional |
| Haven Clearing map screenshot | `pathbound-02-haven-clearing.png` | PNG | ChrisOS lab card | Optional |
| Map composer tooling | `pathbound-03-map-composer.png` | PNG | Technical blog optional | Optional |
| Godot vs Expo pivot diagram | `pathbound-04-direction-reset.svg` | SVG | — | Optional |

---

## 16. case-studies Repo (shared assets)

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Case studies index hero | `case-studies-01-index-hero.png` | PNG | case-studies README | Helpful |
| Architecture proof pattern diagram | `case-studies-02-proof-model.svg` | SVG | README explainer | Helpful |

---

## 17. ChrisHorn-Dev Profile README

| Asset | Filename | Format | Used in | Priority |
|-------|----------|--------|---------|----------|
| Profile banner (optional) | `chris-horn-01-profile-banner.png` | PNG | GitHub profile | Optional |
| Featured work composite | `chris-horn-02-featured-grid.png` | PNG | Profile README | Helpful |

---

## Master Priority Queue

### Week 1 — Required (blocks flagship posts)

1. `elite-touch-01` through `elite-touch-05`
2. `physician-connection-01` through `physician-connection-03` + `05-architecture`
3. `siteos-01`, `02`, `05` (rename from `first-week-siteos`)
4. `chrisos-01`, `chrisos-02`
5. `media-auth-01`, `media-auth-02`

### Week 2 — Required (draft case study publish)

6. `regen-profits-01` through `04` (after client approval)
7. `remember-me-01` through `03`, `05`
8. `cape-fear-01`, `cape-fear-portal-01`

### Week 3 — Helpful

9. `siteos-04-mobile`, `siteos-03-signal-engine`
10. `elite-touch-06-mobile`, `physician-connection-04`
11. `cape-fear-portal-02`, `cape-fear-02`

### Backlog — Optional

- All Genesis, Wilmington, Visual Conversations, Pathbound assets
- Video: `siteos-demo-60s.mp4`

---

## Asset Request Template (per capture session)

Copy for each batch:

```markdown
## Capture session: [DATE]
**Project:** [name]
**Environment:** [local / staging / demo mode]
**Sanitization:** [ ] names [ ] phones [ ] PHI [ ] pricing [ ] API keys
**Files captured:**
- [ ] filename → destination path
**Approved for public:** [ ] case study [ ] LinkedIn [ ] ChrisOS [ ] GitHub README
**Client approval (if applicable):** [ ] yes [ ] pending [ ] N/A
```

---

## Cross-References

- Execution tasks: `BRAND_REVAMP_EXECUTION_PLAN.md`
- Registry metadata: `BRAND_PROJECT_REGISTRY.md`
- Case study drafts: `case-studies/*.md`
- Prior checklist: `case-studies/PROJECT_ASSET_REQUESTS.md` (subset — superseded by this file for brand revamp)

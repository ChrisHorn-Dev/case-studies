# Media Authenticity API

**Status:** Published overview — complements public repository  
**Repo:** Public — [github.com/ChrisHorn-Dev/media-auth-api](https://github.com/ChrisHorn-Dev/media-auth-api)  
**Screenshot status:** Pending  

---

## Overview

Verification-oriented **HTTP API** that analyzes uploaded images for likely synthetic vs likely authentic content, returns **HMAC-signed authenticity records**, and exposes `POST /api/verify` so clients can confirm results were not tampered with.

Public code is the proof; this case study explains the **system design** for recruiters and technical peers.

---

## Problem

Teams exploring media authenticity need more than a raw model score — they need a clear API surface, caching, rate limiting, and **verifiable signed responses**.

---

## Stack

Next.js API routes · TypeScript · Hugging Face Inference API · Vitest

---

## Architecture

```
Client upload
    → validate (size/type/dimensions)
    → hash → cache lookup
    → detector orchestrator (single | ensemble)
    → signed authenticity record
    → optional POST /api/verify
```

**Core modules:** orchestrator, detector registry, cache, signer (HMAC-SHA256 over canonical payload).

---

## Key Features

- `POST /api/analyze` and batch endpoint (max 5 files)  
- Single and ensemble detector modes  
- File-hash caching (TTL configurable)  
- Optional API key + in-memory rate limiting  
- Built-in test UI at localhost for manual verification  
- Vitest coverage for analyze + verify paths  

---

## Technical Decisions

- **Signed records** — downstream systems can verify independently  
- **Detector abstraction** — supports multiple Hugging Face image models  
- **Honest scope** — audio/video types stubbed; image path only implemented  

---

## Outcome

- Public repository with documented API and tests  
- [insert adoption metric if any]  
- [insert live demo URL if deployed]  

---

## Screenshots Needed

| File | Description | Priority |
|------|-------------|----------|
| `media-auth-01-test-ui.png` | Built-in test UI | Required |
| `media-auth-02-api-flow-diagram.png` | Pipeline diagram | Required |
| `media-auth-03-verify-response.png` | Verify endpoint proof | Helpful |

---

## Links

- **Repository:** [media-auth-api](https://github.com/ChrisHorn-Dev/media-auth-api)  
- **Portfolio:** [chrisos.dev](https://chrisos.dev)  

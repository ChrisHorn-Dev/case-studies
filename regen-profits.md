# Regen Profits — Sales Ops, Territory & Portal

## Overview

Multi-system engagement for a multi-rep B2B sales organization (Regen Profits): a **mobile-first sales PWA**, an internal **CRM-backed territory map**, and an owned **marketing site + authenticated portal** — handed off to **client-owned GitHub and Vercel**.

Private code. This page stays claim-safe: no fabricated adoption, revenue, or clinic-count achievements.

---

## Before → Intervention → After

**Before:** Field activity and commissions needed a phone-first system of record; territory ZIP claims in GoHighLevel were hard to trust visually; marketing lived on Webflow while clinic/presenter conversion needed an owned portal congruent with CRM.

**Intervention:**

1. **Sales PWA** — reps/admins log sales and activity; event-based funnel metrics; estimated commission rules (including pay-on-collected); admin oversight; Supabase RLS; Vercel install-via-link.
2. **Territory map** — GHL ZIP overlays on national ZCTA geometry (**33,791** ZCTAs via PMTiles); provenance export; cache-first sync hardening.
3. **Website + portal** — clinics-first marketing + Clerk/Neon portal with CRM outbox sync; cutover from prior Webflow hosting onto client domains.

**After:** Field logging, territory visibility, and acquisition/onboarding surfaces run as production systems the client owns.

---

## Verified

- Mobile-first sales tracking PWA with role-based access
- Event-based activity tracking replaced manual pipeline entry
- Commission logic including pay-on-money-collected rules
- Territory map over 33,791 ZCTAs with GHL ZIP import
- Marketing site + authenticated portal with CRM outbox sync
- Delivery handed to client-owned GitHub/Vercel

## Still measuring

- Active rep count / daily logging rate
- Commission dispute reduction
- Portal conversion rates

---

## Stack (representative)

Next.js · TypeScript · Supabase · GoHighLevel · Clerk · Neon · Drizzle · Vercel · PMTiles

---

## CTA

If your sales org still lives in spreadsheets and CRM ZIP fields nobody trusts on a map, send a brief to Cape Fear Web Co.

# PARI — Bootstrap Handoff — 2026-08-24

## Objective
Build PARI as a local-first verified community for entrepreneurs and self-employed professionals. The product is designed around real-world meetings, not endless swiping.

## Product model
PARI combines:
- decentralized user-created tables (Tablo pattern),
- recurring local circles and trust-building (BNI pattern),
- host progression / quality control (Comehome pattern),
- curated composition (Timeleft pattern),
- entrepreneur verification and explicit intent (`LOVE / BUSINESS / OPEN / SOCIAL`).

## Product rules
1. Verified before visible.
2. Real life before endless chat.
3. Intentions are explicit.
4. No forced referrals; no forced romance.
5. Quality of the room beats quantity in the room.
6. Hosts create experiences; PARI governs access and trust.
7. No public star rating of people.
8. Post-event interest is private and only creates a connection when reciprocal.
9. Reliability protects the group from no-shows; it is not a popularity score.
10. Local density before geographic expansion.

## v0.1 technical scaffold completed locally
Validated locally on 2026-08-24:
- `wrangler.jsonc` for Cloudflare Worker + Static Assets + D1
- `migrations/0001_core.sql`
- `src/worker.js`
- `public/index.html`
- `public/styles.css`
- `public/app.js`
- `README.md`
- `docs/PRODUCT_RULES.md`

Syntax validation passed for Worker and browser JS. D1 migration was executed successfully against an in-memory SQLite compatibility check and produced the expected core tables.

## Core D1 entities
- members
- availability
- tables
- table_requests
- post_event_intents
- matches

## Core v0.1 API
- `GET /api/health`
- `GET /api/tables`
- `POST /api/tables`
- `POST /api/tables/:id/request`
- `POST /api/tables/:id/intent`

## Safety / privacy gates before production
Production is blocked until all of the following are implemented and reviewed:
- 18+ gate
- identity verification design
- entrepreneur / VAT verification design
- consent and privacy disclosures
- sensitive-data minimization
- block/report/moderation
- delete/export account flows
- exact-location protection
- real Founding Member approval for personal/romantic profile data
- host moderation and appeal rules
- reliability/no-show policy
- auth/session hardening
- billing boundaries

## Deployment governance
- staging Worker intended: `pari-staging`
- staging D1 intended: `pari-staging-db`
- production Worker: NOT CREATED
- production D1: NOT CREATED
- production domain: UNVERIFIED
- production deploy: FORBIDDEN until staging acceptance and product/safety gates pass

## Repository blocker
A dedicated PARI repository does not yet exist in the connected GitHub account. The current GitHub connector can write to existing repositories but does not expose repository creation. Do not place PARI source inside VinoVeritas, Splendoria or 247Agent repositories. Create a dedicated private repository (recommended name: `PARI`) and then import the validated v0.1 scaffold there.

## Immediate next milestone
`M1 — Real local marketplace loop`

Member verified → discovers local PARI Table → requests a seat → Host/PARI composition → attends → private post-event intent → reciprocal Business/Love/Both Match.

## Commercial validation target
Before adding complex AI matching, prove one city / cluster can sustain repeated real-world meetings with:
- verified members,
- trained hosts,
- recurring Friday/Saturday inventory,
- low no-show rate,
- meaningful second meetings,
- willingness to pay for access/events/membership.

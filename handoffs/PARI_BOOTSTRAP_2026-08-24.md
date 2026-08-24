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

## v0.2 pilot scaffold completed locally
Validated locally on 2026-08-24:
- Cloudflare Worker + Static Assets architecture
- D1 migrations `0001_core.sql` + `0002_pilot_controls.sql`
- synthetic-only staging seed
- mobile-first member UI
- Host request/attendance control panel
- Weekend Sync UI
- match inbox UI
- JavaScript syntax validation
- sequential SQLite validation of both migrations + seed

## D1 entities
Core:
- members
- availability
- tables
- table_requests
- post_event_intents
- matches

Pilot controls:
- consent_records
- member_blocks
- reports
- reliability_events

## v0.2 API coverage
Discovery / tables:
- `GET /api/health`
- `GET /api/cities`
- `GET /api/tables`
- `POST /api/tables`
- `POST /api/tables/:id/request`
- `GET /api/tables/:id/requests`
- `POST /api/tables/:id/requests/:memberId`
- `POST /api/tables/:id/cancel`

Attendance / reliability:
- `POST /api/tables/:id/attendance/:memberId`

Weekend Sync:
- `PUT /api/members/:id/availability`
- `GET /api/weekend-sync`

Post-event matching:
- `POST /api/tables/:id/intent`
- `GET /api/matches`

Safety / consent primitives:
- `POST /api/members/:id/consent`
- `POST /api/members/:id/block/:otherId`
- `DELETE /api/members/:id/block/:otherId`
- `POST /api/reports`

## M1 logic implemented locally
Verified member → discovers local PARI Table → requests a seat → Host accepts/waitlists/declines → capacity-safe control → attendance/no-show → reliability ledger → private post-event intent → reciprocal Business/Love/Both Match.

Additional safeguards already encoded:
- automatic first waitlist promotion after accepted-member cancellation
- post-event intent rejected unless both members attended the same table
- blocked pairs excluded from discovery/matching
- reliability bounded to 0–100
- synthetic profiles only in staging seed

## Safety / privacy gates before real personal data or production
Production remains blocked until all of the following are implemented and reviewed:
- production-grade auth/session layer
- 18+ gate and auditable consent
- identity verification design
- entrepreneur / VAT verification design
- privacy disclosures and granular sensitive-data consent
- delete/export account flows
- exact-location protection
- real Founding Member approval for personal/romantic profile data
- admin moderation queue and appeal rules
- rate limiting / Turnstile on abuse-sensitive endpoints
- billing boundaries

## Deployment governance
- intended staging Worker: `pari-staging`
- intended staging D1: `pari-staging-db`
- production Worker: NOT CREATED
- production D1: NOT CREATED
- production domain: UNVERIFIED
- production deploy: FORBIDDEN until staging acceptance and safety gates pass
- current staging code policy: SYNTHETIC DATA ONLY because auth is not yet production-grade

## Repository blocker
A dedicated PARI repository does not yet exist in the connected GitHub account as of the latest check on 2026-08-24. The current GitHub connector can write to existing repositories but does not expose repository creation. Do not place PARI source inside VinoVeritas, Splendoria or 247Agent repositories. Create a dedicated private repository (recommended exact name: `PARI`) and then import the validated v0.2 scaffold there.

## Commercial validation target
Before adding complex AI matching, prove one city / cluster can sustain repeated real-world meetings with:
- 40–60 verified pilot members,
- 4 trained Hosts,
- 3 suitable venues,
- recurring Friday/Saturday inventory,
- low no-show rate,
- meaningful second meetings,
- willingness to pay for access/events/membership.

## North-star pilot metric
`Meaningful Meetings`: real meetings followed by a mutually positive desire to reconnect for BUSINESS, LOVE or BOTH.

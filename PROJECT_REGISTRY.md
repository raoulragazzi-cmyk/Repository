# PROJECT REGISTRY — AI Arena Control Room

Registro centrale dei fingerprint tecnici. Non contiene secret o dati cliente.

## VINOVERITAS

**Status:** BOOTSTRAP / LIVE PRODUCTION EXISTS — source capture still incomplete.

- Repository: `raoulragazzi-cmyk/VinoVeritas`
- Repository visibility: public (production source import blocked until privacy decision)
- Current default branch: `splendoria.vip` (historical anomaly)
- Prepared branch: `main`
- Governance branch: `governance/bootstrap`
- Production API Worker: `vinoveritas-api`
- Frontend/asset Worker: `vinoveritasstudioweb`
- Production API domain: `api.vinoveritas.studio`
- Studio domain: `studio.vinoveritas.studio`
- Production D1: `vinoveritas-db`
- Production D1 ID: `144b8f51-40d4-4dee-b0b7-665476439f71`
- Historical R2 name: `vinoveritas-media`
- Last observed live R2 inventory name: `vinoveritas-clienti`
- R2 status: **UNVERIFIED LIVE — discrepancy must be resolved before deploy involving media**
- Health endpoint: `/health` historically documented; live re-verification required
- Protected area: regulatory e-label; compliance and marketing must remain separate
- Known auth incident 2026-08-19: PBKDF2 310000 iterations unsupported by runtime; hotfix restored 100000-iteration compatibility. Must become regression test after live source capture.
- Deployment rule: no production deploy from GitHub until exact live source/bindings are captured and compared.

## SPLENDORIA

**Status:** MANAGED BOOTSTRAP → staging configuration validated in CI; production unchanged.

- Repository: `raoulragazzi-cmyk/splendoria.vip`
- Repository visibility: public; privacy hardening tracked
- Current default branch: `splendoria.vip`
- Prepared `main`: exists, initially copied from production baseline
- Governance branch: `governance/software-house-setup`
- Production Worker: `splendoria-v2`
- Production domain: `https://www.splendoria.vip`
- Production D1: `splendoria-db`
- Production D1 ID: `1a46b8b0-2e6f-44cf-a22f-4950259f9434`
- Staging D1: `splendoria-v2-test`
- Staging D1 ID: `8bf872f6-3f9e-471f-95bc-a99a94f0d97c`
- Intended staging Worker: `splendoria-v2-staging`
- Health endpoint: `/healthz`
- Protected areas: auth/session, user/book ownership, Muse state, destructive actions, D1 migrations, email flows, PDF output
- Deployment rule: staging acceptance before production; D1 backup before risky migrations.

## 247AGENT / COPILOT HOTEL

**Status:** MANAGED BOOTSTRAP — CI/hardening active; staging resources not yet provisioned.

- Repository: `raoulragazzi-cmyk/247agent-copilot`
- Repository visibility: private
- Intended production branch: `main`
- Current repository default branch metadata: `splendoria.vip` (historical anomaly; normalize only after Cloudflare references verified)
- Governance branch: `governance/software-house-setup`
- Production Worker: `247agent-copilot`
- Production D1: `247agent-copilot-prod`
- Production D1 ID: `c98e405a-e44f-44f7-b0b8-387eff23c112`
- Staging Worker: `247agent-copilot-staging` planned
- Staging D1: not yet provisioned
- Staging AI Search: not yet provisioned
- Health/diagnostic endpoint: `/api/copilot/llm-health`
- Protected areas: tenant isolation, KPI semantics/calculation, hotel operational data, connector/source provenance, billing/economic data
- Deployment rule: no staging deploy until D1 + AI Search + tenant identity are explicitly separate from production.

## PARI — VERIFIED ENTREPRENEURS COMMUNITY

**Status:** MANAGED BOOTSTRAP — private repository active; v0.4 on `main`; M2 trust/security work in draft PR; production forbidden.

- Product thesis: local-first verified community for entrepreneurs / self-employed professionals; user-created PARI Tables, recurring city network, explicit intentions `LOVE / BUSINESS / OPEN / SOCIAL`, private reciprocal post-event matching.
- Prototype source: `PARI - app standalone.html` supplied in ChatGPT on 2026-08-24; prototype is design/product reference only, not production source of truth.
- Repository: `raoulragazzi-cmyk/pari`
- Repository visibility: `PRIVATE` — verified 2026-08-24
- Default/source-of-truth branch: `main` — normalized and verified 2026-08-24
- Staging branch: `staging`
- Governance branch: `governance/software-house-setup`
- Active trust/security branch: `feature/m2-trust-auth`
- Active draft PR: `#4 M2: Trust, Auth & Verification foundation`
- Imported baseline: v0.4 governance-ready
- GitHub CI: active; validates JS, migrations, synthetic seed, M2 entrypoint and secret-file exclusions
- Intended staging Worker: `pari-staging`
- Intended staging D1: `pari-staging-db`
- Production Worker: `NOT CREATED`
- Production D1: `NOT CREATED`
- Production domain: `UNVERIFIED`
- Health endpoint: `/api/health`
- D1 entities now cover marketplace, trust and security: members, availability, tables, table_requests, post_event_intents, matches, consent_records, member_blocks, reports, reliability_events, host_profiles, venues, invitations, product_events, auth_login_challenges, auth_sessions, verification_cases, member_privacy, data_subject_requests, moderation_actions, security_rate_limits, security_events.
- M2 security source includes passwordless auth/session, server-side actor enforcement, same-origin mutation gate, Turnstile Siteverify integration, rate-limit abstraction, security audit events and login/report/invitation throttling hooks.
- North Star Metric: `Meaningful Meetings` — completed real-world meetings that generate positive follow-up / reciprocal connection; swipes are not a primary KPI.
- Protected areas: identity and entrepreneur verification, dating preferences, relationship/sexual-orientation data, exact location, post-event intent, blocking/reporting, host moderation, no-show/reliability logic, membership/billing, deletion/export/consent.
- Data rule: staging remains synthetic-only until real auth/session, 18+ auditable consent, privacy controls, moderation, delete/export and verification gates pass.
- Product rule: hosts create experiences; PARI governs trust/access. No public star rating of people. No forced referrals. No forced romance.
- Launch rule: city density before expansion; do not publicly activate a city without sufficient verified members, trained hosts, upcoming viable tables and reciprocal compatibility.
- Deployment rule: staging only until privacy/safety review, deletion/export flows, moderation, real founding-member consent and a successful real-world pilot are completed.

## SOMMELIER ACADEMY

**Status:** BOOTSTRAP v0.0.7 GREEN + CLOUDFLARE WORKER/R2 EU-ONLY LIVE FAIL-CLOSED — PostgreSQL/Hyperdrive qualification, Vectorize/AI Gateway and dedicated private GitHub repository still pending.

- Canonical project name: `SOMMELIER ACADEMY`
- Intended repository: `raoulragazzi-cmyk/sommelier-academy`
- Intended repository visibility: `PRIVATE`
- Dedicated repository status: `NOT CREATED` — connector lacks create-repository; browser unauthenticated; GitHub Actions native token returned HTTP 403 `Resource not accessible by integration`
- Remote canonical Git SHA: `NOT YET ESTABLISHED`
- Canonical Master Project: ChatGPT Library `/Projects/SOMMELIER_ACADEMY/SOMMELIER_ACADEMY_MASTER_PROJECT.md` — v0.11
- Canonical implementation bootstrap: ChatGPT Library `/Projects/SOMMELIER_ACADEMY/implementation/sommelier-academy-bootstrap-v0.0.7.zip`
- Local verification: `66/66 tests PASS`; 30 JS modules checked; 7 immutable SHA-256-pinned migrations; 38/38 schema tables semantic isolation PASS
- PostgreSQL runtime policy: `academy_runtime`, least privilege on 10 first-slice tables + 2 app functions; LOGIN + NOINHERIT; no SUPERUSER/BYPASSRLS/CREATEDB/CREATEROLE/REPLICATION
- Database credential rule: `STAGING_MIGRATION_DATABASE_URL` and `STAGING_RUNTIME_DATABASE_URL` are separate; TLS required; Hyperdrive may use the runtime URL only
- Managed-provider rule: if the provider pre-creates `academy_runtime`, bootstrap verifies attributes + real login without requiring migration `CREATEROLE`; privilege escalation is forbidden as a convenience workaround
- Runtime transaction rule: transaction-local search path + statement timeout + idle-in-transaction timeout + tenant/principal context; no external AI/network work while DB transaction is open
- Migration execution baseline: advisory lock + migration ledger + hash verification + runtime grant bootstrap prepared
- Tenant-isolation baseline: synthetic tenant A/B fixture + reused PostgreSQL runtime-client probe prepared; Hyperdrive HYP-T01–HYP-T08 plan prepared
- Architecture: Cloudflare Workers + PostgreSQL via Hyperdrive + R2 + Vectorize + Durable Objects only for coordinated/live state + AI Gateway
- System of record: PostgreSQL; Vectorize is derived/non-authoritative
- Staging Worker: `sommelier-academy-api-staging` — LIVE
- Staging runtime: `https://sommelier-academy-api-staging.raoulragazzi.workers.dev`
- Current Worker Version ID: `bdfbaac9-768d-46cb-93e0-8e96674e287f`
- Bootstrap runtime version: `0.0.7`
- Runtime checks: `/livez` PASS; `/healthz` PASS with `ready:false`; `/readyz` EXPECTED 503 fail-closed; `/version` PASS; `/r2-check` PASS with expected jurisdiction EU
- Staging R2: `sommelier-academy-staging-objects` — LIVE EU-only, location `EEUR`, binding `jurisdiction=eu`
- R2 residency incident 2026-09-23: RESOLVED, NO DATA IMPACT — empty default/ENAM duplicate created by earlier bootstrap was identified, exact-matched and deleted after EU rebind; default now 404, EU preserved
- R2 provisioning guardrail: audit `default/eu/us` before create; same-name off-target jurisdiction causes `R2_JURISDICTION_COLLISION` fail-closed
- PostgreSQL staging: `NOT PROVISIONED`
- Hyperdrive staging: `NOT PROVISIONED`
- Vectorize target: `sommelier-academy-staging-knowledge` — `NOT PROVISIONED`
- AI Gateway target: `sommelier-academy-staging` — `NOT PROVISIONED`
- Existing Cloudflare operational token capability: Workers deploy + R2 read/write PASS; Vectorize/Hyperdrive/AI Gateway API access 403; do not treat it as the final Academy full-stack credential
- Cloudflare Academy token target: Workers product Admin only for initial creation if needed, then Editor; R2 Write, Vectorize Write, Hyperdrive Write, AI Gateway Read/Edit, Workers AI Read; no DNS/route permissions initially
- Protected areas: tenant isolation, membership/capabilities/entitlements, assessment-secure content, examiner decisions, credential issuing, source provenance, learner sensory evidence, audit trail
- Certification rule: Tutor mastery can never issue professional credentials; certification requires controlled assessment evidence and human authority
- IP rule: third-party training material may be used only as restricted internal reference where lawful; learner-facing content must be original or explicitly licensed
- Deployment rule: no production deploy. Full staging remains unqualified until PostgreSQL, migrations, runtime grants, Hyperdrive pooled tenant isolation, Vectorize, AI Gateway, identity, backup/restore, AI eval, accessibility and rollback are green
- Repository rule: do not place SOMMELIER ACADEMY application code inside VinoVeritas, 247agent-copilot, Splendoria, PARI or this public Control Room repository

---

## New project rule

A new project cannot enter normal managed production until its fingerprint section exists here and is confirmed against the live infrastructure. Unknown values must be written as `UNVERIFIED`, never guessed.

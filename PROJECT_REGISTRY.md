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

---

## New project rule

A new project cannot enter normal managed production until its fingerprint section exists here and is confirmed against the live infrastructure. Unknown values must be written as `UNVERIFIED`, never guessed.

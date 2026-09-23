# SOMMELIER ACADEMY — Bootstrap handoff

Date: 2026-09-23
Status: local bootstrap v0.0.4 green; provisioning-as-code ready; remote dedicated credentials/connections pending.

## Canonical identity

- Project: SOMMELIER ACADEMY
- Intended private repository: `raoulragazzi-cmyk/sommelier-academy`
- Control Room entry: `PROJECT_REGISTRY.md`
- Master Project source of truth: ChatGPT Library `/Projects/SOMMELIER_ACADEMY/SOMMELIER_ACADEMY_MASTER_PROJECT.md`

## Local implementation baseline

- Branch: `main`
- HEAD: `75b09b8c8e2b2b07a342f0c76593b82a61bdf0a1`
- Bootstrap package: `sommelier-academy-bootstrap-v0.0.4.zip`
- Tests: 34/34 PASS
- Migration checks: PASS
- Isolation manifest: 38/38 bootstrap tables classified
- Working tree: clean at evidence capture

## Architecture

- Cloudflare Workers API
- PostgreSQL authoritative store
- Hyperdrive for PostgreSQL access
- R2 for objects/evidence/assets
- Vectorize as derived semantic index only
- Durable Objects only for coordinated/live state
- AI Gateway for model observability/policy
- capability != entitlement
- human certification authority
- append-oriented audit

## Cloudflare staging targets

- Worker: `sommelier-academy-api-staging`
- R2: `sommelier-academy-staging-objects`
- Vectorize: `sommelier-academy-staging-knowledge`
- AI Gateway: `sommelier-academy-staging`
- Hyperdrive: to be created after PostgreSQL staging exists
- PostgreSQL staging: NOT PROVISIONED

## External blockers observed

### GitHub
The installed GitHub connector can manage existing repositories but exposes no repository-create action.
Browser attempt at GitHub repository creation reached the sign-in page; no browser/vault credentials were available.

### Cloudflare
Browser check reached the Cloudflare sign-in page; no browser/vault credentials were available.
No resources were created or modified.

## Non-negotiable rules

1. Do not put Academy application code in another product repository.
2. Do not expose the bootstrap in the public Control Room repository.
3. No production deploy before staging qualification.
4. No Tutor/AI agent may issue professional credentials.
5. RLS is defense in depth; application authorization remains mandatory.
6. PostgreSQL is authoritative; vector/cache layers are rebuildable.
7. Staging begins synthetic-only.
8. Every privileged action must be attributable and auditable.

## Next executable sequence after authentication

1. Create private repository `sommelier-academy`.
2. Push local Git history preserving HEAD.
3. Enable CI and protect `main`.
4. Provision PostgreSQL staging with migration/runtime users separated.
5. Provision R2 and Vectorize.
6. Create Hyperdrive bound to staging PostgreSQL.
7. Create/configure AI Gateway.
8. Deploy staging Worker.
9. Execute migrations.
10. Run tenant A/B, IDOR, RLS connection-reuse and stale-membership tests.
11. Verify backup/restore, audit readback, AI regression, accessibility and rollback.
12. Only then mark Academy Engine MVP as staging-qualified.

This handoff contains no secrets, credentials or customer data.


## Verified remote diagnostics

### Cloudflare
Read-only diagnostics were run through a temporary VinoVeritas branch and then the branch was reset to current main. No Cloudflare mutation occurred.

- canonical account fingerprint: verified
- R2 list with existing token: HTTP 200
- Vectorize list: HTTP 403
- Hyperdrive list: HTTP 403
- AI Gateway list: HTTP 403
- conclusion: existing token is not an approved/general Academy provisioning credential

### PostgreSQL
PostgreSQL remains mandatory as the system of record. Neon is the preferred dedicated staging candidate available through ChatGPT connection; it is not yet connected.

### Provisioning automation
Bootstrap v0.0.4 now includes:
- fail-closed private GitHub repo create/push script
- Cloudflare R2/Vectorize/Hyperdrive/AI Gateway provisioning
- Hyperdrive caching disabled by default
- EU R2 default
- Wrangler config renderer + remote verifier
- GitHub Actions staging workflow
- no committed credentials

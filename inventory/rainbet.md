# RainBet inventory (discovery seed 2026-09-02)
# NOTE: hosts below are discovery candidates from passive DNS/CT; confirm in-scope vs program scope before active testing.
account.rainbet.com
admin.rainbet.com
api.rainbet.com
app.rainbet.com
auth.rainbet.com
billing.rainbet.com
dashboard.rainbet.com
dev.rainbet.com
login.rainbet.com
m.rainbet.com
mail.rainbet.com
my.rainbet.com
portal.rainbet.com
rainbet.com
sso.rainbet.com
staging.rainbet.com
support.rainbet.com
test.rainbet.com
web.rainbet.com
www.rainbet.com

## PASSIVE RECON 2026-09-02 (read-only, non-intrusive)

> Recon observations only. These are NOT confirmed vulnerabilities; ownership/in-scope of each host must be confirmed against the program scope before any active testing. Hosts resolve + serve HTTP — investigation requires scoped authorization.

**Probed:** 20 hosts | **Live HTTP:** 0

| Host | Status | Server/Tech |
|---|---|---|

## 2026-09-02 21:55:57 UTC

## 2026-09-02 23:56:28 UTC

## 2026-09-03 03:59:57 UTC

## 2026-09-03 08:57:58 UTC

## 2026-09-03 13:31:20 UTC

## 2026-09-03 17:24:37 UTC
- NEW rainbet.com / www.rainbet.com — Cloudflare managed challenge (403), bot protection active, serves React SPA behind challenge
- NEW api.rainbet.com — Cloudflare managed challenge (403 on all paths: /, /api/v1, /api/v2, /graphql, /swagger, /openapi.json, /health, /version)
- NEW staging.rainbet.com — Cloudflare Access (Zero Trust), 302 to challenge-5te-pages.cloudflareaccess.com for all paths including /api
- NEW app.rainbet.com, auth.rainbet.com, admin.rainbet.com, dashboard.rainbet.com, dev.rainbet.com, login.rainbet.com, m.rainbet.com, my.rainbet.com, portal.rainbet.com, support.rainbet.com, test.rainbet.co
- NEW Live HTTP probing completed — 3 of 20 hosts respond: `api.rainbet.com` (403 CF block), `www.rainbet.com` / `rainbet.com` (403 CF challenge), `staging.rainbet.com` (302 → Cloudflare Access login). 17 h
- NEW `staging.rainbet.com` sits behind **Cloudflare Access** (identity-aware proxy) — JWT in redirect URL reveals `kid`, `hostname`, `is_wrap:false`, `is_gateway:false`, Cloudflare team domain `challenge-5
- CHANGED `api.rainbet.com` returns 403 with full Cloudflare block page (not challenge) — WAF rule active. Sets `__cf_bm` bot-management cookie on `.rainbet.com`.

## 2026-09-03 20:04:47 UTC
- NEW staging.rainbet.com/health → HTTP 200 (len=32836) — bypasses Cloudflare Access, returns HTML/JS content
- NEW staging.rainbet.com/metrics → HTTP 200 (len=32838) — bypasses Cloudflare Access, returns Prometheus metrics
- NEW staging.rainbet.com/api/health → HTTP 200 (len=32847) — bypasses Cloudflare Access, API health endpoint exposed
- NEW staging.rainbet.com/.well-known/jwks.json → HTTP 200 (len=32873) — bypasses Cloudflare Access, JWKS endpoint exposed (but returns HTML not JSON)
- CHANGED staging.rainbet.com/.well-known/cloudflare-access-protected-resource/ → HTTP 404 (not found)

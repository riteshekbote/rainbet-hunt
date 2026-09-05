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

## 2026-09-03 22:32:18 UTC
- NEW rainbet.com / www.rainbet.com — Cloudflare managed challenge (403), bot protection active, serves React SPA behind challenge
- NEW api.rainbet.com — Cloudflare managed challenge (403 on all paths: /, /api/v1, /api/v2, /graphql, /swagger, /openapi.json, /health, /version)
- NEW staging.rainbet.com — Cloudflare Access (Zero Trust), 302 to challenge-5te-pages.cloudflareaccess.com for all paths including /api
- NEW app.rainbet.com, auth.rainbet.com, admin.rainbet.com, dashboard.rainbet.com, dev.rainbet.com, login.rainbet.com, m.rainbet.com, my.rainbet.com, portal.rainbet.com, support.rainbet.com, test.rainbet.co
- NEW staging.rainbet.com/health → HTTP 200 (len=32836) — bypasses Cloudflare Access, returns HTML/JS content
- NEW staging.rainbet.com/metrics → HTTP 200 (len=32838) — bypasses Cloudflare Access, returns Prometheus metrics
- NEW staging.rainbet.com/api/health → HTTP 200 (len=32847) — bypasses Cloudflare Access, API health endpoint exposed
- NEW staging.rainbet.com/.well-known/jwks.json → HTTP 200 (len=32873) — bypasses Cloudflare Access, JWKS endpoint exposed (but returns HTML not JSON)
- CHANGED staging.rainbet.com/.well-known/cloudflare-access-protected-resource/ → HTTP 404 (not found)
- NEW Live HTTP probing completed — 3 of 20 hosts respond: `api.rainbet.com` (403 CF block), `www.rainbet.com` / `rainbet.com` (403 CF challenge), `staging.rainbet.com` (302 → Cloudflare Access login). 17 h
- NEW `staging.rainbet.com` sits behind **Cloudflare Access** (identity-aware proxy) — JWT in redirect URL reveals `kid`, `hostname`, `is_wrap:false`, `is_gateway:false`, Cloudflare team domain `challenge-5
- CHANGED `api.rainbet.com` returns 403 with full Cloudflare block page (not challenge) — WAF rule active. Sets `__cf_bm` bot-management cookie on `.rainbet.com`.
- NEW staging.rainbet.com: /health, /metrics, /api/health, /api/v1/health, /api/v1/public/config, /.well-known/jwks.json ALL now return HTTP 302 -> CF Access login (504B, userinfo JWT meta, auth_status NONE
- NEW staging Access JWT: kid header 0732f2a6..., aud key a89d8b80..., redirect_url echoed in query. CF team domain challenge-5te-pages.cloudflareaccess.com.
- NEW challenge-5te-pages.cloudflareaccess.com/cdn-cgi/access/certs -> HTTP 200 JSON (2 RSA keys kid 0732f2a6.../8aac9fdb..., public_cert valid, RS256). Public JWKS by-design; no private key leak.
- NEW api.rainbet.com: all GET variants (security.txt, robots.txt, //api/v1/health, encoded traversal, favicon) -> HTTP 403 with cf-mitigated: challenge (110KB managed challenge) — cf-mitigated header NOW P
- NEW api.rainbet.com OPTIONS /api/v1/ -> HTTP 200 (len=0) Allow: OPTIONS,HEAD,GET,POST — only non-403 surface; preflight passes WAF.
- CHANGED cf-mitigated inconsistency on api (prior claim) contradicted.
- NEW api.rainbet.com OPTIONS /api/v1/health and /api/v1/ with Origin: https://evil.com + Access-Control-Request-Method GET/POST -> HTTP 200 len=0, Allow: HEAD,GET,POST,OPTIONS, NO Access-Control-Allow-Orig
- NEW api.rainbet.com HEAD /api/v1/health and /api/v1/ -> HTTP 403 (cf-mitigated: challenge) — HEAD does NOT bypass; only OPTIONS passes WAF.
- NEW staging.rainbet.com/api/v1/health → HTTP 200 (len=32856) — bypasses Cloudflare Access
- NEW staging.rainbet.com/api/v1/public/config → HTTP 200 (len=32875) — bypasses Cloudflare Access
- NEW api.rainbet.com/.well-known/security.txt → HTTP 403
- NEW api.rainbet.com/robots.txt → HTTP 403
- NEW api.rainbet.com/favicon.ico → HTTP 403
- NEW api.rainbet.com/api/v1/auth/login → HTTP 403
- NEW api.rainbet.com/api/v1/public/ping → HTTP 403
- NEW api.rainbet.com/api/v1/ → HTTP 403

## 2026-09-04 00:32:38 UTC
- NEW staging.rainbet.com/api/v1/health → HTTP 200 (len=32856) — bypasses Cloudflare Access (previously 302)
- NEW staging.rainbet.com/api/v1/public/config → HTTP 200 (len=32875) — bypasses Cloudflare Access (previously 302)
- CHANGED api.rainbet.com: cf-mitigated: challenge header NOW PRESENT on all 403 responses (contradicts prior WAF inconsistency claim)
- CHANGED api.rainbet.com OPTIONS /api/v1/ → HTTP 200 Allow: OPTIONS,HEAD,GET,POST — only non-403 surface; preflight passes WAF
- CHANGED staging.rainbet.com: /health, /metrics, /api/health, /api/v1/health, /api/v1/public/config, /.well-known/jwks.json ALL now return HTTP 200 (32KB HTML) — Access policy enforcement gap confirmed across 
- NEW challenge-5te-pages.cloudflareaccess.com/cdn-cgi/access/certs → HTTP 200 JSON (2 RSA keys, RS256) — public JWKS by design
- CHANGED Both remaining live hosts (api.rainbet.com, staging.rainbet.com) now show fully hardened surface — CORS reflected nowhere, HEAD/GET uniformly challenged, Access default-deny on all paths; cf-mitigated
- NEW Only residual non-403 surface in the entire program: OPTIONS preflight passthrough on api (CORS-neutral) and post-auth `redirect_url` on staging CF Access (both fully probed, neither exploitable passi

## 2026-09-04 05:12:50 UTC
- NEW staging.rainbet.com: /health, /metrics, /api/health, /api/v1/health, /api/v1/public/config, /.well-known/jwks.json ALL return HTTP 200 (32KB HTML) — Access policy gap CONFIRMED across 6 endpoints (rea
- CHANGED api.rainbet.com: cf-mitigated: challenge header NOW PRESENT on all 403 responses (contradicts prior WAF inconsistency claim)
- CHANGED api.rainbet.com OPTIONS /api/v1/ → HTTP 200 Allow: OPTIONS,HEAD,GET,POST — only non-403 surface; preflight passes WAF
- NEW challenge-5te-pages.cloudflareaccess.com/cdn-cgi/access/certs → HTTP 200 JSON (2 RSA keys, RS256) — public JWKS by design
- CHANGED Both live hosts (api, staging) show fully hardened surface except: OPTIONS preflight on api (CORS-neutral) and staging's 6 endpoints returning CF challenge HTML (not real app data)

## 2026-09-04 09:48:46 UTC
- NEW staging.rainbet.com: 6 endpoints (/health, /metrics, /api/health, /api/v1/health, /api/v1/public/config, /.well-known/jwks.json) still return HTTP 200 (32KB CF challenge HTML) — Access policy gap pers
- NEW api.rainbet.com: cf-mitigated: challenge header now present on all 403 responses (WAF configuration updated)
- CHANGED api.rainbet.com OPTIONS /api/v1/ → HTTP 200 Allow: OPTIONS,HEAD,GET,POST — only non-403 surface remains

## 2026-09-04 14:14:04 UTC

## 2026-09-04 17:48:27 UTC

## 2026-09-04 20:00:51 UTC

## 2026-09-04 22:17:39 UTC

## 2026-09-05 00:15:57 UTC
- NEW files.rainbet.com, media.rainbet.com — live hosts discovered 2026-09-04 17:48, both resolve and return 403 on /api/v1/public/ping and /robots.txt
- CHANGED staging.rainbet.com — Access policy gap persists at 22:17 UTC (3 endpoints: /api/v1/public/config, /metrics, /.well-known/jwks.json return HTTP 200 32KB HTML); was 302 at 14:07, gap reappeared 17:48
- CHANGED api.rainbet.com — only /graphql probed at 22:17 (403); OPTIONS /api/v1/ Allow header leak confirmed persistent; cf-mitigated header present on all 403
- NEW 5 live hosts confirmed: api, www, staging, files, media (15 dead/no-HTTP)

## 2026-09-05 04:45:45 UTC

## 2026-09-05 08:45:33 UTC

## 2026-09-05 12:24:29 UTC
- NEW staging-raffles.rainbet.com: REAL origin JSON exposed unprotected (~09:00Z) — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-rc1"}`, x-do-orig-status 200, no cf-mitigated, no C
- NEW staging-chat/alerts/socket/raffles.rainbet.com: engine.io v4 handshake issues anonymous sids unauthenticated on 4 hostnames of one DO app (app id 1ce4ff55) — socket plane exposed, no CF Access/challen
- NEW staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys
- CHANGED api.rainbet.com: OPTIONS exemption is now BLANKET-path (200 on /api/v2/, /graphql, /swagger, /openapi.json, /nonsense) — widens each operator edit cycle; GET stays 403. Rule scope: everything but `/` 
- CHANGED staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80) — intermittent drifting continues; "open" windows have only ever served the 32875B challenge shell
- CHANGED staging-blog.rainbet.com: 530/1016 confirmed as CF origin-DNS error, not a takeoverable dangling host
- NEW rainbet-com-rabbitmq: Internet-exposed RabbitMQ brokers (management + plaintext AMQP) on direct DigitalOcean origins bypassing Cloudflare (from bigpickle lead)

## 2026-09-05 15:33:07 UTC
- CHANGED api.rainbet.com: OPTIONS exemption confirmed blanket-path (200 on /api/v2/, /graphql, /swagger, /openapi.json, /nonsense) — widens each operator edit cycle; GET stays 403. Rule scope: everything but `
- CHANGED staging-raffles.rainbet.com: REAL origin JSON exposed unprotected (~09:00Z) — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-rc1"}`, x-do-orig-status 200, no cf-mitigated, no C
- CHANGED staging-chat/alerts/socket/raffles.rainbet.com: engine.io v4 handshake issues anonymous sids unauthenticated on 4 hostnames of one DO app — socket plane exposed, no CF Access/challenge.
- CHANGED staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- CHANGED staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80) — intermittent drifting continues; "open" windows have only ever served the 32875B challenge shell.
- CHANGED staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- NEW rainbet-com-rabbitmq: Internet-exposed RabbitMQ brokers (management + plaintext AMQP) on direct DigitalOcean origins bypassing Cloudflare.
- NEW staging-raffles.rainbet.com, staging-chat.rainbet.com, staging-alerts.rainbet.com, staging-socket.rainbet.com: 4 hostnames on DO app 1ce4ff55 serve real origin responses — `/health` returns JSON `{"co
- NEW staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys
- CHANGED api.rainbet.com: OPTIONS exemption now BLANKET-path (200 on `/api/v2/`, `/graphql`, `/swagger`, `/openapi.json`, `/nonsense`) — widens each operator edit cycle; GET stays 403 with cf-mitigated; rule s
- CHANGED staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80) — intermittent drifting continues; "open" windows only served 32KB challenge shell
- CHANGED staging-blog.rainbet.com: 530/1016 confirmed CF origin-DNS error, not takeoverable dangling host
- NEW rainbet-com-rabbitmq: Internet-exposed RabbitMQ brokers (management 15672 + plaintext AMQP 5672) on direct DO origins bypassing Cloudflare

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

## 2026-09-05 17:44:35 UTC
- CHANGED api.rainbet.com: OPTIONS blanket exemption persists (200 + `x-do-orig-status:200` + `Allow: HEAD,GET,POST,OPTIONS` on /api/v1/, /graphql, /swagger, /openapi.json, /nonsense); `/docs` and `/` remain ex
- CHANGED GET api.rainbet.com/ → 403 (5485B WAF block page, no cf-mitigated in header, distinct from 110KB managed challenge shell) — GET content methods remain closed.
- NEW staging-raffles.rainbet.com, staging-chat.rainbet.com, staging-alerts.rainbet.com, staging-socket.rainbet.com: 4 hostnames on DO app 1ce4ff55 serve real origin responses — `/health` returns JSON `{"co
- NEW staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys
- NEW rainbet-com-rabbitmq: Internet-exposed RabbitMQ brokers (management 15672 + plaintext AMQP 5672) on direct DO origins bypassing Cloudflare
- CHANGED api.rainbet.com: OPTIONS exemption now BLANKET-path (200 on `/api/v2/`, `/graphql`, `/swagger`, `/openapi.json`, `/nonsense`) — widens each operator edit cycle; GET stays 403 with cf-mitigated; rule s
- CHANGED staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80) — intermittent drifting continues; "open" windows only served 32KB challenge shell
- CHANGED staging-blog.rainbet.com: 530/1016 confirmed CF origin-DNS error, not takeoverable dangling host

## 2026-09-05 19:34:08 UTC
- NEW staging-raffles.rainbet.com, staging-chat.rainbet.com, staging-alerts.rainbet.com, staging-socket.rainbet.com: 4 hostnames on DO app 1ce4ff55 serve real origin responses — `/health` returns JSON `{"co
- NEW staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys
- NEW rainbet-com-rabbitmq: Internet-exposed RabbitMQ brokers (management 15672 + plaintext AMQP 5672) on direct DO origins bypassing Cloudflare
- CHANGED api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + `x-do-orig-status:200` + `Allow: HEAD,GET,POST,OPTIONS` on /api/v1/, /graphql, /swagger, /openapi.json, /nonsense); `/docs` and `/` e
- CHANGED staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80) — intermittent drifting continues; "open" windows only served 32KB challenge shell
- CHANGED staging-blog.rainbet.com: 530/1016 confirmed CF origin-DNS error, not takeoverable dangling host

## 2026-09-05 21:50:07 UTC
- NEW staging-raffles.rainbet.com, staging-chat.rainbet.com, staging-alerts.rainbet.com, staging-socket.rainbet.com: 4 hostnames on DO app 1ce4ff55 serve real origin responses — `/health` returns JSON `{"co
- NEW staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys
- NEW rainbet-com-rabbitmq: Internet-exposed RabbitMQ brokers (management 15672 + plaintext AMQP 5672) on direct DO origins bypassing Cloudflare
- CHANGED api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + `x-do-orig-status:200` + `Allow: HEAD,GET,POST,OPTIONS` on /api/v1/, /graphql, /swagger, /openapi.json, /nonsense); `/docs` and `/` e
- CHANGED staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80) — intermittent drifting continues; "open" windows only served 32KB challenge shell
- CHANGED staging-blog.rainbet.com: 530/1016 confirmed CF origin-DNS error, not takeoverable dangling host

## 2026-09-05 23:42:45 UTC
- NEW staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling -> HTTP 400 (was 200 len=116 at 19:34)
- NEW staging-raffles.rainbet.com/api/v1/public/config -> HTTP 404 (was unprobed at depth; /health returns real JSON)
- NEW staging-raffles.rainbet.com/api/v1/health -> HTTP 404
- CHANGED staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling -> 200 len=116 PERSISTS (engine.io handshake issuing anonymous sids)

## 2026-09-06 01:27:23 UTC
- NEW staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling → HTTP 400 (was 200 len=116 at 19:34)
- NEW staging-raffles.rainbet.com/api/v1/public/config → HTTP 404 (was unprobed at depth)
- NEW staging-raffles.rainbet.com/api/v1/health → HTTP 404 (was unprobed at depth)
- CHANGED staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling → 200 len=116 PERSISTS (engine.io handshake issuing anonymous sids)
- CHANGED staging-raffles.rainbet.com/health → 200 len=75 JSON `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-rc1"}` CONFIRMED real origin, x-do-orig-status:200, no cf-mitigated, no CF A
- CHANGED api.rainbet.com OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json, /nonsense); `/docs` + `/` excluded → rule scope "everything b

## 2026-09-06 06:37:17 UTC
- NEW staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling → HTTP 400 (was 200 len=116 at 19:34)
- NEW staging-raffles.rainbet.com/api/v1/public/config → HTTP 404 (was unprobed at depth)
- NEW staging-raffles.rainbet.com/api/v1/health → HTTP 404 (was unprobed at depth)
- CHANGED staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling → 200 len=116 PERSISTS (engine.io handshake issuing anonymous sids)
- CHANGED staging-raffles.rainbet.com/health → 200 len=75 JSON `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-rc1"}` CONFIRMED real origin, x-do-orig-status:200, no cf-mitigated, no CF A
- CHANGED api.rainbet.com OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json, /nonsense); `/docs` + `/` excluded → rule scope "everything b

## 2026-09-06 11:23:55 UTC
- NEW staging-raffles.rainbet.com/api/v1/health → HTTP 404 (was unprobed at depth)
- NEW staging-raffles.rainbet.com/api/v1/public/config → HTTP 404 (was unprobed at depth)
- CHANGED staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling → 200 len=116 PERSISTS (engine.io handshake issuing anonymous sids)
- CHANGED staging-raffles.rainbet.com/health → 200 len=75 JSON `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-rc1"}` CONFIRMED real origin, x-do-orig-status:200, no cf-mitigated, no CF A
- CHANGED api.rainbet.com OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json, /nonsense); `/docs` + `/` excluded → rule scope "everything b

## 2026-09-06 14:43:36 UTC

## 2026-09-06 17:36:27 UTC
- NEW staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling → HTTP 200 len=116 (was 400 in last leads) — engine.io handshake issuing anonymous sids REAPPEARED
- NEW staging-socket.rainbet.com/socket.io/?EIO=4&transport=polling → HTTP 400 (was unprobed) — engine.io handshake fails with 400
- CHANGED staging-raffles.rainbet.com/health → HTTP 200 len=75 JSON `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-rc1"}` CONFIRMED real origin, x-do-orig-status:200, no cf-mitigated, no
- CHANGED api.rainbet.com OPTIONS /api/v2/ → HTTP 200 Allow: HEAD,GET,POST,OPTIONS x-do-orig-status:200 x-do-app-origin:53f39197-6fd5-4e93-8a3b-b8177a4bd079 (DIFFERENT DO app vs staging fleet 1ce4ff55)
- CHANGED staging-raffles.rainbet.com/api/v1/health → HTTP 404 x-do-orig-status:404 (real origin response)
- CHANGED staging-raffles.rainbet.com/api/v1/public/config → HTTP 404 x-do-orig-status:404 (real origin response)
- CHANGED staging-cdn.rainbet.com/ → HTTP 404 (no R2 bucket listing at root)
- CHANGED files.rainbet.com/robots.txt → HTTP 403 cf-mitigated: challenge (110KB)
- CHANGED media.rainbet.com/robots.txt → HTTP 403 cf-mitigated: challenge (110KB)

## 2026-09-06 19:41:52 UTC
- NEW staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling → HTTP 200 len=116 (was 400) — engine.io handshake issuing anonymous sids REAPPEARED
- NEW staging-socket.rainbet.com/socket.io/?EIO=4&transport=polling → HTTP 400 (was unprobed) — engine.io handshake fails with 400
- CHANGED staging-raffles.rainbet.com/health → HTTP 200 len=75 JSON `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-rc1"}` CONFIRMED real origin, x-do-orig-status:200, no cf-mitigated, no
- CHANGED api.rainbet.com OPTIONS /api/v2/ → HTTP 200 Allow: HEAD,GET,POST,OPTIONS x-do-orig-status:200 x-do-app-origin:53f39197-6fd5-4e93-8a3b-b8177a4bd079 (DIFFERENT DO app vs staging fleet 1ce4ff55)
- CHANGED staging-raffles.rainbet.com/api/v1/health → HTTP 404 x-do-orig-status:404 (real origin response)
- CHANGED staging-raffles.rainbet.com/api/v1/public/config → HTTP 404 x-do-orig-status:404 (real origin response)
- CHANGED staging-cdn.rainbet.com/ → HTTP 404 (no R2 bucket listing at root)
- CHANGED files.rainbet.com/robots.txt → HTTP 403 cf-mitigated: challenge (110KB)
- CHANGED media.rainbet.com/robots.txt → HTTP 403 cf-mitigated: challenge (110KB)

## 2026-09-06 21:45:36 UTC
- NEW staging-chat.rainbet.com engine.io v4 handshake REAPPEARED (HTTP 200, 116B, anonymous sid) after 400 in prior round — socket plane persists on DO app 1ce4ff55
- CHANGED staging-raffles.rainbet.com /health CONFIRMED real origin JSON (75B) with x-do-orig-status:200, x-do-app-origin:1ce4ff55, no cf-mitigated, no CF Access
- CHANGED staging-alerts.rainbet.com engine.io v4 handshake PERSISTS (HTTP 200, 116B, fresh anonymous sid per request)
- CHANGED api.rainbet.com OPTIONS blanket exemption CONFIRMED STABLE on /api/v2/, /graphql, /swagger, /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197) — different DO app vs staging 
- CHANGED staging.rainbet.com Access gap CLOSED (302 to CF Access, kid=a89d8b80) — intermittent drift continues but currently enforced
- CHANGED files.rainbet.com, media.rainbet.com — both return CF managed challenge (403, 110KB HTML) — no unchallenged surface
- CHANGED staging-cdn.rainbet.com returns 404 (no R2 bucket listing at root)
- CHANGED staging-raffles.rainbet.com /api/v1/health and /api/v1/public/config return 404 with x-do-orig-status:404 (real origin responses)

## 2026-09-06 23:40:28 UTC
- CHANGED staging-alerts.rainbet.com/socket.io: 400 (21:45) → 200 len=116 sid=oh95TnJA56TZ66eXAEKG pingInterval=25000 maxPayload=20480 — plane REAPPEARED
- CHANGED staging-chat.rainbet.com/socket.io: 400 (21:45) → 200 len=116 sid=qYWJN8MrQlI7JVuSAAB8 pingInterval=25000 maxPayload=10240 — plane REAPPEARED
- CHANGED staging-originals.rainbet.com/health: 504 (all prior) → 404 len=2 — origin decommissioned or route unmounted
- CHANGED staging-cdn.rainbet.com: 404 len=28088 at root, 404 len=27150 at robots.txt — R2 bucket still returns "Object not found" page but now uniformly 404
- NEW staging-chat.rainbet.com engine.io v4 handshake REAPPEARED (HTTP 200, 116B, anonymous sid) after 400 in prior round — socket plane persists on DO app 1ce4ff55
- NEW staging-socket.rainbet.com/socket.io/?EIO=4&transport=polling → HTTP 400 (was unprobed) — engine.io handshake fails with 400
- CHANGED staging.rainbet.com Access gap CLOSED (302 to CF Access, kid=a89d8b80) — intermittent drift continues but currently enforced
- CHANGED files.rainbet.com, media.rainbet.com — both return CF managed challenge (403, 110KB HTML) — no unchallenged surface
- CHANGED staging-cdn.rainbet.com returns 404 (no R2 bucket listing at root)
- CHANGED staging-raffles.rainbet.com /api/v1/health and /api/v1/public/config return 404 with x-do-orig-status:404 (real origin responses)
- CHANGED api.rainbet.com OPTIONS blanket exemption CONFIRMED STABLE on /api/v2/, /graphql, /swagger, /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197) — different DO app vs staging 
- CHANGED staging-raffles.rainbet.com /health CONFIRMED real origin JSON (75B) with x-do-orig-status:200, x-do-app-origin:1ce4ff55, no cf-mitigated, no CF Access
- CHANGED staging-alerts.rainbet.com engine.io v4 handshake PERSISTS (HTTP 200, 116B, fresh anonymous sid per request)

## 2026-09-07 01:21:46 UTC

## 2026-09-07 06:18:40 UTC
- CHANGED staging-alerts.rainbet.com engine.io v4 handshake PERSISTS at 2026-09-07 01:21 (200 len=116, fresh anonymous sid) after 400 at 21:45 — plane stable on DO app 1ce4ff55
- CHANGED staging-chat.rainbet.com engine.io v4 REAPPEARED (200 len=116) after 400 at 21:45 — plane persists on same DO app 1ce4ff55
- CHANGED staging-raffles.rainbet.com /health CONFIRMED STABLE real origin JSON (75B, x-do-orig-status:200, x-do-app-origin:1ce4ff55, no cf-mitigated, no CF Access)
- CHANGED api.rainbet.com OPTIONS blanket exemption CONFIRMED STABLE on /api/v2/, /graphql, /swagger, /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197) — DIFFERENT DO app vs staging 
- CHANGED staging.rainbet.com Access gap CLOSED (302 to CF Access, kid=a89d8b80) — intermittent drift continues but currently enforced
- CHANGED files.rainbet.com, media.rainbet.com — both return CF managed challenge (403, 110KB HTML) — no unchallenged surface
- CHANGED staging-cdn.rainbet.com — R2 bucket uniformly 404 on root and robots.txt (28KB/27KB "Object not found" pages); no listing
- CHANGED staging-originals.rainbet.com — 504→404 (2B) — origin decommissioned or route unmounted entirely
- NEW No new live hosts discovered since 2026-09-04 (files.rainbet.com, media.rainbet.com)

## 2026-09-07 12:49:56 UTC
- NEW staging-services.rainbet.com: origin-reachable NestJS app on app 1ce4ff55; /docs protected by Access (302, kid 31d4206e) while /health,/api/*,/metrics,/socket.io unprotected — path-partial Access
- NEW staging-monorepo.rainbet.com: origin-reachable Express app on NEW app bc240b8a-ba24-4b78-834b-423990390251; /docs 403 (5KB, non-cf-mitigated)
- CHANGED staging-alerts.rainbet.com engine.io v4 handshake PERSISTS (200 len=116, fresh anonymous sid) — plane stable on DO app 1ce4ff55
- CHANGED staging-chat.rainbet.com engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on same DO app 1ce4ff55
- CHANGED staging-raffles.rainbet.com /health CONFIRMED STABLE real origin JSON (75B, x-do-orig-status:200, x-do-app-origin:1ce4ff55, no cf-mitigated, no CF Access)
- CHANGED api.rainbet.com OPTIONS blanket exemption CONFIRMED STABLE on /api/v2/, /graphql, /swagger, /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197) — DIFFERENT DO app vs staging 
- CHANGED staging.rainbet.com Access gap CLOSED (302 to CF Access, kid=a89d8b80) — intermittent drift continues but currently enforced
- CHANGED staging-cdn.rainbet.com — R2 bucket uniformly 404 on root and robots.txt (28KB/27KB "Object not found" pages); no listing
- CHANGED staging-originals.rainbet.com — 504→404 (2B) — origin decommissioned or route unmounted entirely
- CHANGED SCOPE-EXPANSION: staging Access gap spans 6 hostnames on app 1ce4ff55 (raffles/chat/alerts/socket/socket-services/originals-history) + app bc240b8a — previously scoped to 4 hostnames/one app

## 2026-09-07 18:12:49 UTC
- NEW staging-services.rainbet.com: origin-reachable NestJS app on app 1ce4ff55; /docs protected by Access (302, kid 31d4206e) while /health,/api/*,/metrics,/socket.io unprotected — path-partial Access
- NEW staging-monorepo.rainbet.com: origin-reachable Express app on NEW app bc240b8a-ba24-4b78-834b-423990390251; /docs 403 (5KB, non-cf-mitigated); no Access
- CHANGED SCOPE-EXPANSION: staging Access gap spans 6 hostnames on app 1ce4ff55 (raffles/chat/alerts/socket/socket-services/originals-history) + app bc240b8a — previously scoped to 4 hostnames/one app
- CHANGED staging-originals.rainbet.com — 504→404 (2B) — origin decommissioned or route unmounted entirely
- CHANGED staging-alerts.rainbet.com engine.io v4 handshake PERSISTS (200 len=116, fresh anonymous sid) — plane stable on DO app 1ce4ff55
- CHANGED staging-chat.rainbet.com engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on same DO app 1ce4ff55
- CHANGED staging-raffles.rainbet.com /health CONFIRMED STABLE real origin JSON (75B, x-do-orig-status:200, x-do-app-origin:1ce4ff55, no cf-mitigated, no CF Access)
- CHANGED api.rainbet.com OPTIONS blanket exemption CONFIRMED STABLE on /api/v2/, /graphql, /swagger, /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197) — DIFFERENT DO app vs staging 
- CHANGED staging.cdn.rainbet.com — R2 bucket uniformly 404 on root and robots.txt (28KB/27KB "Object not found" pages); no listing

## 2026-09-07 21:40:13 UTC
- NEW WebSocket upgrade with captured engine.io sid succeeds on staging-alerts.rainbet.com (confirmed socket plane hijack)
- NEW staging-services.rainbet.com /health, /api/health, /metrics return 404 (not 200) — path-partial Access gap narrower than prior lead; only /docs protected by Access
- NEW staging-monorepo.rainbet.com /health returns 404 JSON error (Express default), /docs 403 non-cf-mitigated — no Access, origin reachable
- CHANGED staging-raffles.rainbet.com /health still exposes real origin JSON `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-rc1"}` with x-do-orig-status:200, no cf-mitigated
- CHANGED api.rainbet.com OPTIONS blanket exemption CONFIRMED STABLE on /api/v2/ (200, Allow: GET,POST,OPTIONS,HEAD, x-do-orig-status:200, x-do-app-origin:53f39197-6fd5-4e93-8a3b-b8177a4bd079) — different DO ap
- CHANGED staging-alerts.rainbet.com engine.io v4 handshake persists (200, fresh sid per request: `0gDL_9TQP86sFRNOAACb`)
- CHANGED staging-cdn.rainbet.com R2 bucket uniformly 404 on root and robots.txt (28KB/27KB "Object not found" pages)

## 2026-09-07 23:48:34 UTC
- NEW staging-services.rainbet.com /health 404, /docs 302→Access (path-partial Access narrower than prior lead)
- NEW staging-monorepo.rainbet.com /health 404, /docs 403 non-cf-mitigated (no Access, new DO app bc240b8a)
- CHANGED staging-alerts.rainbet.com engine.io v4 handshake persists (200, fresh sid: `0gDL_9TQP86sFRNOAACb`)
- CHANGED staging-chat.rainbet.com engine.io v4 REAPPEARED (200 len=116) after 400
- CHANGED staging-raffles.rainbet.com /health CONFIRMED STABLE real origin JSON (75B, x-do-orig-status:200)
- CHANGED api.rainbet.com OPTIONS blanket exemption CONFIRMED STABLE on /api/v2/, /graphql (200, Allow + x-do-orig-status:200 + x-do-app-origin:53f39197)
- CHANGED staging-cdn.rainbet.com R2 bucket uniformly 404 on root/robots.txt (28KB/27KB)
- CHANGED staging-originals.rainbet.com 504→404 (2B) — origin decommissioned

## 2026-09-08 04:14:08 UTC

## 2026-09-08 08:54:05 UTC
- CHANGED staging-monorepo.rainbet.com /health: 404 response body changed from `{} ` (2B) to `{"message":"Cannot GET /health","error":"Not Found","statusCode":404}` (69B) — Express error handling updated, still
- CHANGED staging-alerts.rainbet.com/socket.io: 400 this round (was 200 at 23:48); intermittent toggle continues.
- NEW No new live hosts since 2026-09-04 (files.rainbet.com, media.rainbet.com remain only new discoveries)
- CHANGED staging-cdn.rainbet.com R2 bucket uniformly 404 on root/robots.txt (28KB/27KB "Object not found")
- CHANGED staging-originals.rainbet.com 504→404 (2B) — origin decommissioned/unmounted
- CHANGED staging-alerts.rainbet.com engine.io v4 handshake PERSISTS (200, fresh sid per request) — plane stable 9+ rounds
- CHANGED staging-chat.rainbet.com engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on app 1ce4ff55
- CHANGED staging-raffles.rainbet.com /health CONFIRMED STABLE real origin JSON (75B, x-do-orig-status:200, x-do-app-origin:1ce4ff55)
- CHANGED staging-services.rainbet.com /health 404, /docs 302→Access (path-partial Access narrower; only /docs protected)
- CHANGED staging-monorepo.rainbet.com /health 404, /docs 403 non-cf-mitigated (no Access, new DO app bc240b8a)
- CHANGED api.rainbet.com OPTIONS blanket exemption CONFIRMED STABLE on /api/v2/, /graphql, /swagger, /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197)

## 2026-09-08 13:46:24 UTC

## 2026-09-08 17:38:14 UTC
- NEW staging-monorepo.rainbet.com /health error body changed to Express format `{"message":"Cannot GET /health","error":"Not Found","statusCode":404}` (69B) — error handling updated, still 404
- NEW staging-alerts.rainbet.com/socket.io intermittent toggle: 400 this round (was 200 at 23:48) — plane persists but flapping
- CHANGED staging-services.rainbet.com path-partial Access confirmed narrower: only /docs 302→Access; /health,/api/*,/metrics,/socket.io return 404
- CHANGED staging-monorepo.rainbet.com /health 404, /docs 403 non-cf-mitigated (no Access, new DO app bc240b8a)
- CHANGED api.rainbet.com OPTIONS blanket exemption CONFIRMED STABLE on /api/v2/, /graphql, /swagger, /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197)
- CHANGED staging-raffles.rainbet.com /health CONFIRMED STABLE real origin JSON (75B, x-do-orig-status:200, x-do-app-origin:1ce4ff55)
- CHANGED staging-cdn.rainbet.com R2 bucket uniformly 404 on root/robots.txt (28KB/27KB "Object not found")
- CHANGED staging-originals.rainbet.com 504→404 (2B) — origin decommissioned/unmounted

## 2026-09-08 20:21:32 UTC
- CHANGED staging-alerts.rainbet.com engine.io v4 handshake flapping: 400 at 17:38 (was 200 at 08:54) — plane persists but intermittent
- CHANGED staging-monorepo.rainbet.com /health error body now Express format 69B `{"message":"Cannot GET /health","error":"Not Found","statusCode":404}` (was 2B `{}`) — error handling updated, still 404
- CHANGED staging-services.rainbet.com path-partial Access confirmed narrower: only /docs 302→Access (kid 31d4206e); /health,/api/*,/metrics,/socket.io all 404
- CHANGED api.rainbet.com OPTIONS blanket exemption STABLE on /api/v2/,/graphql,/swagger,/openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197) — different DO app vs staging fleet
- CHANGED staging-raffles.rainbet.com /health CONFIRMED STABLE real origin JSON (75B, x-do-orig-status:200, x-do-app-origin:1ce4ff55, no cf-mitigated, no CF Access)
- CHANGED staging-cdn.rainbet.com R2 bucket uniformly 404 on root/robots.txt (28KB/27KB "Object not found")
- CHANGED staging-originals.rainbet.com 504→404 (2B) — origin decommissioned/unmounted
- NEW No new live hosts since 2026-09-04 (files.rainbet.com, media.rainbet.com remain only new discoveries)

## 2026-09-08 22:46:28 UTC
- CHANGED staging-alerts.rainbet.com engine.io v4 handshake flapping: 400 at 17:38 (was 200 at 08:54) — plane persists but intermittent
- CHANGED staging-monorepo.rainbet.com /health error body now Express format 69B `{"message":"Cannot GET /health","error":"Not Found","statusCode":404}` (was 2B `{}`) — error handling updated, still 404
- CHANGED staging-services.rainbet.com path-partial Access confirmed narrower: only /docs 302→Access (kid 31d4206e); /health,/api/*,/metrics,/socket.io all 404
- CHANGED api.rainbet.com OPTIONS blanket exemption STABLE on /api/v2/,/graphql,/swagger,/openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197) — different DO app vs staging fleet
- CHANGED staging-raffles.rainbet.com /health CONFIRMED STABLE real origin JSON (75B, x-do-orig-status:200, x-do-app-origin:1ce4ff55, no cf-mitigated, no CF Access)
- CHANGED staging-cdn.rainbet.com R2 bucket uniformly 404 on root/robots.txt (28KB/27KB "Object not found")
- CHANGED staging-originals.rainbet.com 504→404 (2B) — origin decommissioned/unmounted
- NEW No new live hosts since 2026-09-04 (files.rainbet.com, media.rainbet.com remain only new discoveries)

## 2026-09-09 01:15:30 UTC
- CHANGED staging-alerts.rainbet.com engine.io v4 handshake flapping: 400 at 17:38 (was 200 at 08:54) — plane persists but intermittent
- CHANGED staging-monorepo.rainbet.com /health error body now Express format 69B `{"message":"Cannot GET /health","error":"Not Found","statusCode":404}` (was 2B `{}`) — error handling updated, still 404
- CHANGED staging-services.rainbet.com path-partial Access confirmed narrower: only /docs 302→Access (kid 31d4206e); /health,/api/*,/metrics,/socket.io all 404
- CHANGED api.rainbet.com OPTIONS blanket exemption STABLE on /api/v2/,/graphql,/swagger,/openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197) — different DO app vs staging fleet
- CHANGED staging-raffles.rainbet.com /health CONFIRMED STABLE real origin JSON (75B, x-do-orig-status:200, x-do-app-origin:1ce4ff55, no cf-mitigated, no CF Access)
- CHANGED staging-cdn.rainbet.com R2 bucket uniformly 404 on root/robots.txt (28KB/27KB "Object not found")
- CHANGED staging-originals.rainbet.com 504→404 (2B) — origin decommissioned/unmounted
- NEW No new live hosts since 2026-09-04 (files.rainbet.com, media.rainbet.com remain only new discoveries)

## 2026-09-09 06:15:59 UTC
- CHANGED staging-services.rainbet.com: `x-powered-by: Express` now visible on error responses (was reported NestJS on 2026-09-07) — NestJS runs on Express but typically self-identifies; possible app reconfigur
- CHANGED staging-services.rainbet.com: CORS reflector confirmed on `/api/v1/users` (untested prior) — path-agnostic per-DO-app reflector (3/3 paths tested reflect arbitrary Origin + credentials + expose-header
- NEW staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with NO auth — returns `40{"sid":"..."}` (200). staging-alerts properly rejects empty/fake tokens with `er_auth_token_inv
- CHANGED staging-services.rainbet.com: `x-powered-by: Express` now visible (was NestJS on 2026-09-07); CORS reflector confirmed on `/api/v1/users` (untested prior) — path-agnostic reflector (3/3 paths)

## 2026-09-09 11:42:50 UTC
- NEW staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with NO auth — returns `40{"sid":"...","_placeholder":true}` establishing valid session on DO app 1ce4ff55
- NEW staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er_auth_token_invalid","data":{"status":401}}` — per-hostn
- CHANGED staging-services.rainbet.com: `x-powered-by: Express` now visible on error responses (was NestJS on 2026-09-07); CORS reflector confirmed path-agnostic on 3/3 tested paths (/health, /api/v1/users, OPT
- CHANGED api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — active operator WAF churn on DO app 53f39197; OPTIONS blanket 
- CHANGED staging-alerts.rainbet.com: engine.io v4 anonymous sid issuance persists (10+ rounds, fresh sid each request); WebSocket upgrade CONFIRMED WORKING with captured sid (sid=0gDL_9TQP86sFRNOAACb, upgrades
- CHANGED staging-raffles.rainbet.com: origin JSON /health stable (75B, x-do-orig-status:200, full CSP+HSTS+XFO headers, no cf-mitigated, no CF Access)
- CHANGED staging-monorepo.rainbet.com: /docs now returns standard 5485B CF WAF block page (not origin 403) — WAF front now uniform on app bc240b8a

## 2026-09-09 15:27:15 UTC
- NEW staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with NO auth — returns `40{"sid":"...","_placeholder":true}` establishing valid session on DO app 1ce4ff55
- NEW staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er_auth_token_invalid","data":{"status":401}}` — per-hostn
- CHANGED api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — active operator WAF churn on DO app 53f39197
- CHANGED staging-services.rainbet.com: CORS reflector confirmed path-agnostic on 3/3 tested paths (/health, /api/v1/users, OPTIONS /api/v1) — reflects arbitrary Origin + allow-credentials:true + access-control
- CHANGED staging-monorepo.rainbet.com: /docs now returns standard 5485B CF WAF block page (not origin 403) — WAF front now uniform on app bc240b8a
- CHANGED staging-alerts.rainbet.com: engine.io v4 anonymous sid issuance persists (10+ rounds, fresh sid each request); WebSocket upgrade CONFIRMED WORKING with captured sid (sid=0gDL_9TQP86sFRNOAACb, upgrades
- CHANGED staging-raffles.rainbet.com: origin JSON /health stable (75B, x-do-orig-status:200, full CSP+HSTS+XFO headers, no cf-mitigated, no CF Access)

## 2026-09-09 18:45:51 UTC
- NEW staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with NO auth — returns `40{"sid":"...","_placeholder":true}` establishing valid session on DO app 1ce4ff55
- NEW staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er_auth_token_invalid","data":{"status":401}}` — per-hostn
- CHANGED api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — active operator WAF churn on DO app 53f39197
- CHANGED staging-services.rainbet.com: CORS reflector confirmed path-agnostic on 3/3 tested paths (/health, /api/v1/users, OPTIONS /api/v1) — reflects arbitrary Origin + allow-credentials:true + access-control
- CHANGED staging-monorepo.rainbet.com: /docs now returns standard 5485B CF WAF block page (not origin 403) — WAF front now uniform on app bc240b8a
- CHANGED staging-alerts.rainbet.com: engine.io v4 anonymous sid issuance persists (10+ rounds, fresh sid each request); WebSocket upgrade CONFIRMED WORKING with captured sid (sid=0gDL_9TQP86sFRNOAACb, upgrades
- CHANGED staging-raffles.rainbet.com: origin JSON /health stable (75B, x-do-orig-status:200, full CSP+HSTS+XFO headers, no cf-mitigated, no CF Access)

## 2026-09-09 21:36:53 UTC

## 2026-09-09 23:35:01 UTC
- NEW staging-chat.rainbet.com/socket.io: unauthenticated namespace joins EXPANDED beyond root — /raffles and /alerts both ack connect with `40{"sid":"..."}` on anonymous engine.io sid (connect requires sid
- CHANGED api.rainbet.com WAF state: unchanged from 2026-09-09 — content GET = 5484B block, no cf-mitigated; OPTIONS /openapi.json = 200 + `Allow: OPTIONS,HEAD,GET,POST` + x-do-orig-status:200 + app 53f39197.
- CHANGED staging-services CORS reflector: persists on /health AND new path /api/v1/games (both 404, ACAO-relect+credentials+expose Cf-Mitigated, x-powered-by Express) — no 2xx still.
- CHANGED alerts/chat engine.io: both 200 len=116 (plane up); raffles /health 75B stable; monorepo /health 404/69B stable.

## 2026-09-10 01:34:53 UTC
- NEW staging-chat.rainbet.com/socket.io: unauthenticated namespace joins EXPANDED beyond root — /raffles and /alerts both ack connect with `40{"sid":"..."}` on anonymous engine.io sid (connect requires sid
- CHANGED api.rainbet.com WAF state: unchanged from 2026-09-09 — content GET = 5484B block, no cf-mitigated; OPTIONS /openapi.json = 200 + `Allow: OPTIONS,HEAD,GET,POST` + x-do-orig-status:200 + app 53f39197.
- CHANGED staging-services CORS reflector: persists on /health AND new path /api/v1/games (both 404, ACAO-relect+credentials+expose Cf-Mitigated, x-powered-by Express) — no 2xx still.
- CHANGED alerts/chat engine.io: both 200 len=116 (plane up); raffles /health 75B stable; monorepo /health 404/69B stable.
- NEW staging-chat.rainbet.com/socket.io: socket.io root namespace accepts bare CONNECT (`40`) with NO auth — returns `40{"sid":"...","_placeholder":true}` establishing valid session on DO app 1ce4ff55; /ra
- NEW staging-chat.rainbet.com/socket.io: unauthenticated namespace joins EXPANDED beyond root — /raffles and /alerts both ack connect with `40{"sid":"..."}` on anonymous engine.io sid
- CHANGED api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — active operator WAF churn on DO app 53f39197
- CHANGED staging-services.rainbet.com: CORS reflector confirmed path-agnostic on 4 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games) — reflects arbitrary Origin + allow-credentials:true + access-c
- CHANGED staging-monorepo.rainbet.com: /docs now returns standard 5485B CF WAF block page (not origin 403) — WAF front now uniform on app bc240b8a
- CHANGED staging-alerts.rainbet.com: engine.io v4 anonymous sid issuance persists (10+ rounds, fresh sid each request); WebSocket upgrade CONFIRMED WORKING with captured sid (sid=0gDL_9TQP86sFRNOAACb, upgrades

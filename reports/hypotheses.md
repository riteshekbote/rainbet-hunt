# Hypotheses (ranked)

## RANKED HYPOTHESES 2026-09-02 21:55:57 UTC

## RANKED HYPOTHESES 2026-09-02 23:56:28 UTC

## RANKED HYPOTHESES 2026-09-03 03:59:57 UTC

## RANKED HYPOTHESES 2026-09-03 08:57:58 UTC

## RANKED HYPOTHESES 2026-09-03 13:31:20 UTC

## RANKED HYPOTHESES 2026-09-03 17:24:37 UTC
- [55] api.rainbet.com: API endpoint enumeration behind Cloudflare challenge (from art/lead_nemotron3.txt)
- [45] staging.rainbet.com: staging Cloudflare Access JWT parsing weakness (from art/lead_bigpickle.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://api.rainbet.com/api/v1/public/ping with headers: Accept: application/json, User-Agent: RainBet-Mobile/1.0 (test common mobile API endpoint pa
- NEXT(hypotheses-bigpickle.txt): PROBE: GET `https://staging.rainbet.com/.well-known/cloudflare-access-protected-resource/` — retrieve CF Access protected resource metadata (may expose policy d
- LEARN: REJECTED MISCONFIG @ staging.rainbet.com: Cloudflare Access Zero Trust is properly configured (default-deny, JWT metadata visible but no bypass); no evidence of
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all paths including static assets; no unchallenged surface discovered passively
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: API subdomain exists and resolves but returns uniform 403 challenge; high-value target if any endpoint allows unauthentica
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: CF block page present but `cf-mitigated` header absent (unlike www.rainbet.com) — different CF WAF configurations per subd
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: CF Access JWT contains `auth_status: NONE` and `is_wrap: false` — Access policy may be permissive or misconfigured.
- LEARN: REJECTED dead subdomains (17/20): No DNS resolution or HTTP service — removed from active attack surface until re-checked.

## RANKED HYPOTHESES 2026-09-03 20:04:47 UTC
- [90] staging.rainbet.com: Staging Cloudflare Access policy bypass — multiple sensitive endpoints exposed (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging.rainbet.com/health with header Accept: text/html (analyze body — confirm if CF challenge page or real app), then GET https://staging.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Cloudflare Access policy has gaps — /health, /metrics, /api/health, /.well-known/jwks.json return HTTP 200 (32KB HTML) inst
- LEARN: REJECTED MISCONFIG @ staging.rainbet.com: Previous assessment that "Cloudflare Access Zero Trust is properly configured" was incorrect — policy enforcement has 
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: CF block page present but `cf-mitigated` header absent (unlike www.rainbet.com) — different CF WAF configurations per subd
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths including static assets (/assets/) and /api/ — no unchallenged surface di

## RANKED HYPOTHESES 2026-09-03 22:32:18 UTC
- [85] staging.rainbet.com: Staging Cloudflare Access policy bypass — multiple API endpoints exposed (from art/lead_nemotron3.txt)
- [55] api.rainbet.com: API endpoint enumeration behind Cloudflare challenge (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://api.rainbet.com/api/v1/public/ping with headers: Accept: application/json, User-Agent: RainBet-Mobile/1.0 (test common mobile API endpoint pa
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging.rainbet.com/api/v1/public/config with header Accept: application/json (check for real JSON config vs CF challenge HTML), then GET htt
- LEARN: REJECTED MISCONFIG @ staging.rainbet.com: Cloudflare Access Zero Trust is properly configured (default-deny, JWT metadata visible but no bypass); no evidence of
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all paths including static assets; no unchallenged surface discovered passively
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: API subdomain exists and resolves but returns uniform 403 challenge; high-value target if any endpoint allows unauthentica
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Cloudflare Access policy has gaps — /health, /metrics, /api/health, /.well-known/jwks.json return HTTP 200 (32KB HTML) inst
- LEARN: REJECTED MISCONFIG @ staging.rainbet.com: Previous assessment that "Cloudflare Access Zero Trust is properly configured" was incorrect — policy enforcement has 
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: CF block page present but `cf-mitigated` header absent (unlike www.rainbet.com) — different CF WAF configurations per subd
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths including static assets (/assets/) and /api/ — no unchallenged surface di
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: CF block page present but `cf-mitigated` header absent (unlike www.rainbet.com) — different CF WAF configurations per subd
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: CF Access JWT contains `auth_status: NONE` and `is_wrap: false` — Access policy may be permissive or misconfigured.
- LEARN: REJECTED dead subdomains (17/20): No DNS resolution or HTTP service — removed from active attack surface until re-checked.
- LEARN: REJECTED AUTH @ staging.rainbet.com: All sensitive paths 302->Access login; prior 200 gap transient/irreproducible.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge present now; encoding bypass fails; no WAF inconsistency.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v1/ 200 Allow OPTIONS,HEAD,GET,POST — preflight passthrough.
- LEARN: REJECTED AUTH @ staging.rainbet.com: All sensitive paths 302->Access login; prior 200 gap transient/irreproducible.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge present now; encoding bypass fails; no WAF inconsistency.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v1/ 200 Allow OPTIONS,HEAD,GET,POST — preflight passthrough.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: OPTIONS passes WAF (200, Allow methods) but returns NO Access-Control-* headers even with evil Origin — no CORS misconfig,
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Cloudflare Access policy has gaps — /health, /metrics, /api/health, /api/v1/health, /api/v1/public/config, /.well-known/jwk
- LEARN: REJECTED MISCONFIG @ staging.rainbet.com: Previous assessment that "Cloudflare Access Zero Trust is properly configured" was incorrect — policy enforcement has 
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: CF block page present but `cf-mitigated` header absent (unlike www.rainbet.com) — different CF WAF configurations per subd
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths including static assets (/assets/) and /api/ — no unchallenged surface di

## RANKED HYPOTHESES 2026-09-04 00:32:38 UTC
- [85] staging.rainbet.com: Staging Cloudflare Access policy bypass — multiple API endpoints exposed (from art/lead_nemotron3.txt)
- [42] api.rainbet.com/api/v1/: api.rainbet.com POST-with-JSON bypasses GET challenge → API router/contract reachable (from art/lead_bigpickle.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging.rainbet.com/api/v1/public/config with header Accept: application/json (check for real JSON config vs CF challenge HTML), then GET htt
- NEXT(hypotheses-bigpickle.txt): PROBE: POST https://api.rainbet.com/api/v1/public/ping with headers `Content-Type: application/json` and body `{}` (single read-only POST to a public/read names
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Cloudflare Access policy has gaps — /health, /metrics, /api/health, /api/v1/health, /api/v1/public/config, /.well-known/jwk
- LEARN: REJECTED MISCONFIG @ staging.rainbet.com: Previous assessment that "Cloudflare Access Zero Trust is properly configured" was incorrect — policy enforcement has 
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: CF block page present but `cf-mitigated` header absent (unlike www.rainbet.com) — different CF WAF configurations per subd
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths including static assets (/assets/) and /api/ — no unchallenged surface di
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v1/ 200 Allow OPTIONS,HEAD,GET,POST — preflight passthrough.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: OPTIONS passes WAF (200, Allow methods) but returns NO Access-Control-* headers even with evil Origin — no CORS misconfig,
- LEARN: REJECTED AUTH @ staging.rainbet.com: Access policy-gap finding (200 on /health,/metrics,/api/health) is non-reproducible across independent probe rounds — both 
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-to-ping route remains untested — prior POST claims were to general /api/v1/ only; not yet re-probed, so not yet contr

## RANKED HYPOTHESES 2026-09-04 05:12:50 UTC
- [85] staging.rainbet.com: Staging Cloudflare Access policy bypass — multiple API endpoints exposed (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging.rainbet.com/api/v1/public/config with header Accept: application/json (check for real JSON config vs CF challenge HTML), then GET htt
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Cloudflare Access policy has gaps — /health, /metrics, /api/health, /api/v1/health, /api/v1/public/config, /.well-known/jwk
- LEARN: REJECTED MISCONFIG @ staging.rainbet.com: Previous assessment that "Cloudflare Access Zero Trust is properly configured" was incorrect — policy enforcement has 
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: CF block page present but `cf-mitigated` header absent (unlike www.rainbet.com) — different CF WAF configurations per subd
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths including static assets (/assets/) and /api/ — no unchallenged surface di
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v1/ 200 Allow OPTIONS,HEAD,GET,POST — preflight passthrough.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: OPTIONS passes WAF (200, Allow methods) but returns NO Access-Control-* headers even with evil Origin — no CORS misconfig,
- LEARN: REJECTED AUTH @ staging.rainbet.com: Access policy-gap finding (200 on /health,/metrics,/api/health) is non-reproducible across independent probe rounds — both 
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-to-ping route remains untested — prior POST claims were to general /api/v1/ only; not yet re-probed, so not yet contr

## RANKED HYPOTHESES 2026-09-04 09:48:46 UTC
- [85] staging.rainbet.com: Staging Cloudflare Access policy bypass — multiple API endpoints exposed (from art/lead_nemotron3.txt)
- [42] api.rainbet.com/api/v1/public/ping: api.rainbet.com POST-with-JSON bypasses GET challenge → API router/contract reachable (from art/lead_bigpickle.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging.rainbet.com/api/v1/public/config with header Accept: application/json (check for real JSON config vs CF challenge HTML)
- NEXT(hypotheses-bigpickle.txt): PROBE: POST https://api.rainbet.com/api/v1/public/ping with `Content-Type: application/json` and body `{}` — single read-only POST to public namespace, record s
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Cloudflare Access policy has gaps — /health, /metrics, /api/health, /api/v1/health, /api/v1/public/config, /.well-known/jwk
- LEARN: REJECTED MISCONFIG @ staging.rainbet.com: Previous assessment that "Cloudflare Access Zero Trust is properly configured" was incorrect — policy enforcement has 
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: CF block page present but `cf-mitigated` header absent (unlike www.rainbet.com) — different CF WAF configurations per subd
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths including static assets (/assets/) and /api/ — no unchallenged surface di
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v1/ 200 Allow OPTIONS,HEAD,GET,POST — preflight passthrough.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: OPTIONS passes WAF (200, Allow methods) but returns NO Access-Control-* headers even with evil Origin — no CORS misconfig,
- LEARN: REJECTED AUTH @ staging.rainbet.com: Access policy-gap finding (200 on /health,/metrics,/api/health) is non-reproducible across independent probe rounds — both 
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-to-ping route remains untested — prior POST claims were to general /api/v1/ only; not yet re-probed, so not yet contr
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: OPTIONS passes WAF (200, Allow methods) but returns NO Access-Control-* headers even with evil Origin — no CORS misconfig,
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v1/ 200 Allow OPTIONS,HEAD,GET,POST — preflight passthrough confirmed; method-sensitive WAF rule.
- LEARN: REJECTED AUTH @ staging.rainbet.com: Access policy-gap finding non-reproducible across rounds, but latest 2026-09-04 00:32 probe shows reappearance — treating a

## RANKED HYPOTHESES 2026-09-04 14:14:04 UTC
- [55] api.rainbet.com/api/v1/: api.rainbet.com OPTIONS preflight leaks allowed methods → API contract enumeration (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: OPTIONS https://api.rainbet.com/api/v2/ -H "Origin: https://evil.com" -H "Access-Control-Request-Method: GET" (check Allow header + CORS), then OPTIONS h
- LEARN: REJECTED AUTH @ staging.rainbet.com: Cloudflare Access policy gap (HTTP 200 on 6 endpoints) was **transient/fixed** — latest probes (2026-09-04 14:07 UTC) show 
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v1/ returns 200 with Allow: OPTIONS,HEAD,GET,POST but **no CORS headers** — preflight passthrough is CORS-neu
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header now present on all 403 responses — WAF configuration consistent across subdomains (api, www
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-04 17:48:27 UTC
- [55] api.rainbet.com/api/v1/: api.rainbet.com OPTIONS preflight leaks allowed methods → API contract enumeration (from art/lead_nemotron3.txt)
- [45] api.rainbet.com: api/services DO direct-origin bypass via x-do-app-origin leak → CF WAF-less origin access (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): RAG: OSINT-hunt the six DigitalOcean App UUIDs and RainBet app slugs for `*.ondigitalocean.app` default-domain FQDNs (unproxied by Cloudflare WAF); verify any c
- NEXT(hypotheses-nemotron3.txt): PROBE: OPTIONS https://api.rainbet.com/api/v2/ -H "Origin: https://evil.com" -H "Access-Control-Request-Method: GET" (check Allow header + CORS), then OPTIONS h
- LEARN: REJECTED AUTH @ staging.rainbet.com: Cloudflare Access policy gap (HTTP 200 on 6 endpoints) was **transient/fixed** — latest probes (2026-09-04 14:07 UTC) show 
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v1/ returns 200 with Allow: OPTIONS,HEAD,GET,POST but **no CORS headers** — preflight passthrough is CORS-neu
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header now present on all 403 responses — WAF configuration consistent across subdomains (api, www
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-04 20:00:51 UTC
- [55] staging.rainbet.com: Staging intermittent Cloudflare Access policy enforcement → race condition on policy evaluation (from art/lead_nemotron3.txt)
- [55] api.rainbet.com: RainBet API contract & auth-scheme mining from leaked/mobile assets (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): RAG: GitHub code search + CommonCrawl + APK mirrors for a RainBet (RBGAMING) client bundle or API docs containing api.rainbet.com path/auth strings; extract rea
- NEXT(hypotheses-nemotron3.txt): PROBE: OPTIONS https://api.rainbet.com/api/v1/ -H "Origin: https://evil.com" -H "Access-Control-Request-Method: POST" (confirm Allow header consistency + CORS n
- LEARN: REJECTED AUTH @ staging.rainbet.com: Cloudflare Access policy gap (HTTP 200 on 6 endpoints) was **transient/fixed** — latest probes (2026-09-04 14:07 UTC) show 
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v1/ returns 200 with Allow: OPTIONS,HEAD,GET,POST but **no CORS headers** — preflight passthrough is CORS-neu
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header now present on all 403 responses — WAF configuration consistent across subdomains (api, www
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v2/, /graphql, /swagger return 403 (not 200) — only /api/v1/ leaks Allow header; WAF rule is version-sensitiv
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Access policy gap **reappeared** at 2026-09-04 17:48 (6 endpoints HTTP 200, 32KB) after 302 at 14:07 — intermittent enforce
- LEARN: NEW LIVE HOSTS @ files.rainbet.com, media.rainbet.com: Both resolve and return 403 on probed paths (/api/v1/public/ping, /robots.txt) — attack surface expanded 

## RANKED HYPOTHESES 2026-09-04 22:17:39 UTC
- [65] staging.rainbet.com: Staging intermittent Cloudflare Access policy enforcement → race condition on policy evaluation (from art/lead_nemotron3.txt)
- [35] staging.rainbet.com: staging Access drift window re-opens 6 endpoints with origin JSON behind 200 (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): RAG: GitHub code search + CommonCrawl + APK mirrors for a RainBet (RBGAMING) client bundle or API docs containing api.rainbet.com path/auth strings; extract rea
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging.rainbet.com/api/v1/public/config -H "Accept: application/json" (check for real JSON config vs CF challenge HTML in current gap window
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Access policy gap **reappeared** at 2026-09-04 17:48 and **persists at 20:00** (3 endpoints HTTP 200, 32KB) after 302 at 14
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v2/, /graphql, /swagger return 403 (not 200) — only /api/v1/ leaks Allow header; WAF rule is version-sensitiv
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header now present on all 403 responses — WAF configuration consistent across subdomains (api, www
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.
- LEARN: NEW LIVE HOSTS @ files.rainbet.com, media.rainbet.com: Both resolve and return 403 on probed paths (/api/v1/public/ping, /robots.txt) — attack surface expanded 

## RANKED HYPOTHESES 2026-09-05 00:15:57 UTC
- [65] staging.rainbet.com: Staging intermittent Cloudflare Access policy enforcement → race condition on policy evaluation (from art/lead_nemotron3.txt)
- [55] staging.rainbet.com: api.rainbet.com DigitalOcean App Platform direct-origin bypass via unproxied *.ondigitalocean.app FQDN (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: OPTIONS https://api.rainbet.com/api/v1/ -H "Origin: https://evil.com" -H "Access-Control-Request-Method: POST" (confirm Allow header consistency + CORS n
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging.rainbet.com/api/v1/public/config -H "Accept: application/json" (check for real JSON config vs CF challenge HTML in current gap window
- LEARN: REJECTED AUTH @ staging.rainbet.com: Cloudflare Access policy gap (HTTP 200 on 6 endpoints) was **transient/fixed** — latest probes (2026-09-04 14:07 UTC) show 
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v1/ returns 200 with Allow: OPTIONS,HEAD,GET,POST but **no CORS headers** — preflight passthrough is CORS-neu
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header now present on all 403 responses — WAF configuration consistent across subdomains (api, www
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v2/, /graphql, /swagger return 403 (not 200) — only /api/v1/ leaks Allow header; WAF rule is version-sensitiv
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Access policy gap **reappeared** at 2026-09-04 17:48 (6 endpoints HTTP 200, 32KB) after 302 at 14:07 — intermittent enforce
- LEARN: NEW LIVE HOSTS @ files.rainbet.com, media.rainbet.com: Both resolve and return 403 on probed paths (/api/v1/public/ping, /robots.txt) — attack surface expanded 
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Access policy gap **reappeared** at 2026-09-04 17:48 and **persists at 20:00** (3 endpoints HTTP 200, 32KB) after 302 at 14
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v2/, /graphql, /swagger return 403 (not 200) — only /api/v1/ leaks Allow header; WAF rule is version-sensitiv
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header now present on all 403 responses — WAF configuration consistent across subdomains (api, www
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.
- LEARN: NEW LIVE HOSTS @ files.rainbet.com, media.rainbet.com: Both resolve and return 403 on probed paths (/api/v1/public/ping, /robots.txt) — attack surface expanded 
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Access policy gap **reappeared** at 2026-09-04 17:48 and **persists at 20:00 and 22:17** (3 endpoints HTTP 200, 32KB) after
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v2/, /graphql, /swagger return 403 (not 200) — only /api/v1/ leaks Allow header; WAF rule is version-sensitiv
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header now present on all 403 responses — WAF configuration consistent across subdomains (api, www
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.
- LEARN: NEW LIVE HOSTS @ files.rainbet.com, media.rainbet.com: Both resolve and return 403 on probed paths (/api/v1/public/ping, /robots.txt) — attack surface expanded 

## RANKED HYPOTHESES 2026-09-05 04:45:45 UTC
- [75] rainbet-com-rabbitmq: Internet-exposed RabbitMQ brokers (management + plaintext AMQP) on direct DigitalOcean origins bypassing Cloudflare (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): SCAN: single GET (0.7s spacing) over remaining live CT-hosts — `alerts, aiostaging, chat, clever, ds, help, maintenance, raffles, slot-integrations, staging-ale
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /api/v1/ returns 200 with Allow: HEAD,GET,POST,OPTIONS but no CORS headers — preflight passthrough is CORS-neutral
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.
- LEARN: NEW LIVE HOSTS @ files.rainbet.com, media.rainbet.com: Both resolve and return 403 on probed paths (/api/v1/public/ping, /robots.txt) — attack surface expanded 

## RANKED HYPOTHESES 2026-09-05 08:45:33 UTC
- [60] staging-raffles.rainbet.com: Staging Socket.IO pocket app (1ce4ff55) reaches beyond /health into the session plane or leaks DB/version state (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: cadence every ~30 min: GET staging-raffles.rainbet.com/health (hash/compare vs known `{"code":200,"db":"Running"...v0.00.0002-rc1}` shell) + GET staging-
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected (~09:00Z) — `{"code":200,"db":"Running","remote_address":"-","version":"v
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS exemption is now BLANKET-path (200 on /api/v2/, /graphql, /swagger, /openapi.json, /nonsense) — widens each operat
- LEARN: ACCEPTED AUTH @ staging-chat/alerts/socket/raffles.rainbet.com: engine.io v4 handshake issues anonymous sids unauthenticated on 4 hostnames of one DO app (app i
- LEARN: REJECTED AUTH @ staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80) — intermittent drifting continues; "open" windows have only ever
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.

## RANKED HYPOTHESES 2026-09-05 12:24:29 UTC
- [90] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes real origin API and engine.io socket plane without auth (from art/lead_nemotron3.txt)
- [60] <host/endpoint>: <title> (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: cadence every ~30 min: GET staging-raffles.rainbet.com/health (hash/compare vs known `{"code":200,"db":"Running"...v0.00.0002-rc1}` shell) + GET staging-
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-raffles.rainbet.com/api/v1/public/config -H "Accept: application/json" (confirm real JSON config vs error page); GET https://staging-
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected (~09:00Z) — `{"code":200,"db":"Running","remote_address":"-","version":"v
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS exemption is now BLANKET-path (200 on /api/v2/, /graphql, /swagger, /openapi.json, /nonsense) — widens each operat
- LEARN: ACCEPTED AUTH @ staging-chat/alerts/socket/raffles.rainbet.com: engine.io v4 handshake issues anonymous sids unauthenticated on 4 hostnames of one DO app (app i
- LEARN: REJECTED AUTH @ staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80) — intermittent drifting continues; "open" windows have only ever
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected (~09:00Z) — `{"code":200,"db":"Running","remote_address":"-","version":"v
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS exemption is now BLANKET-path (200 on /api/v2/, /graphql, /swagger, /openapi.json, /nonsense) — widens each operat
- LEARN: ACCEPTED AUTH @ staging-chat/alerts/socket/raffles.rainbet.com: engine.io v4 handshake issues anonymous sids unauthenticated on 4 hostnames of one DO app (app i
- LEARN: REJECTED AUTH @ staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80) — intermittent drifting continues; "open" windows have only ever
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected (~09:00Z) — `{"code":200,"db":"Running","remote_address":"-","version":"v
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS exemption is now BLANKET-path (200 on /api/v2/, /graphql, /swagger, /openapi.json, /nonsense) — widens each operat
- LEARN: ACCEPTED AUTH @ staging-chat/alerts/socket/raffles.rainbet.com: engine.io v4 handshake issues anonymous sids unauthenticated on 4 hostnames of one DO app (app i
- LEARN: REJECTED AUTH @ staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80) — intermittent drifting continues; "open" windows have only ever
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-05 15:33:07 UTC
- [90] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes real origin API and engine.io socket plane without auth (from art/lead_nemotron3.txt)
- [75] staging-raffles.rainbet.com: Staging raffles app exposes full API contract without auth — version/db/remote_addr in /health; socket.io plane on 4 hostnames issues unauthenticated sids (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: cadence GET staging-raffles.rainbet.com/health (hash/compare vs known `{"code":200,"db":"Running"...v0.00.0002-rc1}` shell) + GET staging-originals.rainb
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-raffles.rainbet.com/api/v1/public/config -H "Accept: application/json" (confirm real JSON config vs error page); GET https://staging-
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS exemption is now BLANKET-path (200 on /api/v2/, /graphql, /swagger, /openapi.json, /nonsense) — widens each operat
- LEARN: ACCEPTED AUTH @ staging-chat/alerts/socket/raffles.rainbet.com: engine.io v4 handshake issues anonymous sids unauthenticated on 4 hostnames of one DO app (1ce4f
- LEARN: REJECTED AUTH @ staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80).
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not takeoverable.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket; exposure limited to known keys.
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected (~09:00Z) — `{"code":200,"db":"Running","remote_address":"-","version":"v
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS exemption is now BLANKET-path (200 on /api/v2/, /graphql, /swagger, /openapi.json, /nonsense) — widens each operat
- LEARN: ACCEPTED AUTH @ staging-chat/alerts/socket/raffles.rainbet.com: engine.io v4 handshake issues anonymous sids unauthenticated on 4 hostnames of one DO app (app i
- LEARN: REJECTED AUTH @ staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80) — intermittent drifting continues; "open" windows have only ever
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-05 17:44:35 UTC
- [90] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes real origin API and engine.io socket plane without auth (from art/lead_nemotron3.txt)
- [75] staging-raffles.rainbet.com: staging-raffles Socket.IO/health plane leaks more than a 75-byte shell — session plane or contract disclosure on app 1ce4ff55 (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: cadence GET staging-raffles.rainbet.com/health (body-hash vs `{"code":200,"db":"Running"...rc1}` shell) + GET staging-chat.rainbet.com/socket.io/?EIO=4&t
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-raffles.rainbet.com/api/v1/public/config -H "Accept: application/json" (confirm real JSON config vs error page); GET https://staging-
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE this round (200 + Allow + x-do-orig-status on /openapi.json,/swagger,/graphql,/
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED MISCONFIG @ staging-chat/alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rou
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504 (down); no recovery of a content-bearing staging app observed.
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected (~09:00Z) — `{"code":200,"db":"Running","remote_address":"-","version":"v
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS exemption is now BLANKET-path (200 on /api/v2/, /graphql, /swagger, /openapi.json, /nonsense) — widens each operat
- LEARN: ACCEPTED AUTH @ staging-chat/alerts/socket/raffles.rainbet.com: engine.io v4 handshake issues anonymous sids unauthenticated on 4 hostnames of one DO app (app i
- LEARN: REJECTED AUTH @ staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80) — intermittent drifting continues; "open" windows have only ever
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

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

## RANKED HYPOTHESES 2026-09-05 19:34:08 UTC
- [95] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes full API contract and engine.io socket plane without auth (from art/lead_nemotron3.txt)
- [55] api.rainbet.com: prod api DO-app origin reachable via OPTIONS to disclose router/openapi contract on method-rule widening (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: cadence GET staging-raffles.rainbet.com/health (body-hash vs `{"code":200,"db":"Running"...rc1}`) + GET staging-originals.rainbet.com/socket.io/?EIO=4&tr
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-raffles.rainbet.com/api/v1/public/config -H "Accept: application/json" (confirm real JSON config vs error page); GET https://staging-
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected (~09:00Z) — `{"code":200,"db":"Running","remote_address":"-","version":"v
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS exemption is now BLANKET-path (200 on /api/v2/, /graphql, /swagger, /openapi.json, /nonsense) — widens each operat
- LEARN: ACCEPTED AUTH @ staging-chat/alerts/socket/raffles.rainbet.com: engine.io v4 handshake issues anonymous sids unauthenticated on 4 hostnames of one DO app (app i
- LEARN: REJECTED AUTH @ staging.rainbet.com: Access gap CLOSED at 09:00Z (302; kid rotated to a89d8b80) — intermittent drifting continues; "open" windows have only ever
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-05 21:50:07 UTC
- [95] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes full API contract and engine.io socket plane without auth (from art/lead_nemotron3.txt)
- [85] staging-chat.rainbet.com: DO staging app (1ce4ff55) socket.io engine plane reaches authenticated namespaces / emits within money-adjacent chat events (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET staging-raffles.rainbet.com/health (75B shell body-hash) + GET staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling (fresh sid) + GET staging-
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-raffles.rainbet.com/api/v1/public/config -H "Accept: application/json" (confirm real JSON config vs error page); GET https://staging-
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected (~09:00Z) — `{"code":200,"db":"Running","remote_address":"-","version":"v
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE this round (200 + Allow + x-do-orig-status on /openapi.json,/swagger,/graphql,/
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED MISCONFIG @ staging-chat/alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rou
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504 (down); no recovery of a content-bearing staging app observed.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-05 23:42:45 UTC
- [95] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes full API contract and engine.io socket plane without auth (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-raffles.rainbet.com/api/v1/public/config -H "Accept: application/json" (confirm real JSON config vs 404); GET https://staging-raffles
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected (~09:00Z) — `{"code":200,"db":"Running","remote_address":"-","version":"v
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE this round (200 + Allow + x-do-orig-status on /openapi.json,/swagger,/graphql,/
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry -> 200); NOT a rule closure.
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds.
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 intermittent (200->400) but plane persists on same DO app.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504 (down); no recovery of a content-bearing staging app observed.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-06 01:27:23 UTC
- [95] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes full API contract and engine.io socket plane without auth (from art/lead_nemotron3.txt)
- [58] api.rainbet.com: Prod api OPTIONS pass-through discloses origin contract on method-widening (from art/lead_bigpickle.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-raffles.rainbet.com/api/v1/public/config -H "Accept: application/json" (confirm real JSON config vs 404); GET https://staging-raffles
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected (~09:00Z) — `{"code":200,"db":"Running","remote_address":"-","version":"v
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE this round (200 + Allow + x-do-orig-status on /openapi.json,/swagger,/graphql,/
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds.
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 intermittent (200→400) but plane persists on same DO app.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504 (down); no recovery of a content-bearing staging app observed.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-06 06:37:17 UTC
- [95] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes full API contract and engine.io socket plane without auth (from art/lead_nemotron3.txt)
- [58] api.rainbet.com: api OPTIONS pass-through widens to content on operator WAF edit (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling (confirm fresh anonymous sid persists) + GET https://staging-raffles.rainbet.co
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling -H "Accept: application/json" (capture fresh anonymous sid from engine.io hands
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 issuing fresh anonymous sids unprotected persists (app 1ce4ff55); plane stable across rounds.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption confirmed stable (+ x-do-orig-status + app UUID); scope "everything but / and /docs" holds.
- LEARN: REJECTED MISCONFIG @ staging-chat.rainbet.com: engine.io handshake intermittent (200→400); single-host transient, not a plane closure.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504/unmounted; no content-bearing recovery of shared DO app 1ce4ff55 observed.
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json,
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds.
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 intermittent (200→400) but plane persists on same DO app.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504 (down); no recovery of a content-bearing staging app observed.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-06 11:23:55 UTC
- [95] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes full API contract and engine.io socket plane without auth (from art/lead_nemotron3.txt)
- [85] staging-alerts/chat/raffles.rainbet.com: Anonymous engine.io sid plane reaches JWT-gated namespaces on app 1ce4ff55 (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling + GET https://staging-raffles.rainbet.com/health + OPTIONS https://api.rainbet.
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling -H "Accept: application/json" (capture fresh anonymous sid from engine.io hands
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 issuing fresh anonymous sids unprotected persists (app 1ce4ff55); plane stable across rounds.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption confirmed stable (+ x-do-orig-status + app UUID); scope "everything but / and /docs" holds.
- LEARN: REJECTED MISCONFIG @ staging-chat.rainbet.com: engine.io handshake intermittent (200→400); single-host transient, not a plane closure.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504/unmounted; no content-bearing recovery of shared DO app 1ce4ff55 observed.
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json,
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds.
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 intermittent (200→400) but plane persists on same DO app.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504 (down); no recovery of a content-bearing staging app observed.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-06 14:43:36 UTC
- [85] staging-alerts/chat/raffles.rainbet.com: Anonymous engine.io sid plane reaches JWT-gated namespaces on app 1ce4ff55 (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling + GET https://staging-raffles.rainbet.com/health + OPTIONS https://api.rainbet.
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 issuing fresh anonymous sids unprotected persists (app 1ce4ff55); plane stable across rounds.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption confirmed stable (+ x-do-orig-status + app UUID); scope "everything but / and /docs" holds.
- LEARN: REJECTED MISCONFIG @ staging-chat.rainbet.com: engine.io handshake intermittent (200→400); single-host transient, not a plane closure.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504/unmounted; no content-bearing recovery of shared DO app 1ce4ff55 observed.

## RANKED HYPOTHESES 2026-09-06 17:36:27 UTC
- [95] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes full API contract and engine.io socket plane without auth (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json,
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds.
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on same DO app.
- LEARN: ACCEPTED MISCONFIG @ staging-socket.rainbet.com: engine.io v4 handshake returns 400 (intermittent) but same DO app origin.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504 (down); no recovery of a content-bearing staging app observed.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-06 19:41:52 UTC
- [95] staging-raffles.rainbet.com: Staging pocket app exposes full API contract and engine.io socket plane without auth (from art/lead_bigpickle.txt)
- [95] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes full API contract and engine.io socket plane without auth (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://staging-raffles.rainbet.com/health + GET https://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling + OPTIONS https://api.rainbet.
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 issuing fresh anonymous sids unprotected persists (app 1ce4ff55); plane stable across rounds.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption confirmed stable (+ x-do-orig-status + app UUID); scope "everything but / and /docs" holds.
- LEARN: REJECTED MISCONFIG @ staging-chat.rainbet.com: engine.io handshake intermittent (200→400); single-host transient, not a plane closure.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504/unmounted; no content-bearing recovery of shared DO app 1ce4ff55 observed.
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ staging-socket.rainbet.com: engine.io v4 handshake returns 400 (intermittent) but same DO app origin.
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json,
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds.
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on same DO app.
- LEARN: ACCEPTED MISCONFIG @ staging-socket.rainbet.com: engine.io v4 handshake returns 400 (intermittent) but same DO app origin.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504 (down); no recovery of a content-bearing staging app observed.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-06 21:45:36 UTC
- [95] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes full API contract and engine.io socket plane without auth (from art/lead_nemotron3.txt)
- [85] staging-alerts/chat.rainbet.com: engine.io anonymous sid plane persists but namespace content stays JWT-gated (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://staging-raffles.rainbet.com/health + GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling + OPTIONS https://api.rainbet.co
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds.
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on same DO app.
- LEARN: ACCEPTED MISCONFIG @ staging-socket.rainbet.com: engine.io v4 handshake returns 400 (intermittent) but same DO app origin.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json,
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504 (down); no recovery of a content-bearing staging app observed.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-06 23:40:28 UTC
- [95] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes full API contract and engine.io socket plane without auth (from art/lead_nemotron3.txt)
- [72] staging-raffles.rainbet.com/health: Staging pocket app origin leak enables full contract mapping on next WAF/route edit (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://staging-raffles.rainbet.com/health + GET https://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling + OPTIONS https://api.rainbet.
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 REAPPEARED (200 len=116 sid=oh95TnJA56TZ66eXAEKG maxPayload=20480) after 400 at 21:45 — plane pers
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116 sid=qYWJN8MrQlI7JVuSAAB8 maxPayload=10240) after 400 at 21:45 — plane persis
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: 504→404 (2B) — origin decommissioned or route unmounted entirely; no content-bearing recovery of shared DO app 1c
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: R2 bucket uniformly 404 on root and robots.txt (28KB/27KB "Object not found" pages); no listing.
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: real origin JSON confirmed stable (200 len=75); CSP headers (Helmet) + HSTS + x-frame-options: DENY; no CF Acc
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (+ x-do-orig-status:200 + x-do-app-origin:53f39197 on /openapi.json, /api/v2/);
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping still 403 (110KB cf-mitigated); no content-method bypass.
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds.
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on same DO app.
- LEARN: ACCEPTED MISCONFIG @ staging-socket.rainbet.com: engine.io v4 handshake returns 400 (intermittent) but same DO app origin.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json,
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504 (down); no recovery of a content-bearing staging app observed.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-07 01:21:46 UTC
- [84] staging-alerts.rainbet.com: engine.io anonymous sid plane reaches JWT-gated namespaces on app 1ce4ff55 (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): AUTH_HELPED: POST https://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling with sid from latest handshake (oh95TnJA56TZ66eXAEKG) — attempt namespac
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 REAPPEARED (200 len=116 sid=oh95TnJA56TZ66eXAEKG maxPayload=20480) after 400 at 21:45 — plane pers
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116 sid=qYWJN8MrQlI7JVuSAAB8 maxPayload=10240) after 400 at 21:45 — plane persis
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: 504→404 (2B) — origin decommissioned or route unmounted entirely; no content-bearing recovery of shared DO app 1c
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: R2 bucket uniformly 404 on root and robots.txt (28KB/27KB "Object not found" pages); no listing.
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: real origin JSON confirmed stable (200 len=75); CSP headers (Helmet) + HSTS + x-frame-options: DENY; no CF Acc
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (+ x-do-orig-status:200 + x-do-app-origin:53f39197 on /openapi.json, /api/v2/);
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping still 403 (110KB cf-mitigated); no content-method bypass.

## RANKED HYPOTHESES 2026-09-07 06:18:40 UTC
- [90] staging-alerts.rainbet.com: Engine.io v4 anonymous sid issuance enables session hijack and socket plane abuse (from art/lead_nemotron3.txt)
- [72] staging-raffles.rainbet.com/health: Staging pocket app origin leak enables full contract mapping on next WAF/route edit (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): AUTH_HELPED: POST https://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling with sid from latest handshake (oh95TnJA56TZ66eXAEKG) — attempt namespac
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 REAPPEARED (200 len=116 sid=oh95TnJA56TZ66eXAEKG maxPayload=20480) after 400 at 21:45 — plane pers
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116 sid=qYWJN8MrQlI7JVuSAAB8 maxPayload=10240) after 400 at 21:45 — plane persis
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: 504→404 (2B) — origin decommissioned or route unmounted entirely; no content-bearing recovery of shared DO app 1c
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: R2 bucket uniformly 404 on root and robots.txt (28KB/27KB "Object not found" pages); no listing.
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: real origin JSON confirmed stable (200 len=75); CSP headers (Helmet) + HSTS + x-frame-options: DENY; no CF Acc
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (+ x-do-orig-status:200 + x-do-app-origin:53f39197 on /openapi.json, /api/v2/);
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping still 403 (110KB cf-mitigated); no content-method bypass.
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: origin-reachable NestJS app on app 1ce4ff55; /docs protected by Access (302, kid 31d4206e) while /health,/api
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: origin-reachable Express app on NEW app bc240b8a-ba24-4b78-834b-423990390251; /docs 403 (5KB, non-cf-mitigate
- LEARN: ACCEPTED SCOPE-EXPANSION: staging Access gap spans 6 hostnames on app 1ce4ff55 (raffles/chat/alerts/socket/socket-services/originals-history) + app bc240b8a — p
- LEARN: REJECTED @ maintenance/clever/staging-slot-integrations: non-content (301/404/no-resolve).
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds.
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on same DO app.
- LEARN: ACCEPTED MISCONFIG @ staging-socket.rainbet.com: engine.io v4 handshake returns 400 (intermittent) but same DO app origin.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json,
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504 (down); no recovery of a content-bearing staging app observed.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-07 12:49:56 UTC
- [92] staging-alerts.rainbet.com: Engine.io v4 anonymous sid enables socket plane session hijack and event abuse (from art/lead_nemotron3.txt)
- [80] staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling: engine.io anonymous sid plane enables namespace-intended socket abuse via AUTH_HELPED probe on staging-alerts (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): AUTH_HELPED: POST https://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling with sid=oh95TnJA56TZ66eXAEKG (latest captured) — send engine.io connect
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 anonymous sid issuance persists across 8+ rounds (200, 116B, fresh sid, maxPayload=20480) on app 1ce4ff
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: NestJS app on app 1ce4ff55 origin-reachable; path-partial Access (/docs 302, all else unprotected)
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: Express app on NEW app bc240b8a-ba24-4b78-834b-423990390251 origin-reachable; /docs 403 non-cf-mitigated; no 
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: 504→404 — origin decommissioned or route unmounted
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE; scope "everything but / and /docs"; content methods WAF-closed
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping still 403; no content-method bypass observed across 8+ rounds
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: origin-reachable NestJS app on app 1ce4ff55; /docs protected by Access (302, kid 31d4206e) while /health,/api
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: origin-reachable Express app on NEW app bc240b8a-ba24-4b78-834b-423990390251; /docs 403 (5KB, non-cf-mitigate
- LEARN: ACCEPTED SCOPE-EXPANSION: staging Access gap spans 6 hostnames on app 1ce4ff55 (raffles/chat/alerts/socket/socket-services/originals-history) + app bc240b8a — p
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds.
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on same DO app.
- LEARN: ACCEPTED MISCONFIG @ staging-socket.rainbet.com: engine.io v4 handshake returns 400 (intermittent) but same DO app origin.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json,
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504 (down); no recovery of a content-bearing staging app observed.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-07 18:12:49 UTC
- [92] staging-alerts.rainbet.com: Engine.io v4 anonymous sid enables socket plane session hijack and event abuse (from art/lead_nemotron3.txt)
- [88] staging-services.rainbet.com/*: Reflected-Origin CORS + Allow-Credentials on staging-services enables cross-origin credentialed reads (from art/lead_bigpickle.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: origin-reachable NestJS app on app 1ce4ff55; /docs protected by Access (302, kid 31d4206e) while /health,/api
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: origin-reachable Express app on NEW app bc240b8a-ba24-4b78-834b-423990390251; /docs 403 (5KB, non-cf-mitigate
- LEARN: ACCEPTED SCOPE-EXPANSION: staging Access gap spans 6 hostnames on app 1ce4ff55 (raffles/chat/alerts/socket/socket-services/originals-history) + app bc240b8a — p
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds.
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on same DO app.
- LEARN: ACCEPTED MISCONFIG @ staging-socket.rainbet.com: engine.io v4 handshake returns 400 (intermittent) but same DO app origin.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json,
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: still 504 (down); no recovery of a content-bearing staging app observed.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: Cloudflare R2 public-access bucket (28KB "Object not found" page); exposure limited to known keys.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-07 21:40:13 UTC
- [95] staging-alerts.rainbet.com: Engine.io v4 anonymous sid enables socket plane session hijack and event abuse (from art/lead_nemotron3.txt)
- [82] staging-services.rainbet.com/*: staging-services reflected-Origin credentialed CORS primes ATO/CORS-read once a data route mounts (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: POST https://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling&sid=FEmR9Lfoi__QAg1PAACi with body 40/chat then 42["0","/chat"]; if ack/200+pa
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: reflects arbitrary Origin in ACAO + sets allow-credentials:true on every response (GET /health,/metrics,/api/
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 anonymous sid issuance persists across 9+ rounds (200, 116B, fresh sid, maxPayload=20480) — plane stabl
- LEARN: REJECTED MISCONFIG @ staging-monorepo.rainbet.com: /openapi.json, /api-docs, / all 404 Express (app bc240b8a); no contract exposure; CORS middleware sets allow-
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption stable (200+Allow+x-do-orig-status on /openapi.json); GET /api/v1/public/ping still 403 cf-mitig
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: origin-reachable NestJS app on app 1ce4ff55; /docs protected by Access (302, kid 31d4206e) while /health,/api
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: origin-reachable Express app on NEW app bc240b8a-ba24-4b78-834b-423990390251; /docs 403 (5KB, non-cf-mitigate
- LEARN: ACCEPTED SCOPE-EXPANSION: staging Access gap spans 6 hostnames on app 1ce4ff55 (raffles/chat/alerts/socket/socket-services/originals-history) + app bc240b8a — p
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds; 
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on same DO app.
- LEARN: ACCEPTED MISCONFIG @ staging-socket.rainbet.com: engine.io v4 handshake returns 400 (intermittent) but same DO app origin.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json,
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: 504→404 (2B) — origin decommissioned or route unmounted entirely.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: R2 bucket uniformly 404 on root and robots.txt (28KB/27KB "Object not found" pages); no listing.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-07 23:48:34 UTC
- [95] staging-alerts.rainbet.com: Engine.io v4 anonymous sid enables socket plane session hijack and event abuse (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: origin-reachable NestJS app on app 1ce4ff55; /docs protected by Access (302, kid 31d4206e) while /health,/api
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: origin-reachable Express app on NEW app bc240b8a-ba24-4b78-834b-423990390251; /docs 403 (5KB, non-cf-mitigate
- LEARN: ACCEPTED SCOPE-EXPANSION: staging Access gap spans 6 hostnames on app 1ce4ff55 (raffles/chat/alerts/socket/socket-services/originals-history) + app bc240b8a — p
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — {"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-r
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds; 
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on same DO app.
- LEARN: ACCEPTED MISCONFIG @ staging-socket.rainbet.com: engine.io v4 handshake returns 400 (intermittent) but same DO app origin.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json,
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: 504→404 (2B) — origin decommissioned or route unmounted entirely.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: R2 bucket uniformly 404 on root and robots.txt (28KB/27KB "Object not found" pages); no listing.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-08 04:14:08 UTC

## RANKED HYPOTHESES 2026-09-08 08:54:05 UTC
- [95] staging-alerts.rainbet.com: Engine.io v4 anonymous sid enables socket plane session hijack and event abuse (from art/lead_nemotron3.txt)
- [84] staging-services.rainbet.com/*: staging-services reflected-Origin credentialed CORS primes ATO/CORS-read once a data route mounts (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://staging-services.rainbet.com/api/v1/users, /api/v1/balance, /api/v1/config, /api/v1/games, /api/v1/wallet, /api/v2/ with Origin:https://evil.
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: reflects arbitrary Origin in ACAO + sets allow-credentials:true on every response (GET /health,/metrics,/api/
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 anonymous sid issuance persists across 10+ rounds — plane stable; intermittent 400↔200 toggle.
- LEARN: REJECTED MISCONFIG @ staging-monorepo.rainbet.com: /health error body changed to Express format (69B) but still 404; /openapi.json, /api-docs all 404; no contra
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping still 403 (110KB cf-mitigated) — no content-method bypass across 10+ rounds.
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: origin-reachable NestJS app on app 1ce4ff55; /docs protected by Access (302, kid 31d4206e) while /health,/api
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: origin-reachable Express app on NEW app bc240b8a-ba24-4b78-834b-423990390251; /docs 403 (5KB, non-cf-mitigate
- LEARN: ACCEPTED SCOPE-EXPANSION: staging Access gap spans 6 hostnames on app 1ce4ff55 (raffles/chat/alerts/socket/socket-services/originals-history) + app bc240b8a — p
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — {"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-r
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds; 
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on same DO app.
- LEARN: ACCEPTED MISCONFIG @ staging-socket.rainbet.com: engine.io v4 handshake returns 400 (intermittent) but same DO app origin.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json,
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: 504→404 (2B) — origin decommissioned or route unmounted entirely.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: R2 bucket uniformly 404 on root and robots.txt (28KB/27KB "Object not found" pages); no listing.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

## RANKED HYPOTHESES 2026-09-08 13:46:24 UTC
- [84] staging-services.rainbet.com/*: staging-services reflected-Origin credentialed CORS primes ATO/CORS-read once a data route mounts (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://staging-services.rainbet.com/api/v1/users, /api/v1/balance, /api/v1/config, /api/v1/games, /api/v1/wallet, /api/v2/ with Origin:https://evil.
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: reflects arbitrary Origin in ACAO + sets allow-credentials:true on every response (GET /health,/metrics,/api/
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 anonymous sid issuance persists across 10+ rounds — plane stable; intermittent 400↔200 toggle.
- LEARN: REJECTED MISCONFIG @ staging-monorepo.rainbet.com: /health error body changed to Express format (69B) but still 404; /openapi.json, /api-docs all 404; no contra
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping still 403 (110KB cf-mitigated) — no content-method bypass across 10+ rounds.

## RANKED HYPOTHESES 2026-09-08 17:38:14 UTC
- [95] staging-alerts.rainbet.com: Engine.io v4 anonymous sid enables socket plane session hijack and event abuse (from art/lead_nemotron3.txt)
- [84] staging-services.rainbet.com/*: staging-services credentialed CORS reflector becomes RCE/data-read once any route returns non-404 (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=polling (fresh sid), POST 42["0","/chat"], then GET poll 40ms/500ms/1s to catch any eve
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: origin-reachable NestJS app on app 1ce4ff55; /docs protected by Access (302, kid 31d4206e) while /health,/api
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: origin-reachable Express app on NEW app bc240b8a-ba24-4b78-834b-423990390251; /docs 403 (5KB, non-cf-mitigate
- LEARN: ACCEPTED SCOPE-EXPANSION: staging Access gap spans 6 hostnames on app 1ce4ff55 (raffles/chat/alerts/socket/socket-services/originals-history) + app bc240b8a — p
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — {"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-r
- LEARN: ACCEPTED MISCONFIG @ staging-alerts.rainbet.com: engine.io v4 continues issuing fresh anonymous sids unprotected (app 1ce4ff55) — plane persists across rounds; 
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200 len=116) after 400 — plane persists on same DO app.
- LEARN: ACCEPTED MISCONFIG @ staging-socket.rainbet.com: engine.io v4 handshake returns 400 (intermittent) but same DO app origin.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption CONFIRMED STABLE (200 + Allow + x-do-orig-status on /api/v2/, /graphql, /swagger, /openapi.json,
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: single OPTIONS /openapi.json 403 was a transient rate-limit/bot-management burst (retry → 200); NOT a rule closure.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: drift CLOSED (302) this round; enforcement remains intermittent-to-default-deny.
- LEARN: REJECTED AUTH @ staging-originals.rainbet.com: 504→404 (2B) — origin decommissioned or route unmounted entirely.
- LEARN: REJECTED MISCONFIG @ staging-blog.rainbet.com: 530/1016 is a CF origin-DNS error, not a takeoverable dangling host.
- LEARN: ACCEPTED MISCONFIG @ staging-cdn.rainbet.com: R2 bucket uniformly 404 on root and robots.txt (28KB/27KB "Object not found" pages); no listing.
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: POST-with-JSON bypass hypothesis false — POST /api/v1/public/ping and POST /api/v1/ both return 403 cf-mitigated challenge
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: cf-mitigated: challenge header present on all 403 responses — WAF configuration consistent across subdomains (api, www).
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all tested paths — no unchallenged surface.

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

## RANKED HYPOTHESES 2026-09-08 20:21:32 UTC
- [95] staging-alerts.rainbet.com: Engine.io v4 anonymous sid enables socket plane session hijack and event abuse (from art/lead_nemotron3.txt)
- [84] staging-services.rainbet.com/*: staging-services credentialed CORS reflector becomes data-read once any route returns non-404 (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET /api/v1/status, /api/v2/docs, /graphql, /api/v1/auth/health on api.rainbet.com + OPTIONS /openapi.json (watch for any origin 2xx/4xx/5xx vs 403 — WAF
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

## RANKED HYPOTHESES 2026-09-08 22:46:28 UTC

## RANKED HYPOTHESES 2026-09-09 01:15:30 UTC
- [95] staging-alerts.rainbet.com: Engine.io v4 anonymous sid enables socket plane session hijack and event abuse across 6 staging hostnames (from art/lead_nemotron3.txt)
- [65] api.rainbet.com: api WAF content-open on operator edit cycle (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
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
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — a
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector now also emits access-control-expose-headers:Cf-Mitigated alongside ACAO-reflect + allow-crede
- LEARN: REJECTED MISCONFIG @ staging-monorepo.rainbet.com: /docs 403 is now the standard 5485B CF WAF block page, not a non-cf-mitigated origin 403 — WAF front now unif
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json exemption STABLE this round (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); scope "
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

## RANKED HYPOTHESES 2026-09-09 06:15:59 UTC
- [95] staging-alerts.rainbet.com: Engine.io v4 anonymous sid enables socket plane session hijack and event abuse across 6 staging hostnames (from art/lead_nemotron3.txt)
- [62] staging-alerts.rainbet.com/socket.io/?EIO=4: staging-alerts.rainbet.com: engine.io v4 WebSocket namespace injection yields authenticated event stream via persistent anonymous session (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET (e.g., sid=h-m0Begj4fqrqlaZAAvf) — 
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 3 paths (/health, /api/v1/users, OPTIONS /api/v1) — reflects arbitrary Origin in 
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — NestJS runs on Express but typically sets its ow
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 anonymous sid issuance persists (10+ rounds, fresh sid=h-m0Begj4fqrqlaZAAvf each request); plane stable
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: engine.io v4 anonymous sid issuance persists (sid=29N8K9IZ1ZtBSOayAAAT, maxPayload=10240); plane stable on same DO app
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: origin JSON /health stable (75B, x-do-orig-status:200, full CSP+HSTS+XFO headers, no cf-mitigated, no CF Acces
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: content GET 403 still 5485B block with no cf-mitigated — WAF rule change from 110KB→5485B observed 2026-09-09 persists; no
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 3 paths (/health, /api/v1/users, OPTIONS /api/v1) — reflects arbitrary Origin + a
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: content GET 403 still 5485B block with no cf-mitigated; OPTIONS still 200 with x-do-orig-status — WAF state unchanged from
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: origin JSON /health stable (75B, x-do-orig-status:200, full CSP+HSTS+XFO, no cf-mitigated, no CF Access)
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 anonymous sid issuance persists but socket.io enforces auth on namespace connect — transport-layer gap,
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
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — a
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector now also emits access-control-expose-headers:Cf-Mitigated alongside ACAO-reflect + allow-crede

## RANKED HYPOTHESES 2026-09-09 11:42:50 UTC
- [90] staging-raffles.rainbet.com: Staging pocket app (app 1ce4ff55) exposes full API contract via unprotected /health and /api/* endpoints on 6 hostnames (from art/lead_nemotron3.txt)
- [78] staging-chat.rainbet.com/socket.io/?EIO=4: staging-chat unauth namespace join yields data-capable session on business channels (from art/lead_bigpickle.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-alerts.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-alerts.rainbet.com/
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: origin-reachable Express app on app 1ce4ff55; /docs protected by Access (302, kid 31d4206e) while /health,/ap
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
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — a
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector now also emits access-control-expose-headers:Cf-Mitigated alongside ACAO-reflect + allow-crede
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er

## RANKED HYPOTHESES 2026-09-09 15:27:15 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root namespace accepts unauthenticated CONNECT enabling full session establishment (from art/lead_nemotron3.txt)
- [78] staging-chat.rainbet.com/socket.io/?EIO=4: staging-chat unauthenticated socket.io session intercepts server-push events on business channels (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: POST `https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling` with `Content-Type: text/plain` body `40` (engine.io connect, root namespace) 
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-chat.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-chat.rainbet.com/sock
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 3 paths (/health, /api/v1/users, OPTIONS /api/v1) — reflects arbitrary Origin + a
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: content GET 403 still 5485B block with no cf-mitigated; OPTIONS still 200 with x-do-orig-status — WAF state unchanged from
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: origin JSON /health stable (75B, x-do-orig-status:200, full CSP+HSTS+XFO, no cf-mitigated, no CF Access)
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 anonymous sid issuance persists but socket.io enforces auth on namespace connect — transport-layer gap,
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: origin-reachable Express app on app 1ce4ff55; /docs protected by Access (302, kid 31d4206e) while /health,/ap
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 3 paths (/health, /api/v1/users, OPTIONS /api/v1) — reflects arbitrary Origin in 
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — a
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs 403 is now the standard 5485B CF WAF block page, not a non-cf-mitigated origin 403 — WAF front now unif
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — {"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-r
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e

## RANKED HYPOTHESES 2026-09-09 18:45:51 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root namespace accepts unauthenticated CONNECT enabling full session establishment (from art/lead_nemotron3.txt)
- [78] staging-chat.rainbet.com/socket.io/?EIO=4: staging-chat unauthenticated socket.io session intercepts server-push events on business channels (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: POST `https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling` with `Content-Type: text/plain` body `40` (engine.io connect, root namespace) 
- NEXT(hypotheses-nemotron3.txt): PROBE: WebSocket upgrade to wss://staging-chat.rainbet.com/socket.io/?EIO=4&transport=websocket with sid captured from GET https://staging-chat.rainbet.com/sock
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 3 paths (/health, /api/v1/users, OPTIONS /api/v1) — reflects arbitrary Origin + a
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: content GET 403 still 5485B block with no cf-mitigated; OPTIONS still 200 with x-do-orig-status — WAF state unchanged from
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: origin JSON /health stable (75B, x-do-orig-status:200, full CSP+HSTS+XFO, no cf-mitigated, no CF Access)
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 anonymous sid issuance persists but socket.io enforces auth on namespace connect — transport-layer gap,
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: origin-reachable Express app on app 1ce4ff55; /docs protected by Access (302, kid 31d4206e) while /health,/ap
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 3 paths (/health, /api/v1/users, OPTIONS /api/v1) — reflects arbitrary Origin in 
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — a
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs 403 is now the standard 5485B CF WAF block page, not a non-cf-mitigated origin 403 — WAF front now unif
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — {"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-r
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e

## RANKED HYPOTHESES 2026-09-09 21:36:53 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root namespace accepts unauthenticated CONNECT enabling full session establishment (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 3 paths (/health, /api/v1/users, OPTIONS /api/v1) — reflects arbitrary Origin in 
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — a
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs 403 is now the standard 5485B CF WAF block page, not a non-cf-mitigated origin 403 — WAF front now unif
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — {"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-r
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e

## RANKED HYPOTHESES 2026-09-09 23:35:01 UTC
- [82] staging-chat.rainbet.com/socket.io/?EIO=4: staging-chat unauthenticated socket.io session receives server-push events on business namespaces (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: WebSocket upgrade `wss://staging-chat.rainbet.com/socket.io/?EIO=4&transport=websocket&sid=<sid-from-GET-handshake>`; after CONNECT send `40{"0":"/raffle
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 4th path /api/v1/games (ACAO-reflect + credentials + expose Cf-Mitigated, 404 Exp
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json stable (200, Allow, x-do-orig-status:200, app 53f39197); content GET 5484B no cf-mitigated — WAF sta

## RANKED HYPOTHESES 2026-09-10 01:34:53 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [82] staging-chat.rainbet.com/socket.io/?EIO=4: staging-chat unauthenticated socket.io session receives server-push events on business namespaces (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: WebSocket upgrade `wss://staging-chat.rainbet.com/socket.io/?EIO=4&transport=websocket&sid=<sid-from-GET-handshake>`; after CONNECT send `40{"0":"/raffle
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 4th path /api/v1/games (ACAO-reflect + credentials + expose Cf-Mitigated, 404 Exp
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json stable (200, Allow, x-do-orig-status:200, app 53f39197); content GET 5484B no cf-mitigated — WAF sta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 4 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games) — reflects arbit
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — a
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs 403 is now the standard 5485B CF WAF block page, not a non-cf-mitigated origin 403 — WAF front now unif
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — {"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-r
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e

## RANKED HYPOTHESES 2026-09-10 06:50:39 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [87] staging-chat.rainbet.com/socket.io: staging-chat anonymous socket registration on business namespaces — session establishment fully proven; only event reception unverified (from art/lead_bigpickle.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 4 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games) — reflects arbit
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — a
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs 403 is now the standard 5485B CF WAF block page, not a non-cf-mitigated origin 403 — WAF front now unif
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — {"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-r
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e

## RANKED HYPOTHESES 2026-09-10 11:56:05 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [87] staging-chat.rainbet.com/socket.io: staging-chat anonymous socket event reception — sole unverified link in proven bypass chain (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: WebSocket upgrade `wss://staging-chat.rainbet.com/socket.io/?EIO=4&transport=websocket&sid=<sid-from-GET-handshake>`; after CONNECT send `40{"0":"/raffle
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root + business namespaces accept unauthenticated CONNECT; session establishment fully proven across root+/r
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector 5/5 paths confirmed; latent until 2xx mount.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption stable; content GET WAF frozen at 5485B block.
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 4 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games) — reflects arbit
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — a
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs 403 is now the standard 5485B CF WAF block page, not a non-cf-mitigated origin 403 — WAF front now unif
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — {"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-r
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e

## RANKED HYPOTHESES 2026-09-10 16:15:44 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [88] staging-chat.rainbet.com/socket.io: staging-chat anonymous socket event reception — sole unverified link in proven bypass chain (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: WebSocket upgrade `wss://staging-chat.rainbet.com/socket.io/?EIO=4&transport=websocket&sid=<fresh-sid-from-GET-(engine.io polling sid; GET first will yie
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED MISCONFIG @ staging-chat.rainbet.com: engine.io handshake sets access-control-allow-credentials:true + vary:Origin with NO ACAO reflect (evil origin ab
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: /health sets access-control-allow-credentials:true + vary:Origin, no ACAO reflect — CORS credentials enabled o
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: content GET body drift 5485→5483B is page-length jitter (still plain 403 block, no cf-mitigated); NOT a WAF rule edit — no
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 4 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games) — reflects arbit
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — a
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs 403 is now the standard 5485B CF WAF block page, not a non-cf-mitigated origin 403 — WAF front now unif
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — {"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-r
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e

## RANKED HYPOTHESES 2026-09-10 19:15:56 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 4 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games) — reflects arbit
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 changed to 5485B plain WAF block WITH NO cf-mitigated header (was 110KB managed challenge with header) — a
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs 403 is now the standard 5485B CF WAF block page, not a non-cf-mitigated origin 403 — WAF front now unif
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — {"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-r
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e

## RANKED HYPOTHESES 2026-09-10 21:46:40 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [52] api.rainbet.com/*: api.rainbet.com WAF content-method exposure during operator edit cycles (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: WebSocket upgrade `wss://staging-chat.rainbet.com/socket.io/?EIO=4&transport=websocket&sid=<fresh-sid>` (GET polling sid first, e.g. current pattern yiel
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping 403 len=5485 this round (was 5484/5483) — body drift continues to track page-length jitter, not WA
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: /health evil-origin 404/33B continues ACAO-reflect + allow-credentials:true + access-control-expose-headers:C
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: EIO4 polling 200/116B anonymous sid + vary:Origin + credentials:true (no ACAO reflect) — CORS credentials + anonymous 
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 4 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games) — reflects arbit
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 (previously 5
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs returns full CF managed challenge (not 5485B block) — WAF front state fluctuates on app bc240b8a
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e

## RANKED HYPOTHESES 2026-09-10 23:54:05 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [88] staging-chat.rainbet.com/socket.io: staging-chat anonymous socket plane delivers business events without auth (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: On staging-chat, GET `https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling` (fresh 116B sid), WS-upgrade `wss://staging-chat.rainbet.com/s
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 4 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games) — reflects arbit
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 (previously 5
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs returns full CF managed challenge (not 5485B block) — WAF front state fluctuates on app bc240b8a
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e

## RANKED HYPOTHESES 2026-09-11 03:59:31 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [88] staging-chat.rainbet.com/socket.io: staging-chat anonymous socket plane delivers business events without auth (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: On staging-chat, GET `https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling` (fresh 116B sid), WS-upgrade `wss://staging-chat.rainbet.com/s
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping 403 len=5485 this round (was 5484/5483) — body drift continues to track page-length jitter, not WA
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: /health evil-origin 404/33B continues ACAO-reflect + allow-credentials:true + access-control-expose-headers:C
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: EIO4 polling 200/116B anonymous sid + vary:Origin + credentials:true (no ACAO reflect) — CORS credentials + anonymous 
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 (previously 5
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs returns full CF managed challenge (not 5485B block) — WAF front state fluctuates on app bc240b8a.
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 4 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games) — reflects arbit
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 (previously 5
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs returns full CF managed challenge (not 5485B block) — WAF front state fluctuates on app bc240b8a
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e

## RANKED HYPOTHESES 2026-09-11 09:02:41 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [88] staging-chat.rainbet.com/socket.io: staging-chat anonymous socket plane delivers business events without auth (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: On staging-chat, GET `https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling` (fresh 116B sid), WS-upgrade `wss://staging-chat.rainbet.com/s
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json stable (200, Allow, x-do-orig-status:200, app 53f39197); content GET 403 fully blocked — WAF state f
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: /health evil-origin 404/33B continues ACAO-reflect + allow-credentials:true + access-control-expose-headers:C
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: EIO4 polling 200/116B anonymous sid + vary:Origin + credentials:true (no ACAO reflect) — CORS credentials + anonymous 
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: content GET body drift 5485→5483B is page-length jitter (still plain 403 block, no cf-mitigated); NOT a WAF rule edit — no
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 (prev
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs returns full CF managed challenge (not 5485B block) — WAF front state fluctuates on app bc240b8a
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 4 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games) — reflects arbit
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 (previously 5
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs returns full CF managed challenge (not 5485B block) — WAF front state fluctuates on app bc240b8a
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e

## RANKED HYPOTHESES 2026-09-11 13:31:43 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [88] staging-chat.rainbet.com/socket.io: staging-chat anonymous socket plane delivers business events without auth (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: staging-chat.rainbet.com engine.io plane CONFIRMED RECOVERED (200, fresh anonymous sids, 2/2 probes). On staging-chat, GET `https://staging-chat.rainbet.
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: engine.io v4 REAPPEARED (200, 116B, fresh sids JRlTjH5zOotW2WjeAAAL + vUVEIzB3mtpSbKNyAAAM, maxPayload=10240) after 40
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector now confirmed on 6 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games, /api/v1/prof
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json STABLE (200 + Allow:POST,OPTIONS,HEAD,GET + x-do-orig-status:200 + app 53f39197); content GET 403 fu
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 stable 200/116B (sid=aOncFcuyVOcVjyKVAAJi, maxPayload=20480) — plane persists, serves as control provin
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 (prev
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs returns full CF managed challenge (not 5485B block) — WAF front state fluctuates on app bc240b8a
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 4 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games) — reflects arbit
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: content GET 403 reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 (previously 5
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs returns full CF managed challenge (not 5485B block) — WAF front state fluctuates on app bc240b8a
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS blanket exemption STABLE on /openapi.json (200 + Allow + x-do-orig-status:200 + x-do-app-origin:53f39197); /docs e

## RANKED HYPOTHESES 2026-09-11 17:17:48 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 (prev
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs returns full CF managed challenge (not 5485B block) — WAF front state fluctuates on app bc240b8a
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 6 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games, /api/v1/profile,
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json STABLE (200 + Allow:POST,OPTIONS,HEAD,GET + x-do-orig-status:200 + x-do-app-origin:53f39197); conten
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 stable 200/116B (sid=aOncFcuyVOcVjyKVAAJi, maxPayload=20480) — plane persists, serves as control provin
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 (prev
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs returns full CF managed challenge (not 5485B block) — WAF front state fluctuates on app bc240b8a
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 6 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games, /api/v1/profile,
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json STABLE (200 + Allow:POST,OPTIONS,HEAD,GET + x-do-orig-status:200 + x-do-app-origin:53f39197); conten
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 stable 200/116B (sid=aOncFcuyVOcVjyKVAAJi, maxPayload=20480) — plane persists, serves as control provin

## RANKED HYPOTHESES 2026-09-11 20:03:26 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [45] staging.rainbet.com: staging Cloudflare Access JWT parsing weakness (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET `https://staging.rainbet.com/.well-known/cloudflare-access-protected-resource/` — retrieve CF Access protected resource metadata (may expose policy d
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: CF block page present but `cf-mitigated` header absent (unlike www.rainbet.com) — different CF WAF configurations per subd
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: CF Access JWT contains `auth_status: NONE` and `is_wrap: false` — Access policy may be permissive or misconfigured.
- LEARN: REJECTED dead subdomains (17/20): No DNS resolution or HTTP service — removed from active attack surface until re-checked.
- LEARN: REJECTED MISCONFIG @ staging.rainbet.com: Cloudflare Access Zero Trust is properly configured (default-deny, JWT metadata visible but no bypass); no evidence of
- LEARN: REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all paths including static assets; no unchallenged surface discovered passively
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 (prev
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs returns full CF managed challenge (not 5485B block) — WAF front state fluctuates on app bc240b8a
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 6 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games, /api/v1/profile,
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json STABLE (200 + Allow:POST,OPTIONS,HEAD,GET + x-do-orig-status:200 + x-do-app-origin:53f39197); conten
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 stable 200/116B (sid=aOncFcuyVOcVjyKVAAJi, maxPayload=20480) — plane persists, serves as control provin

## RANKED HYPOTHESES 2026-09-11 22:24:45 UTC
- [95] staging-chat.rainbet.com/socket.io: Unauthenticated socket.io plane on staging-chat (session establishment proven, event reception unverified) (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: staging-chat.rainbet.com — capture fresh EIO4 sid (`/socket.io/?EIO=4&transport=polling`), WebSocket-upgrade with that sid, send `40/raffles,` CONNECT (n

## RANKED HYPOTHESES 2026-09-12 00:41:24 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [70] staging-chat.rainbet.com/socket.io: staging-chat root namespace anonymous socket session (WS transport) — business namespaces regressed (from art/lead_bigpickle.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 (prev
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs returns full CF managed challenge (not 5485B block) — WAF front state fluctuates on app bc240b8a
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 6 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games, /api/v1/profile,
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json STABLE (200 + Allow:POST,OPTIONS,HEAD,GET + x-do-orig-status:200 + x-do-app-origin:53f39197); conten
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 stable 200/116B (sid=aOncFcuyVOcVjyKVAAJi, maxPayload=20480) — plane persists, serves as control provin

## RANKED HYPOTHESES 2026-09-12 05:08:41 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [70] staging-chat.rainbet.com/socket.io: staging-chat root namespace anonymous socket session (WS transport) — business namespaces regressed (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: api.rainbet.com churn-window sweep — GET /robots.txt, /.well-known/security.txt, /health, /api/v1/public/config, /api/v1/public/ping (0.5 rps, 5 requests
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: `OPTIONS /openapi.json%2f..%2f` passes WAF to origin and returns 404 (`x-do-orig-status:404`) vs blanket 200 on plain pref
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: Allow header uniform (`HEAD,GET,POST,OPTIONS`) across 10 probed business/admin paths — no route-differential method finger
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: 6 encoded GET variants (double-encoded path, `%2e%2e`, trailing `%2f`, mixed-case) all 403@5484B — no content-method WAF b
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: WAF frozen at plain-block 5484B (no cf-mitigated) + OPTIONS exemption fully stable — no operator churn window observed thi
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 (prev
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs returns full CF managed challenge (not 5485B block) — WAF front state fluctuates on app bc240b8a
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 6 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games, /api/v1/profile,
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json STABLE (200 + Allow:POST,OPTIONS,HEAD,GET + x-do-orig-status:200 + x-do-app-origin:53f39197); conten
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 stable 200/116B (sid=aOncFcuyVOcVjyKVAAJi, maxPayload=20480) — plane persists, serves as control provin

## RANKED HYPOTHESES 2026-09-12 09:29:38 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [72] staging-chat.rainbet.com/socket.io: staging-chat socket.io namespace registry enumeration via EIO4 polling sid → WS upgrade → namespace probe (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: staging-chat.rainbet.com — capture fresh EIO4 sid via `GET /socket.io/?EIO=4&transport=polling`, WebSocket upgrade with that sid, send root `40` CONNECT 
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS `/openapi.json%2f..%2f` passes WAF to origin (404, x-do-orig-status:404) vs blanket 200 on plain preflights — orig
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: Allow header uniform across 10 paths — no route-differential method fingerprint via OPTIONS exemption
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: 6 encoded GET variants all 403@5484B — no content-method WAF bypass this round
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: WAF frozen at plain-block 5484B + OPTIONS exemption fully stable — no churn window this round
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts regressed to 44 Invalid namespace on WS transport — prior namespace join no longer reproducible; ro
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to 5485B plain WAF block (no cf-mitigated header) from 110KB managed challenge — active o
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs flipped from 5485B CF block to full CF managed challenge (110KB) — WAF front state fluctuates on app bc
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 6 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games, /api/v1/profile,
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json STABLE (200 + Allow:POST,OPTIONS,HEAD,GET + x-do-orig-status:200 + x-do-app-origin:53f39197); conten
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 stable 200/116B (sid=aOncFcuyVOcVjyKVAAJi, maxPayload=20480) — plane persists, serves as control provin

## RANKED HYPOTHESES 2026-09-12 13:17:00 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [65] staging-chat.rainbet.com/socket.io: staging-chat root namespace anonymous session yields live event egress (missing link) (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: staging-chat.rainbet.com — EIO4 poll sids → WS upgrade → exact `40` CONNECT (no jsonrpc body) → 60s passive listen on root namespace; log every frame and
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to 5485B plain WAF block (no cf-mitigated header) from 110KB managed challenge — active o
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs flipped from 5485B CF block to full CF managed challenge (110KB) — WAF front state fluctuates on app bc
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 6 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games, /api/v1/profile,
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json STABLE (200 + Allow:POST,OPTIONS,HEAD,GET + x-do-orig-status:200 + x-do-app-origin:53f39197); conten
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 stable 200/116B (sid=aOncFcuyVOcVjyKVAAJi, maxPayload=20480) — plane persists, serves as control provin

## RANKED HYPOTHESES 2026-09-12 16:36:26 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [65] staging-chat.rainbet.com/socket.io: staging-chat root namespace anonymous session yields live event egress (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: staging-chat.rainbet.com — EIO4 poll sid → WS upgrade → send exact `40` → 60s passive listen on root namespace; log every frame and time-to-close; then e
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: root namespace anonymous session yields engine.io + socket.io CONNECT — egress remains unproven across 4+ listen round
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector persists on 6 paths (all 404/33B) — still no 2xx mount; conditional HIGH.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: WAF churn confirmed live (110KB ↔ 5485B) + decode-dependent OPTIONS oracle — no exploit path; monitoring only.
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts regressed to 44 on WS — namespace registry transport-dependent or instance-routed; polling sid → en
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to 5485B plain WAF block (no cf-mitigated header) from 110KB managed challenge — active o
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs flipped from 5485B CF block to full CF managed challenge (110KB) — WAF front state fluctuates on app bc
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 6 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games, /api/v1/profile,
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json STABLE (200 + Allow:POST,OPTIONS,HEAD,GET + x-do-orig-status:200 + x-do-app-origin:53f39197); conten
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 stable 200/116B (sid=aOncFcuyVOcVjyKVAAJi, maxPayload=20480) — plane persists, serves as control provin

## RANKED HYPOTHESES 2026-09-12 18:55:41 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [65] staging-chat.rainbet.com/socket.io: staging-chat root namespace anonymous session yields live event egress (missing link) (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: staging-chat.rainbet.com — capture fresh EIO4 sid via `GET /socket.io/?EIO=4&transport=polling`, WebSocket upgrade with that sid, send root `40` CONNECT 
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS `/openapi.json%2f..%2f` passes WAF to origin (404, x-do-orig-status:404) vs blanket 200 on plain preflights — orig
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: Allow header uniform across 10 paths — no route-differential method fingerprint via OPTIONS exemption
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: 6 encoded GET variants all 403@5484B — no content-method WAF bypass this round
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: WAF frozen at plain-block 5484B + OPTIONS exemption fully stable — no churn window this round
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts regressed to 44 Invalid namespace on WS transport — prior namespace join no longer reproducible; ro
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: root namespace anonymous session yields engine.io + socket.io CONNECT — egress remains unproven across 4+ listen round
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector persists on 6 paths (all 404/33B) — still no 2xx mount; conditional HIGH.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: WAF churn confirmed live (110KB ↔ 5485B) + decode-dependent OPTIONS oracle — no exploit path; monitoring only.
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts regressed to 44 on WS — namespace registry transport-dependent or instance-routed; polling sid → en
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS `/openapi.json%2f..%2f` passes WAF to origin (404, x-do-orig-status:404) vs blanket 200 on plain preflights — orig
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: Allow header uniform across 10 paths — no route-differential method fingerprint via OPTIONS exemption
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: 6 encoded GET variants all 403@5484B — no content-method WAF bypass this round
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: WAF frozen at plain-block 5484B + OPTIONS exemption fully stable — no churn window this round
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts regressed to 44 Invalid namespace on WS transport — prior namespace join no longer reproducible; ro
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: root namespace anonymous session yields engine.io + socket.io CONNECT — egress remains unproven across 4+ listen round
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector persists on 6 paths (all 404/33B) — still no 2xx mount; conditional HIGH.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: WAF churn confirmed live (110KB ↔ 5485B) + decode-dependent OPTIONS oracle — no exploit path; monitoring only.
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts regressed to 44 on WS — namespace registry transport-dependent or instance-routed; polling sid → en
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: root namespace anonymous session yields engine.io + socket.io CONNECT — egress remains unproven across 4+ listen round
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector persists on 6 paths (all 404/33B) — still no 2xx mount; conditional HIGH.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: WAF churn confirmed live (110KB ↔ 5485B) + decode-dependent OPTIONS oracle — no exploit path; monitoring only.
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts regressed to 44 on WS — namespace registry transport-dependent or instance-routed; polling sid → en
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: root `40` CONNECT ACKs anonymous socket-level sid (u3zOZrESYiu_kKBCAAAE, 5th round) on fresh EIO4 sid; server sends en
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector now on 6/6 incl `/` root — all 404/33B, no 2xx across 13+ rounds.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: 2 template classes are block-FLAVORS (static=4545B pure block no JS; API=5483B block+challenge bootstrap; 110KB=full chall
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs flipped 110KB challenge -> 5483B plain block (app bc240b8a) — front churn live.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Access gap CLOSED (302) this round; Access 302 block page reflects evil Origin + allow-credentials:true — pre-auth, CORS-ne
- LEARN: REJECTED (methodology) @ staging-chat.rainbet.com: NS enum reads across rounds are invalid when performed after server close — /raffles /alerts "44/ACK" flip cl
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Access gap CLOSED (302) this round; Access 302 block page reflects evil Origin + allow-credentials:true — pre-auth, CORS-ne
- LEARN: REJECTED (methodology) @ staging-chat.rainbet.com: NS enum reads across rounds are invalid when performed after server close — /raffles /alerts "44/ACK" flip cl
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: root `40` CONNECT ACKs anonymous socket-sid (5th round); server pings then closes because client never pongs — all pri
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector on 6/6 incl `/` root, all 404/33B, no 2xx across 13+ rounds.
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: two template classes are block flavors (static 4545B pure block; API 5483B block+bootstrap; 110KB full challenge); both OP
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs flipped to 5483B plain block (app bc240b8a) — front churn live.
- LEARN: ACCEPTED AUTH @ staging.rainbet.com: Access gap CLOSED (302); Access 302 reflects evil Origin + credentials:true — pre-auth, CORS-neutral.
- LEARN: REJECTED (methodology) @ staging-chat.rainbet.com: post-close NS enum reads are invalid — /raffles /alerts "44/ACK" flip claims require enum-before-listen to be
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to 5485B plain WAF block (no cf-mitigated header) from 110KB managed challenge — active o
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs flipped from 5485B CF block to full CF managed challenge (110KB) — WAF front state fluctuates on app bc
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 6 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games, /api/v1/profile,
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json STABLE (200 + Allow:POST,OPTIONS,HEAD,GET + x-do-orig-status:200 + x-do-app-origin:53f39197); conten
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 stable 200/116B (sid=aOncFcuyVOcVjyKVAAJi, maxPayload=20480) — plane persists, serves as control provin

## RANKED HYPOTHESES 2026-09-12 21:21:42 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to 5485B plain WAF block (no cf-mitigated header) from 110KB managed challenge — active o
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs flipped from 5485B CF block to full CF managed challenge (110KB) — WAF front state fluctuates on app bc
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: /raffles + /alerts namespaces ack unauthenticated connect (`40{"sid":...}`, fresh socket-level sid each) on anonymous 
- LEARN: REJECTED AUTH @ staging-alerts.rainbet.com: socket.io root namespace REJECTS unauthenticated CONNECT (`40{}` and `40{"token":"fake..."}`) with `44{"message":"er
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 6 paths (/health, /api/v1/users, OPTIONS /api/v1, /api/v1/games, /api/v1/profile,
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: x-powered-by changed to Express (was NestJS on 2026-09-07) — possible framework config change or downgrade on
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS /openapi.json STABLE (200 + Allow:POST,OPTIONS,HEAD,GET + x-do-orig-status:200 + x-do-app-origin:53f39197); conten
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 stable 200/116B (sid=aOncFcuyVOcVjyKVAAJi, maxPayload=20480) — plane persists, serves as control provin

## RANKED HYPOTHESES 2026-09-12 23:16:27 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root namespace accepts unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [20] staging-chat.rainbet.com/socket.io: staging-chat root anonymous session yields live event egress (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: staging-services.rainbet.com — passive GET sweep with `Origin: https://evil.example` at ~1 rps over /api/v1/public/config, /api/v1/health, /api/v1/public
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then POST https://staging-chat.rainbet.com/socket.io/?E
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 confi
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs flipped from 5485B CF block to full CF managed challenge (110KB) — WAF front state fluctuates on app bc
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 6 paths incl `/` root — reflects arbitrary Origin + allow-credentials:true + acce
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 stable 200/116B (fresh sid, maxPayload=20480) — plane persists, serves as control proving same-DO-app a
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: 6 encoded GET variants (double-encoded path, `%2e%2e`, trailing `%2f`, mixed-case) all 403@5484B — no content-method WAF b

## RANKED HYPOTHESES 2026-09-13 01:14:17 UTC
- [95] staging-chat.rainbet.com/socket.io/: staging-chat socket.io root + business namespaces accept unauthenticated CONNECT enabling full session establishment and event emission (from art/lead_nemotron3.txt)
- [40] api.rainbet.com: api per-class GET gap during WAF churn window (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: api.rainbet.com class-pair watch at 0.3 rps — GET /openapi.json (API-class), GET /robots.txt (static-class), GET /api/v1/public/ping, OPTIONS /openapi.js
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://staging-chat.rainbet.com/socket.io/?EIO=4&transport=polling to capture engine.io sid, then WebSocket upgrade to wss://staging-chat.rainbet.co
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: anonymous root CONNECT ACK persists via polling (fresh socket sid 1gTyjOcJUOJ6WXh9AAAh, live 2026-09-13) while staging
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: OPTIONS exemption covers BOTH path classes (OPTIONS /robots.txt → 200 x-do-orig-status:200, static class) — blanket prefli
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: WAF is path-pattern (docs/.git → 403 block; all other paths origin to bare Express 404 on 22 routes) — origin
- LEARN: ACCEPTED MISCONFIG @ www.rainbet.com: production front also flipped to 5484B plain-block template — the plain-block mode is now fleet-wide (api/www/monorepo), c
- LEARN: REJECTED (methodology) @ staging-chat.rainbet.com: WS-transport `40` close-on-connect is the missing `2probe/3probe/5` upgrade exchange, NOT an auth closure — p
- LEARN: ACCEPTED MISCONFIG @ api.rainbet.com: GET /api/v1/public/ping reverted to full CF managed challenge (110KB) — active operator WAF churn on DO app 53f39197 confi
- LEARN: ACCEPTED MISCONFIG @ staging-monorepo.rainbet.com: /docs flipped from 5485B CF block to full CF managed challenge (110KB) — WAF front state fluctuates on app bc
- LEARN: ACCEPTED MISCONFIG @ staging-raffles.rainbet.com: REAL origin JSON exposed unprotected — `{"code":200,"db":"Running","remote_address":"-","version":"v0.00.0002-
- LEARN: ACCEPTED AUTH @ staging-chat.rainbet.com: socket.io root namespace accepts bare CONNECT (`40`) with no auth — returns `40{"sid":"...","_placeholder":true}` esta
- LEARN: ACCEPTED MISCONFIG @ staging-services.rainbet.com: CORS reflector confirmed on 6 paths incl `/` root — reflects arbitrary Origin + allow-credentials:true + acce
- LEARN: ACCEPTED AUTH @ staging-alerts.rainbet.com: engine.io v4 stable 200/116B (fresh sid, maxPayload=20480) — plane persists, serves as control proving same-DO-app a
- LEARN: REJECTED MISCONFIG @ api.rainbet.com: 6 encoded GET variants (double-encoded path, `%2e%2e`, trailing `%2f`, mixed-case) all 403@5484B — no content-method WAF b

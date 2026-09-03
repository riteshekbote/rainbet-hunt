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

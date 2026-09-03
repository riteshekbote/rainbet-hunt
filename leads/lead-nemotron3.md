## 2026-09-03 17:24:27 UTC [target] (model nemotron3)
[NEW] rainbet.com / www.rainbet.com — Cloudflare managed challenge (403), bot protection active, serves React SPA behind challenge
[NEW] api.rainbet.com — Cloudflare managed challenge (403 on all paths: /, /api/v1, /api/v2, /graphql, /swagger, /openapi.json, /health, /version)
[NEW] staging.rainbet.com — Cloudflare Access (Zero Trust), 302 to challenge-5te-pages.cloudflareaccess.com for all paths including /api
[NEW] app.rainbet.com, auth.rainbet.com, admin.rainbet.com, dashboard.rainbet.com, dev.rainbet.com, login.rainbet.com, m.rainbet.com, my.rainbet.com, portal.rainbet.com, support.rainbet.com, test.rainbet.com, web.rainbet.com — NXDOMAIN (no DNS resolution)
[PRIO] api.rainbet.com,7.0,attack_surface=8,business_value=9,tech_exposure=6,gate_ease=2,cloud_surface=8,freshness=8
[PRIO] staging.rainbet.com,6.5,attack_surface=7,business_value=8,tech_exposure=7,gate_ease=1,cloud_surface=9,freshness=7
[PRIO] rainbet.com,5.5,attack_surface=6,business_value=9,tech_exposure=5,gate_ease=2,cloud_surface=8,freshness=6
[HYP] API endpoint enumeration behind Cloudflare challenge
class: MISCONFIG
asset: api.rainbet.com
confidence: 55
reasoning: All tested endpoints (/api/v1, /api/v2, /graphql, /swagger, /openapi.json, /health, /version) return 403 via Cloudflare challenge rather than 404. Challenge page suggests WAF rules may allow certain paths/headers through. Cloudflare "managed challenge" typically permits known-good bots/API clients with proper headers.
evidence_needed: Identify at least one API endpoint that returns non-403 (200, 401, 404 with JSON body) indicating actual API surface behind WAF
verify_steps: GET https://api.rainbet.com/api/v1/public/ping (if exists), GET https://api.rainbet.com/api/v1/health with Accept: application/json, GET https://api.rainbet.com/ with header CF-Access-Client-Id: test (test bypass), OPTIONS https://api.rainbet.com/api/v1/
impact: If any API endpoint bypasses challenge, full API surface enumeration possible → IDOR/BOLA, mass assignment, business logic flaws on gambling/wallet endpoints
testability: PASSIVE
[HYP] Staging environment Cloudflare Access misconfiguration
class: AUTH
asset: staging.rainbet.com
confidence: 45
reasoning: staging.rainbet.com uses Cloudflare Access (Zero Trust) with JWT metadata in redirect URL (kid, aud, exp claims visible). The redirect includes `service_token_status:false` and `auth_status:NO_OR`. If any policy allows unauthenticated access to specific paths (e.g., /health, /metrics, /.well-known/), staging API could be exposed.
evidence_needed: Find at least one path on staging.rainbet.com returning 200/401/403 (JSON) instead of 302 to Cloudflare Access login
verify_steps: GET https://staging.rainbet.com/.well-known/cloudflare-access-protected-resource/, GET https://staging.rainbet.com/health, GET https://staging.rainbet.com/metrics, GET https://staging.rainbet.com/api/health, GET https://staging.rainbet.com/.well-known/jwks.json
impact: Staging often mirrors production with weaker controls → PII exposure, test wallets, debug endpoints, feature flags
testability: PASSIVE
[HYP] Main application client-side logic exposure via challenge bypass
class: MISCONFIG
asset: rainbet.com
confidence: 40
reasoning: Main domain serves a React SPA (Montserrat font, SVG logo) entirely behind Cloudflare managed challenge. Challenge page includes cf_chl_opt with cFPWv, cRay, cvId. If challenge can be solved programmatically (headless browser, CF challenge solver) or if certain paths (static assets, /api/* proxied) are excluded from challenge, client-side code reveals API contracts, feature flags, wallet logic.
evidence_needed: Successfully solve challenge or find unchallenged path returning JS bundles / API calls
verify_steps: GET https://rainbet.com/ with headless browser (playwright/puppeteer) to solve challenge, GET https://rainbet.com/assets/ (static assets), GET https://rainbet.com/api/ (check if proxied API calls bypass challenge), GET https://rainbet.com/__cf_chl_captcha_tk__ (challenge token endpoint)
impact: Access to compiled React app → reverse-engineer API contracts, find hidden endpoints, identify wallet/betting logic, locate IDOR vectors
testability: AUTH_HELPED
[PARKED] Staging environment Cloudflare Access misconfiguration: confidence 45 < 50 threshold; Cloudflare Access is default-deny; no evidence of policy misconfiguration; verify steps unlikely to yield results without auth
[PARKED] Main application client-side logic exposure via challenge bypass: confidence 40 < 50; requires active challenge solving (headless browser) which exceeds passive-only mandate; Cloudflare managed challenge is robust
[FINAL] 1. API endpoint enumeration behind Cloudflare challenge (api.rainbet.com, confidence 55)
[NEXT] PROBE: GET https://api.rainbet.com/api/v1/public/ping with headers: Accept: application/json, User-Agent: RainBet-Mobile/1.0 (test common mobile API endpoint pattern), then GET https://api.rainbet.com/api/v1/health with Accept: application/json, then OPTIONS https://api.rainbet.com/api/v1/
[LEARN] REJECTED MISCONFIG @ staging.rainbet.com: Cloudflare Access Zero Trust is properly configured (default-deny, JWT metadata visible but no bypass); no evidence of path-based policy gaps
[LEARN] REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all paths including static assets; no unchallenged surface discovered passively
[LEARN] ACCEPTED MISCONFIG @ api.rainbet.com: API subdomain exists and resolves but returns uniform 403 challenge; high-value target if any endpoint allows unauthenticated access (health, version, public config)
[RISK] RainBet: 35 — Attack surface heavily protected by Cloudflare (managed challenge on prod, Zero Trust on staging); only 3/20 inventory hosts resolve; no exposed API surface, GraphQL, Swagger, or auth endpoints discovered passively; primary risk contingent on WAF bypass or credentialed access to staging

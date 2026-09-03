# Knowledge Base (seed)
- 2026-09-03 REJECTED MISCONFIG @ staging.rainbet.com: Cloudflare Access Zero Trust is properly configured (default-deny, JWT metadata visible but no bypass); no evidence of path-based policy gaps
- 2026-09-03 REJECTED MISCONFIG @ rainbet.com: Cloudflare managed challenge covers all paths including static assets; no unchallenged surface discovered passively
- 2026-09-03 ACCEPTED MISCONFIG @ api.rainbet.com: API subdomain exists and resolves but returns uniform 403 challenge; high-value target if any endpoint allows unauthenticated access (health, version, public config)
- 2026-09-03 ACCEPTED MISCONFIG @ api.rainbet.com: CF block page present but `cf-mitigated` header absent (unlike www.rainbet.com) — different CF WAF configurations per subdomain creates potential inconsistency.
- 2026-09-03 ACCEPTED AUTH @ staging.rainbet.com: CF Access JWT contains `auth_status: NONE` and `is_wrap: false` — Access policy may be permissive or misconfigured.
- 2026-09-03 REJECTED dead subdomains (17/20): No DNS resolution or HTTP service — removed from active attack surface until re-checked.

## REPOSCAN 2026-09-03 16:59:52 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-03 19:41:44 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-03 22:18:47 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 00:10:50 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 04:42:04 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 09:21:01 UTC
[HYP] N/A
class: N/A
asset: N/A
confidence: 0
reasoning: No RainBet GitHub organization exists or is publicly discoverable. cands.txt confirms "no org candidates". scope.yml has github_orgs: none-configured. All search results are third-party clones/unrelated repos.
impact: N/A
verify_steps: N/A
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 13:45:22 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 17:23:13 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 19:51:00 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 22:08:00 UTC
NO FINDINGS — zero candidate repos, zero secrets.
Evidence: GitHub API GET /orgs/rainbet/repos returns [] (empty). cands.txt: "no org candidates". scope.yml: github_orgs: none-configured. Web search found 3 third-party repos (rayanroubio/Rainbet-FE, bodsterm/rainbet-modded, parikshitgorain/tzbetz-showcase) — cloned depth=1, grep-scanned for AKIA*, AIza*, ghp_*, sk_live_*, sk-us*, -----BEGIN PRIVATE, password=, api_key, secret, token, client_secret, storage.googleapis, *.azure, *.amazonaws. Zero matches. None contain RainBet infrastructure references. These are NOT RainBet's own code. Source-code audit vector is closed — no public source code exists for RainBet.
## REPOSCAN 2026-09-04 22:10:10 UTC
REPOSCAN 2026-09-04 22:08:00 UTC
NO FINDINGS — zero candidate repos, zero secrets.

Evidence:
- GitHub API: `GET /orgs/rainbet/repos` returns [] (empty array) — no public org exists
- cands.txt: "no org candidates"
- scope.yml: `github_orgs: none-configured`
- Web search: found 3 third-party repos (rayanroubio/Rainbet-FE, bodsterm/rainbet-modded, parikshitgorain/tzbetz-showcase) — all cloned with depth=1 and grep-scanned
- Clone results: zero matches for AKIA*, AIza*, ghp_*, sk_live_*, sk-us*, -----BEGIN PRIVATE, password=, api_key, secret, token, client_secret, storage.googleapis, *.azure, *.amazonaws
- None of the third-party repos contain references to RainBet infrastructure (api.rainbet.com, staging.rainbet.com, etc.)
- These repos are NOT RainBet's own code; they are templates/clones/third-party projects

Conclusion: No source code audit findings. RainBet does not maintain a public GitHub org. The code surface is entirely private. Source-code audit vector is closed.

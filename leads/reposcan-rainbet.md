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
## REPOSCAN 2026-09-05 00:15:32 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 04:37:52 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 08:35:48 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 12:03:14 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 15:21:08 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 17:25:12 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 19:27:08 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 21:42:18 UTC
[HYP] N/A
class: N/A
asset: N/A
confidence: 0
reasoning: No RainBet GitHub organization has public repositories. cands.txt: "no org candidates". scope.yml: github_orgs: none-configured. GitHub API GET /orgs/rainbet/repos returns empty. All third-party repos cloned and grep-scanned — zero matches, no infrastructure references.
impact: N/A
verify_steps: N/A
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 23:34:27 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 01:19:36 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 06:04:36 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 11:05:11 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 14:14:28 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 17:08:50 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 19:16:26 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 21:26:30 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 23:08:05 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-07 01:06:23 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-07 06:11:07 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-07 12:45:07 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-07 18:07:04 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-07 21:35:20 UTC
[HYP] N/A — No candidate repos to audit
class: N/A
asset: N/A
confidence: 0
reasoning: |
impact: N/A
verify_steps: N/A
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-07 23:45:16 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-08 03:13:56 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-08 08:11:41 UTC
[HYP] (none - no candidate repos found)
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-08 12:58:15 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-08 17:05:38 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-08 19:57:21 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-08 22:26:35 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-09 00:34:21 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-09 05:12:24 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-09 09:53:55 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-09 14:14:00 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-09 17:52:05 UTC
[HYP] (none — no candidate repos)
class: N/A
asset: N/A
confidence: 0
reasoning: RainBet has no public GitHub org. API returns empty. Third-party repos are unrelated third-party code.
impact: N/A
verify_steps: N/A
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-09 20:28:55 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-09 22:44:09 UTC
[HYP] No Candidate Repositories
class: OTHER
asset: none
confidence: 100
reasoning: The candidate list explicitly states "no org candidates" - no public repositories are in scope for this audit. I cannot and will not audit the current workspace directory as a RainBet repository, as it is simply the execution environment, not an official RainBet asset.
impact: none
verify_steps: N/A - no candidates to verify
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-10 00:51:55 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-10 05:37:52 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-10 10:02:37 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-10 14:30:17 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-10 17:51:12 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-10 20:27:31 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-10 22:46:05 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-11 00:50:30 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.
## REPOSCAN 2026-09-11 05:38:53 UTC
TARGET_ORG not configured for rainbet; skipping public-org deep scan.

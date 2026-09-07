# Validated findings (running count 0)

- 4 lead(s) marked VALID at 2026-09-06 01:20:00 UTC
  - **Verdict: VALID**
  - **Verdict: VALID**
  - | 1 | staging-{raffles,chat,alerts,socket} anonymous Socket.IO + health JSON | **VALID** | 5.4 | Report via bugs.olivermaicher.eu |
  - | 2 | rainbet-com-rabbitmq internet-exposed brokers | **VALID** | 7.3 | Report via bugs.olivermaicher.eu |

- 2 lead(s) marked VALID at 2026-09-06 06:05:57 UTC
  - **Verdict: VALID**
  - | 1 | Staging pocket app (1ce4ff55) unprotected origin | **VALID** | 5.3 | Report to bugs.olivermaicher.eu |

- 2 lead(s) marked VALID at 2026-09-06 11:08:47 UTC
  - **Verdict: VALID**
  - | 1 | Staging pocket app: origin API + Socket.IO exposed (4 hostnames, DO app 1ce4ff55) | **VALID** | 7.5 | Report with GET /health proof |

- 7 lead(s) marked VALID at 2026-09-07 18:08:44 UTC
  - **Verdict: VALID**
  - **Verdict: VALID**
  - | Q7 Reasonable triager? | **YES** — same class as Lead 2, valid but may be merged in report |
  - **Verdict: VALID** (merge with Lead 2 in single report)
  - | 1 | staging-services unprotected origin | **VALID** | 5.3 |
  - | 2 | staging-alerts anonymous Socket.IO | **VALID** | 5.3 |
  - | 3 | staging-chat engine.io (merge w/ #2) | **VALID** | 5.3 |

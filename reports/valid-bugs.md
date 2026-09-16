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

- 6 lead(s) marked VALID at 2026-09-08 17:09:18 UTC
  - ### Verdict: **VALID**
  - ### Verdict: **VALID**
  - ### Verdict: **VALID**
  - | 1. Staging pocket app (health + engine.io) | **VALID** | 6.5 | Report |
  - | 2. staging-services reflected CORS | **VALID** | 5.3 | Report |
  - | 8. RabbitMQ brokers on DO origins | **VALID** | 5.3 | Report |

- 11 lead(s) marked VALID at 2026-09-09 20:31:46 UTC
  - | **Q5 Novel/unreported?** | YES — not on valid-bugs.md as merged/duplicate for this exact combination. |
  - **Verdict: VALID**
  - | **Q5 Novel/unreported?** | YES — confirmed in probe results 2026-09-09 06:16:09 but not yet in valid-bugs.md as a distinct merged finding for CORS. |
  - **Verdict: VALID**
  - **Verdict: VALID**
  - | **Q3 Real security impact?** | YES — admin console + unencrypted message broker on public internet bypassing WAF. If default/weak creds → full message-bus compromise → payment/withdrawal event injec
  - | **Q5 Novel/unreported?** | NO — already marked VALID at 2026-09-06 01:20 UTC and merged into valid-bugs.md. |
  - | **Q5 Novel/unreported?** | Already accepted in prior triage as valid but low-impact. |
  - | 1 | staging-{raffles,chat,alerts,socket} unprotected origin + engine.io | **VALID** | 5.3 | Report to bugs.olivermaicher.eu |
  - | 2 | staging-services reflected CORS (credentials:true) | **VALID** | 5.3 | Report to bugs.olivermaicher.eu |
  - | 3 | staging-chat socket.io bare CONNECT auth asymmetry | **VALID** | 5.3 | Report to bugs.olivermaicher.eu (merge w/ Lead 1) |

- 4 lead(s) marked VALID at 2026-09-12 13:07:59 UTC
  - | 1 | staging-{raffles,chat,alerts,socket} anonymous Socket.IO + health JSON origin exposure | 5.4 | VALID |
  - | 2 | rainbet-com-rabbitmq internet-exposed brokers (management 15672 + AMQP 5672) | 7.3 | VALID |
  - | 3 | Staging pocket app (DO app 1ce4ff55) unprotected origin | 5.3 | VALID |
  - | 4 | staging-services reflected CORS (credentials:true on 4+ paths) | 5.3 | VALID |

- 4 lead(s) marked VALID at 2026-09-12 23:05:36 UTC
  - | 1 | staging-{raffles,chat,alerts,socket} anonymous Socket.IO + health JSON origin exposure | 5.4 | VALID |
  - | 2 | rainbet-com-rabbitmq internet-exposed brokers (management 15672 + AMQP 5672) | 7.3 | VALID |
  - | 3 | Staging pocket app (DO app 1ce4ff55) unprotected origin | 5.3 | VALID |
  - | 4 | staging-services reflected CORS (credentials:true on 4+ paths) | 5.3 | VALID |

- 4 lead(s) marked VALID at 2026-09-14 13:21:13 UTC
  - **Verdict: VALID**
  - **Verdict: VALID (Low)**
  - | 1 | staging-chat unauthenticated socket.io | **VALID** | 5.3 (Medium) | Real unauthenticated session on staging |
  - | 3 | staging-raffles /health origin leak | **VALID** (Low) | 3.7 (Low) | Version + DO infra info disclosure |

- 4 lead(s) marked VALID at 2026-09-15 19:14:23 UTC
  - | Q5 Novel/unreported? | **No** — already marked VALID in valid-bugs.md (2026-09-06, 2026-09-09, 2026-09-12, 2026-09-14) |
  - | Q5 Novel/unreported? | **No** — already merged into Lead 1 (staging Socket.IO group) in valid-bugs.md |
  - | Q5 Novel/unreported? | **No** — already marked VALID in valid-bugs.md (2026-09-14 13:21, CVSS 3.7 Low) |
  - | Q5 Novel/unreported? | **Borderline** — OPTIONS on /api/v1/ has been observed since 2026-09-03; already noted in lead logs but NOT in valid-bugs.md as a distinct reportable finding |

- 4 lead(s) marked VALID at 2026-09-15 22:21:56 UTC
  - **Verdict: VALID**
  - **Verdict: VALID**
  - | 1 | Staging pocket app: unprotected origin + anonymous Socket.IO (4 hostnames) | **VALID** | 5.3 |
  - | 2 | Internet-exposed RabbitMQ brokers (management + AMQP) on direct DO IPs | **VALID** | 7.5 |

- 4 lead(s) marked VALID at 2026-09-16 18:57:28 UTC
  - **Verdict: VALID**
  - **Verdict: VALID**
  - | 1 | staging-chat: Unauthenticated socket.io CONNECT | **VALID** | 7.5 |
  - | 2 | staging-alerts: WebSocket hijack via captured sid | **VALID** | 8.1 |

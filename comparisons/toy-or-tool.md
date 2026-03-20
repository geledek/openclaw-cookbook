---
title: "OpenClaw 究竟是不是玩具，到底要不要学 OpenClaw?"
author: "@gkxspace (余温)"
source_url: "https://x.com/gkxspace/status/2028253677597901032"
source_type: twitter-thread
date_saved: 2026-03-02
date_published: 2026-03-01
tags: [openclaw, ai-agents, automation, self-hosted, workshop, strategy]
summary: "Comprehensive OpenClaw vs Claude Code comparison based on 30+ real cases. Key distinction: heartbeat makes OpenClaw a 'duty officer' not just a tool. 7 real case studies (4 positive, 3 negative). Security section covers 6 CVEs, 824+ malicious skills, 42K exposed instances. Best practice: OpenClaw as scheduling brain + Claude Code as coding engine. OpenClaw value requires: clear automation needs + willingness to invest in setup."
language: zh
---

# OpenClaw 究竟是不是玩具？

Author read 30+ real cases, official docs, security reports, Reddit/V2EX/X first-hand experiences.

## OpenClaw vs Claude Code: Fundamental Difference

| | Claude Code | OpenClaw |
|---|---|---|
| Type | Session-based coding executor | Daemon-based full-domain agent |
| Lifecycle | Terminal session, stops when closed | 24/7 resident, event-driven |
| Memory | Project-level, dissolves with session | Life-level, accumulates across tasks/time/platforms |
| Core capability | Code read/write, command execution, test verification | Multi-tool routing, message channels, browser, scripts, memory, sub-sessions |

**One-line summary**: Claude Code = "in-session coding tool", OpenClaw = "full-domain automation OS". One is an execution engine, the other is a scheduling hub.

## The Heartbeat: The Single Most Important Differentiator

Not multi-channel, not memory, not skills — **heartbeat** is what separates OpenClaw from everything else.

- Every 30 min (configurable), agent auto-wakes
- Reads HEARTBEAT.md, executes checklist
- If normal → HEARTBEAT_OK (silent)
- If abnormal → proactive alert or fix

**What this means**: Traditional AI assistants (ChatGPT, Claude Code, Cursor) are passive. Heartbeat flips the model — agent has "proactive environment sensing and action."

### Real heartbeat use cases
1. System health patrol (server status, disk, processes)
2. Inbox follow-up (draft replies, reminders)
3. Flight/logistics tracking (proactive notifications)
4. Code repo monitoring (CI/CD, PR reviews, issues)
5. Memory maintenance (cleanup, context health)
6. Security audit (config compliance checks)

## Positive Cases

### Case 1: Reorx — "From code executor to manager"
Phone chat → OpenClaw → calls Claude Code → auto-deploy → results back. Never opens laptop.

### Case 2: AIMLAPI — "€5 VPS, 2 weeks, never hit resource limits"
2 vCPU / 4GB RAM / 40GB SSD. 5 verified use cases. 8 common problems documented. "Don't need Mac Mini, €5 VPS is enough."

### Case 3: SparkryAI — "15 consulting requests in 24h, best ADHD accommodation"
Auto-classified consulting requests, email drafts, dentist appointment → calendar + 30min drive buffer + auto-reply to wife.

### Case 4: V2EX lang-tools — "41 commits in 2 days, +1,797 lines"
Mac Mini M4 + Ubuntu VM + Telegram. Full automation: download repo → modify → push.

## Negative Cases

### Case 5: V2EX — "Capabilities suck, soul is interesting"
Non-technical user. Complex setup, search needs credit card API, "can't even set a timer reminder."

### Case 6: Reddit — "Cool demo, not for real ops"
WhatsApp pairing "shockingly smooth" but overall: demo-grade, not production-ready.

### Case 7: Medium — "Browser automation repeatedly fails in cloud"
Browser control service timeout in cloud deployment.

### Pattern
**Positive cases share**: need 24/7, cross-platform routing, long-term memory, proactive triggers
**Negative cases share**: high setup barrier, unstable browser automation, unpredictable token costs, infrastructure-sensitive

## Security Concerns

- Feb 23, 2026: Endor Labs found 6 new CVEs
- 824+ malicious skills in registry
- 42,000+ exposed instances
- Karpathy: "handing my private keys to a 400K-line behemoth under massive attack feels like the Wild West"
- NanoClaw alternative: ~3,900 lines (15 files), container-default
- Core tension: feature richness vs security auditability

## Best Practice: Combo Use

OpenClaw (scheduling brain) + Claude Code (coding engine):
1. Via Skills: expose Claude Code as agent tools (claude_launch, claude_respond)
2. Via PTY: run Claude Code as interactive CLI
3. Integration guide on Towards Data Science (6 days ago)

## Verdict

OpenClaw value requires two prerequisites:
1. Clear automation need ("I need it to do X" not "I want to try")
2. Willingness to invest in setup (learning curve, ops, cost governance)

Without both → it IS a toy. With both → it's a production force multiplier.

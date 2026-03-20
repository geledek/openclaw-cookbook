---
title: "How Companies Should Take Notes with AI"
author: "@molt_cornelius (Cornelius)"
source_url: "https://x.com/molt_cornelius/status/2029050581474488599"
source_type: twitter-thread
date_saved: 2026-03-04
tags: [ai-agents, productivity, automation, workshop, strategy, twitter-thread]
category: saves/x
summary: Cornelius lays out a vault-based AI knowledge system for companies using Claude Code — folder structure, skills, hooks — that turns meeting transcripts into a living organizational brain.
---

# How Companies Should Take Notes with AI

**Author:** @molt_cornelius (Cornelius)
**Source:** [X Thread](https://x.com/molt_cornelius/status/2029050581474488599)

---

## The Problem

Fortune 500 companies lose **$31.5 billion per year** from failure to share knowledge (IDC). Every KM initiative — wikis, Confluence, decision logs, OKR trackers — fails for the same reason: they require human maintenance, and no organization sustains that alongside quarterly targets.

- **70% of KM initiatives fail within 6 months** (worse than ERP deployments)
- **37% of organizational time** spent making decisions — more than half ineffectively
- **Ebbinghaus forgetting curve**: 70% of new information forgotten within 24 hours. 92% of meeting attendees multitask. 63% of meetings have no agenda. Within a week, three-quarters of what was decided is gone.

The interesting problem isn't knowledge loss — it's **structural drift**: strategy drifts from execution through thousands of small daily choices, none visible in aggregate.

---

## The Solution: A Vault + Agent Architecture

### Vault Folder Structure

```
vault/
├── decisions/       # Every org decision, linked to assumptions + rejected alternatives
├── strategy/        # Strategic direction as falsifiable claims
├── transcripts/     # Drop zone for meeting recordings
├── competitors/     # Living profiles that accumulate intelligence over time
├── risks/           # Risk register with early warning signals
├── pipeline/        # Deal flow and strategic relationships
├── okrs/            # Objectives; key results computed from vault state
├── reviews/         # Agent-generated analysis
├── archive/         # Processed transcripts + summaries
└── .claude/
    ├── CLAUDE.md    # System prompt / vault constitution
    ├── skills/
    │   ├── mine/SKILL.md     # Extract decisions from transcripts
    │   ├── review/SKILL.md   # OKR progress + health report
    │   ├── deals/SKILL.md    # Pipeline status
    │   ├── learn/SKILL.md    # Parallel web research
    │   └── consult/SKILL.md  # Structured decision-making
    └── hooks/
        ├── session-orient.sh  # Surfaces what needs attention on open
        ├── auto-commit.sh     # Commits every change to git
        └── write-validate.sh  # Schema validation before save
```

**Key design principle:** Every folder holds **atomic notes** — one decision, one risk, one competitor per file. Filenames are propositions: not `pricing.md` but `pricing model uses usage-based billing.md`. A new hire can read the `decisions/` directory listing and understand what the company has decided without opening a single file.

---

## CLAUDE.md — The Vault Constitution

The system prompt lives at `.claude/CLAUDE.md`. It tells the agent:
- What the vault is and how it's structured
- Routing rules for every note type
- Quality gates (e.g., every decision must have an `assumptions` field)
- Vocabulary the agent uses consistently

---

## Skills — Defined Agent Capabilities

Each skill is a markdown file in `.claude/skills/<name>/SKILL.md`. Example — the `/mine` skill:

```markdown
# /mine — Transcript Mining

Extract decisions, insights, action items, and competitive signals
from team conversations. Route each to the correct vault location.

## Instructions

1. Read the full transcript
2. Identify every thread: decisions, actions, competitive mentions,
   strategy shifts, risk signals, feature requests
3. For each decision:
   - Create an atomic note in decisions/
   - Include: assumptions, alternatives, reversibility, review_date
   - Link to any existing decisions it supersedes or depends on
4. For each competitive mention:
   - Update the entity profile in competitors/
   - Add to the signal log with date, source, and impact assessment
5. For each strategy shift:
   - Flag against documented direction in strategy/
   - If contradictory, surface explicitly
6. Create a meeting summary in archive/transcripts/
7. Move the raw transcript to archive/transcripts/

## Quality Gates

- Every extracted decision has an assumptions field
- Every competitive mention updates the entity profile, not just the summary
- Strategy contradictions are flagged, not silently absorbed
- Zero information loss: if it was discussed, it was extracted or explicitly marked as not actionable
```

Other skills: `/review` (OKR health), `/deals` (pipeline), `/learn` (parallel web research), `/consult` (structured decisions with weighted criteria matrix + vault evidence).

---

## Hooks — Automatic Agent Triggers

**session-orient.sh**: Fires on every Claude Code open. Counts unmined transcripts, checks stale competitor profiles, flags overdue decision reviews:
```
Session orient:
  CONDITION: 1 unmined transcript in transcripts/
  → 2026-03-04-strategy-session.txt (47 minutes, ~8200 words)
  Recommended: /mine 2026-03-04-strategy-session.txt
```

**auto-commit.sh**: Commits every change to git after each operation — complete version history of all decisions.

**write-validate.sh**: Checks every new file against schema. A decision without `assumptions`, a risk without `early_warnings` — flagged before save.

---

## Key Insight

> "The first step is not an agent. It is a structure the agent can read."

The agent doesn't replace good knowledge structure — it makes maintaining that structure effortless. **Your only job is to capture. The agent architects.**

---

## Relevance to Ray

- Direct template for Bob's own AGENTS.md / Skills architecture
- Workshop module: "Build your company's AI brain"
- The vault pattern mirrors what Ray's doing with OpenClaw workspace — but framed for enterprise audiences at SAP
- `/mine` skill → transcript mining is a concrete demo use case for workshops

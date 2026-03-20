---
title: "Karpathy: Multi-Agent Research Org with nanochat — It Doesn't Work Yet"
author: "@karpathy"
source_url: "https://x.com/karpathy/status/2027521323275325622"
source_type: twitter-thread
date_saved: 2026-02-28
date_published: 2026-02-28
tags: [ai-agents, llm, automation, productivity, open-source]
summary: "Karpathy ran 8 agents (4 Claude, 4 Codex) with 1 GPU each on nanochat experiments. Tried solo researchers and chief+junior setups. TLDR: doesn't work — agents can implement well-scoped ideas but can't creatively generate good experiment designs."
language: en
---

# Karpathy: Multi-Agent Research Org with nanochat

## Key Takeaways

- 8 agents (4 Claude, 4 Codex), each with 1 GPU, running nanochat experiments (trying to delete logit softcap without regression)
- Tried multiple setups: 8 independent solo researchers, 1 chief scientist + 8 junior researchers
- **It doesn't work yet** — agents' ideas are bad out of the box, even at highest intelligence
- Agents don't think carefully through experiment design, run nonsensical variations, don't create strong baselines, don't control for runtime/flops
- Example failure: agent "discovered" that increasing hidden size improves validation loss — a totally spurious result it should have known about
- **Agents are good at implementing well-scoped ideas but don't creatively generate them**

## Infrastructure Setup

- Each research program = a git branch, each scientist forks into feature branch
- Git worktrees for isolation
- Simple files for communication (no Docker/VMs — instructions are enough to prevent interference)
- Research org runs in tmux window grids of interactive sessions — visual like Teams, can "take over" if needed
- No `-p` flag (interactive, not piped)

## The Bigger Insight

You're now "programming an organization" — the source code is the collection of prompts, skills, tools, and processes. A daily standup is now "org code." The eval question becomes: given an arbitrary task, how quickly does your research org generate progress on it?

## Context

Replying to Thomas Wolf asking why NanoGPT speedrun isn't fully AI-automated research yet. Karpathy's honest answer: because the creative research part is still broken.

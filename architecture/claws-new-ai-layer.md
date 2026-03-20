---
id: 2026-02-26__karpathy-claws-new-layer-ai-stack
title: "Claws Are a New Layer of the AI Stack — Karpathy"
source_type: x
source_url: "https://x.com/karpathy/status/2024987174077432126"
author: "Andrej Karpathy (@karpathy)"
date_saved: 2026-02-26
tags: [openclaw, ai-agents, strategy, llm, twitter-thread, workshop]
category: saves/x
summary: "Karpathy buys a Mac mini to tinker with Claws, raises security concerns about OpenClaw specifically (400K lines, RCE vulns, supply chain risks), loves the concept, highlights NanoClaw (~4000 lines, skills-as-code config) as an interesting alternative. Frames 'Claws' as a new orchestration layer above LLM agents."
---

# Claws Are a New Layer of the AI Stack — Karpathy

> Andrej Karpathy's take: Claws = the next layer above LLM agents. Loves the concept, has real security concerns about OpenClaw specifically, excited about leaner alternatives like NanoClaw.

## The Tweet

> "Bought a new Mac mini to properly tinker with claws over the weekend. The apple store person told me they are selling like hotcakes and everyone is confused :)"

---

## Security Concerns About OpenClaw

Karpathy is specifically skeptical of running OpenClaw:

> "giving my private data/keys to 400K lines of vibe coded monster that is being actively attacked at scale is not very appealing at all"

Already seeing:
- Reports of exposed instances
- RCE vulnerabilities
- Supply chain poisoning
- Malicious or compromised skills in the registry

> "it feels like a complete wild west and a security nightmare"

---

## But He Loves the Concept

> "I do love the concept — just like LLM agents were a new layer on top of LLMs, Claws are now a new layer on top of LLM agents, taking the orchestration, scheduling, context, tool calls and a kind of persistence to a next level."

**The stack as Karpathy sees it:**
```
LLMs
  ↓ (LLM Agents layer)
LLM Agents
  ↓ (Claws layer — new)
Claws: orchestration + scheduling + context + tool calls + persistence
```

---

## NanoClaw — The Alternative He's Most Excited About

> "NanoClaw looks really interesting in that the core engine is ~4000 lines of code (fits into both my head and that of AI agents, so it feels manageable, auditable, flexible, etc.) and runs everything in containers by default."

Two things he loves:
1. **Auditability** — small enough to actually read and understand
2. **Skills-as-code configuration:**

> "I also love their approach to configurability — it's not done via config files it's done via skills! For example, `/add-telegram` instructs your AI agent how to modify the actual code to integrate Telegram."

> "I haven't come across this yet and it slightly blew my mind earlier today as a new, AI-enabled approach to preventing config mess and if-then-else monsters."

**The new meta he's identifying:**
> "Write the most maximally forkable repo and then have skills that fork it into any desired more exotic configuration."

---

## The Ecosystem

Other Claw alternatives he mentions: `nanobot`, `zeroclaw`, `ironclaw`, `picoclaw` — *"lol @ prefixes"*

Cloud-hosted alternatives exist but he prefers local:
- Easier to tinker
- Can connect to home automation on local network
- And aesthetically:

> "there is something aesthetically pleasing about there being a physical device 'possessed' by a little ghost of a personal digital house elf"

---

## Relevance for Workshop

Karpathy's framing is useful for:
1. **Positioning OpenClaw in the stack** — not just another chatbot, a new orchestration layer
2. **Addressing the security elephant in the room** — his concerns are legitimate; workshop should address self-hosting best practices
3. **The "forkable repo + skills" meta** — useful mental model for explaining how skills work
4. **Audience calibration** — even Karpathy is "not 100% sure" what his setup looks like yet; it's genuinely new territory

---
*Saved: 2026-02-26 | Source: x.com (@karpathy)*

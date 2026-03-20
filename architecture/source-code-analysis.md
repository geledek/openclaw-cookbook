---
title: "OpenClaw 源码解析：为什么说它是 AutoGPT 的进化版"
author: "@wang_xiaolou (日拱一卒王小楼)"
source_url: "https://x.com/wang_xiaolou/status/2028024500433170766"
source_type: twitter-thread
date_saved: 2026-03-01
date_published: 2026-03-01
tags: [openclaw, ai-agents, automation, llm, strategy]
summary: "2-day source code deep dive into OpenClaw architecture. 4-layer design (Interface→Gateway→Agent Core→Tools/Skills). Detailed comparison with AutoGPT (incremental vs over-planning), LangChain (complete app vs framework), CrewAI (single-agent vs multi-agent). Key innovation: incremental planning with continuous reflection, structured 3-tier memory (working/short/long-term), and verification after each step."
language: zh
---

# OpenClaw 源码解析：为什么说它是 AutoGPT 的进化版

14万 GitHub stars in short time. Author spent 2 days reading source code.

## 4-Layer Architecture

```
Interface Layer    → Telegram / Discord / Signal / CLI / Web
Gateway Layer      → Message routing / Session mgmt / Auth
Agent Core Layer   → Plan / Execute / Memory / Reflect
Tools/Skills Layer → Filesystem / API / Browser / Custom
```

### Layer 1: Interface
- Not bound to any specific UI — supports Telegram, Discord, Signal, WhatsApp (bridged), CLI, Web
- Same agent runs across multiple platforms simultaneously

### Layer 2: Gateway (most underrated)
- Message routing: identify channel → parse intent → route to agent instance
- Session management: per-user context, multi-turn conversation, lifecycle
- Auth: identity verification, permissions, rate limiting

### Layer 3: Agent Core (the brain)
Core loop: Understand → Plan → Execute → Reflect → Memorize

**3-Tier Memory** (inspired by cognitive science):
1. **Working memory**: current task context, recent conversation, temp vars
2. **Short-term memory**: today's activity log, recent tasks, temporary preference learning
3. **Long-term memory**: knowledge graph, user profile/preferences, historical patterns

### Layer 4: Tools & Skills
- Built-in: filesystem, HTTP client, Playwright browser, sandboxed code execution, SQL
- Skills system: register/execute pattern, extend without modifying core

## OpenClaw vs AutoGPT

| Problem in AutoGPT | OpenClaw's fix |
|---|---|
| Over-planning (complex plans, gets lost) | Incremental planning (next 1-3 steps only) |
| No feedback loop (can't adjust mid-execution) | Continuous reflection after each step |
| Memory chaos (everything in context) | Structured 3-tier memory + knowledge graph |
| False completion reports | Verification mechanism after execution |

**Key code difference**: AutoGPT plans ALL steps upfront; OpenClaw plans next 1-3 steps given current state + history.

## OpenClaw vs LangChain

| | LangChain | OpenClaw |
|---|---|---|
| Type | Framework/toolkit | Complete application |
| Use when | Building custom AI product, need full control | Need ready-made AI assistant, quick automation |
| Learning curve | High | Medium |
| Community | Developer ecosystem | User + developer ecosystem |

## OpenClaw vs CrewAI

- CrewAI: multi-agent collaboration (researcher + writer + editor as a crew)
- OpenClaw: single-agent with multiple skills (one agent uses web_search + content_generation + text_editing)
- Future: community developing multi-agent support with delegation

## Technical Deep Dive

### Task Understanding
Extracts: main goal, required info, potential challenges, success criteria — using user preferences + available tools + current state as context.

### Incremental Planning
Only plans next 1-3 steps. Each step specifies: action, tool/skill, expected outcome, verification method.

### Execute & Reflect
After each step: verify result → if success, record and continue; if fail, analyze failure and suggest correction → replan.

## Assessment

Well-structured technical overview but some code examples look reconstructed/simplified rather than actual source. The architectural analysis and framework comparisons are valuable. Good reference for understanding why OpenClaw works where AutoGPT failed.

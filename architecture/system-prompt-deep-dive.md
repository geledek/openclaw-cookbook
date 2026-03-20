---
id: 2026-02-26__lufzzliz-openclaw-system-prompt-deep-dive
title: "抽丝剥茧：深度解析 OpenClaw 万字系统提示词（System Prompt）构成"
title_en: "Dissecting OpenClaw's 10,000-Character System Prompt: A Deep Analysis"
source_type: x
source_url: "https://x.com/lufzzliz/status/2026669714072809755"
author: "@LufzzLiz (岚叔)"
date_saved: 2026-02-26
tags: [openclaw, ai-agents, llm, workshop, twitter-thread]
category: saves/x
summary: "岚叔's deep teardown of OpenClaw's full system prompt using a custom modelbox proxy tool — revealing the 16k token baseline cost per message, 3-part prompt structure (tools/safety/skills + model aliases/workspace/reply rules + injected files/memory), and practical optimization insights."
---

# 抽丝剥茧：深度解析 OpenClaw 万字系统提示词（System Prompt）构成

> 岚叔's deep teardown of OpenClaw's full system prompt using a custom modelbox proxy tool — revealing 16k token baseline, 3-part prompt architecture, and practical tuning insights.

## 背景 / Background

A single "hi" to OpenClaw costs ~34,062 characters (~16k tokens) in system prompt — before you even write a word. 岚叔 built a custom **modelbox** proxy tool to intercept the full prompt and expose all layers. OpenClaw's session logs only show fragments; modelbox captures everything.

**Tool:** [github.com/cclank/modelbox](https://github.com/cclank/modelbox) — simulates a model provider, intercepts the full prompt payload for analysis.

---

## The 3-Part System Prompt Architecture

### Part 1: Source-injected Core + Plugin Tools + Skill Index

**Identity declaration:**
> "You are a personal assistant running inside OpenClaw."

Hard-coded in source. Establishes the agent's role boundary.

**Tool availability (dynamic, policy-filtered):**
- Lists every currently active tool: `read`, `write`, `edit`, `exec`, `memory_*`, `sessions_*`, custom plugin tools (e.g. `camofox_*`)
- Case-sensitive — a single wrong character breaks the call
- `TOOLS.md` is NOT a permission source — source code overrides it (important: anything in TOOLS.md that implies permissions may be silently overridden)

**Safety block:** No independent goals, no self-preservation, no resource acquisition, comply with stop/audit requests, pause on conflicting instructions.

**OpenClaw CLI Quick Reference:** Injected gateway commands (status/start/stop/restart). Model told not to invent commands.

**Skills (mandatory):** Pre-reply scan of `available_skills` list. Only reads a skill's SKILL.md when task matches description. Max 1 skill loaded per turn. Each skill entry: name + description + location.

**Memory Recall:** Before answering anything about history/decisions/preferences/todos — must run memory_search first.

---

### Part 2: Model Aliases, Workspace, Docs, Time, Reply Rules, Messaging

**Model aliases:** Runtime-injected mapping table (e.g. "opus" → full provider path). Note: a large model list = more tokens per turn.

**Workspace:** Working directory declared dynamically at runtime.

**Documentation:** Local docs path, official mirror, GitHub, Discord, ClawHub links.

**Current Date & Time:** User timezone injected at runtime.

**Workspace Files (injected):** Signals that user-editable workspace files will be appended to Project Context below.

**Reply Tags:** `[[reply_to_current]]` / `[[reply_to:id]]` syntax — must be first token in message, stripped before sending.

**Messaging rules:** Route current-session replies automatically; cross-session via `sessions_send`; no exec/curl for messaging.

---

### Part 3: Project Context (User Files)

This is the big variable. Contains all user-configured markdown files:
- SOUL.md, USER.md, AGENTS.md, MEMORY.md, HEARTBEAT.md, TOOLS.md, IDENTITY.md
- Plus inbound channel metadata, group chat context, runtime metadata

This section is what makes the prompt balloon to 16k+ tokens. Every session loads all these files in full.

---

## Key Insights for Optimization

1. **16k tokens is the baseline floor** — every conversation starts here, even "hi"
2. **MEMORY.md size directly affects cost** — keep it curated, not exhaustive
3. **Skill descriptions are included in every prompt** — keep `<description>` tags concise
4. **TOOLS.md doesn't grant permissions** — it's a human memo, not a policy file
5. **Model alias table is runtime-injected** — fewer configured models = fewer tokens
6. **Skills are progressive disclosure** — only SKILL.md loads on match, descriptions always present
7. **To slim the prompt:** prune MEMORY.md, shorten SOUL.md/AGENTS.md, reduce model aliases, keep skill descriptions tight

---

## 岚叔's Setup Note

岚叔 also uses a `camofox_*` plugin (anti-detection browser for reading tweets) — shows up automatically in the tool list because all active plugins are dynamically injected regardless of task relevance.

---
*Saved: 2026-02-26 | Source: x.com (@LufzzLiz) | Language: Chinese (Simplified)*

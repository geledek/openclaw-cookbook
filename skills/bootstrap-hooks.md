---
title: "OpenClaw Bootstrap Hook 系统完全解析"
author: "@servasyy_ai (huangserva)"
source_url: "https://x.com/servasyy_ai/status/2029186874074644619"
source_type: twitter-thread
date_saved: 2026-03-04
tags: [openclaw, ai-agents, automation, workshop, ebook]
category: saves/x
summary: Code-traced teardown of OpenClaw's 4-mechanism Bootstrap Hook system — agent:bootstrap (file-level), bootstrap-extra-files (append), before_prompt_build (prompt-level), bootstrapMaxChars (budget) — with practical use cases and design principles.
---

# OpenClaw Bootstrap Hook 系统完全解析

**Author:** @servasyy_ai (huangserva)
**Source:** [X Thread](https://x.com/servasyy_ai/status/2029186874074644619)
**Written:** 2026-03-04

> "技术问题必须查代码，不能靠推测。" (Technical questions require reading the code, not guessing.)

---

## The Journey: How a Bootstrap File Gets to the LLM

```
User starts Agent
  ↓
attempt.ts → buildBootstrapContextFiles()
  ↓
bootstrap-files.ts loads 8 default files
  ↓
applyBootstrapHookOverrides() triggers agent:bootstrap Hook
  ↓
bootstrap-extra-files Hook appends extra files
  ↓
buildBootstrapContextFiles() applies character budget (20K/file, 150K total)
  ↓
buildEmbeddedSystemPrompt() builds system prompt
  ↓
before_prompt_build Hook modifies final prompt
  ↓
Sent to LLM
```

---

## The 4 Mechanisms

### 1. `agent:bootstrap` Hook (Internal Hook System)

**Triggered at:** `bootstrap-hooks.ts` → `applyBootstrapHookOverrides()`

**Capabilities:**
- Full control over the `bootstrapFiles` array
- Add, remove, reorder, or modify file content
- Can completely replace all bootstrap files

**Who can register:**
- OpenClaw plugins
- Workspace Hooks (`~/.openclaw/workspace-*/hooks/` directory)
- Internal modules

**Code example:**
```ts
registerInternalHook("agent:bootstrap", (event) => {
  const context = event.context as AgentBootstrapHookContext;
  context.bootstrapFiles = [
    { path: "CUSTOM.md", content: "自定义内容" }
  ];
});
```

---

### 2. `bootstrap-extra-files` Hook (Bundled Hook)

**Triggered at:** `hooks/bundled/bootstrap-extra-files/handler.ts`

**Capabilities:**
- Append-only — does not modify existing files
- Specify extra files via config

**Config:**
```json
{
  "hooks": {
    "bootstrap-extra-files": {
      "enabled": true,
      "paths": ["extra/*.md", "docs/CONTEXT.md"]
    }
  }
}
```

**Best for:**
- Injecting project-specific context files
- Adding docs without touching the default 8 bootstrap files
- Dynamically loading extra documents

---

### 3. `before_prompt_build` Hook (Plugin Hook)

**Triggered at:** `attempt.ts` → `runBeforePromptBuild()`

**Capabilities:**
- Modifies the final prompt (after system prompt is built, before sending to LLM)
- Can prepend context
- Can override `systemPrompt` entirely

**Event data:**
```ts
{
  prompt: string;     // user input
  messages: unknown[]; // session message history
}
```

**Return value:**
```ts
{
  prependContext?: string;  // prepend to prompt
  systemPrompt?: string;    // override system prompt
}
```

**Best for:**
- Dynamically adjusting prompt based on session history
- Injecting real-time context (current time, weather)
- Completely replacing system prompt

**Example:**
```ts
on("before_prompt_build", (event, ctx) => {
  return {
    prependContext: `当前时间：${new Date().toISOString()}`
  };
});
```

---

### 4. `bootstrapMaxChars` / `bootstrapTotalMaxChars` (Config)

Not a hook — a hard budget control.

| Setting | Default | Scope |
|---|---|---|
| `bootstrapMaxChars` | 20,000 chars | Per file |
| `bootstrapTotalMaxChars` | 150,000 chars | All files combined |

Truncation: head 70% + tail 20% (keeps beginning and end, drops middle).

**Config location:**
```json
{
  "agents": {
    "defaults": {
      "bootstrapMaxChars": 20000,
      "bootstrapTotalMaxChars": 150000
    }
  }
}
```

---

## Design Principles

### 1. Layered Control
- **L1 (File level):** `agent:bootstrap` — controls which files load
- **L2 (Content level):** `bootstrapMaxChars` — controls how much of each file is used
- **L3 (Prompt level):** `before_prompt_build` — controls final content sent to LLM

### 2. Progressive Enhancement
- Default 8 files are enough for most cases
- Need more? → `bootstrap-extra-files`
- Need full control? → `agent:bootstrap`
- Need dynamic/real-time? → `before_prompt_build`

### 3. Security Boundaries
- Internal hooks (`agent:bootstrap`) only registered by trusted code
- Plugin hooks (`before_prompt_build`) have explicit input/output contracts
- Config (`bootstrapMaxChars`) provides hard limits

---

## Practical Use Cases

**Add project docs:**
```json
{
  "hooks": {
    "bootstrap-extra-files": {
      "enabled": true,
      "paths": ["docs/API.md", "docs/ARCHITECTURE.md"]
    }
  }
}
```

**Load files dynamically by session type:**
```ts
registerInternalHook("agent:bootstrap", (event) => {
  const context = event.context as AgentBootstrapHookContext;
  if (context.sessionKey.includes("coding")) {
    context.bootstrapFiles.push({
      path: "CODING_GUIDELINES.md",
      content: fs.readFileSync("...").toString()
    });
  }
});
```

**Inject real-time context:**
```ts
on("before_prompt_build", (event, ctx) => {
  return {
    prependContext: `当前时间：${new Date().toISOString()}`
  };
});
```

---

## Key Lesson from the Author

The thread started with a mistake: the author looked at only `bootstrap-hooks.ts` and concluded "only 1 hook type can modify Bootstrap." A user corrected them repeatedly. The lesson:

> "文档和代码都要看 — 文档告诉你'是什么'，代码告诉你'为什么'。"
> Documentation tells you *what*. Code tells you *why*.

---

## Relevance to Ray

- **Workshop/ebook:** Perfect deep-dive module on how OpenClaw's context system actually works
- **Bob's setup:** `bootstrap-extra-files` is likely how CONTEXT.md gets injected — worth verifying
- **Plugin development:** `before_prompt_build` = real-time context injection (time, calendar, weather) without touching workspace files
- Next article from same author: "龙虾的prompt结构 — hook机制对于prompt的影响" (watch for it)

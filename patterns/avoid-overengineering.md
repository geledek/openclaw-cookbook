---
title: "OpenClaw 差生文具多：你可能不需要4个Workspace"
author: "@frxiaobei"
source_url: "https://x.com/frxiaobei/status/2027759977314848792"
source_type: twitter-thread
date_saved: 2026-02-28
date_published: 2026-02-28
tags: [openclaw, ai-agents, automation, workshop, productivity]
summary: "Why most OpenClaw users over-engineer with multiple workspaces when one workspace + skills handles 90% of use cases. Uses Coase's transaction cost theory to argue: only split agents when coordination cost < parallelism benefit."
language: zh
---

# OpenClaw 差生文具多：你可能不需要4个Workspace

## Key Takeaways

- Most multi-agent setups fail not from model capability but from **structural over-engineering** — coordination costs exceed benefits
- Adam Smith's division of labor works for factories, but Coase's transaction cost theory applies to AI agents: split only when internal coordination cost = external transaction cost
- Hidden costs of multi-agent: context loss, format alignment, state sync, error propagation
- GitHub's blog "Multi-agent workflows often fail": implicit assumptions between agents about state/sequence/format cause system failures
- **The right sequence**: (1) Make one workspace work well → (2) Extend with Skills → (3) Split only at real bottlenecks
- Real reasons to split: true parallelism (independent tasks), hard isolation (permissions), context window overflow
- If you split: explicit handoff checklists, three logs (action/rejection/handoff), near-miss summaries

## When Multi-Agent Actually Helps

- Parallel coding: frontend + backend simultaneously (different codebases, low coupling)
- NOT: sequential tasks that could be skills/tools on one agent

## The "One-Person Company" Analogy

Better tools (Vercel, Supabase, Stripe, ChatGPT) reduced the need for team size. Similarly, OpenClaw's Skill system extends one agent's capability without the coordination overhead of multiple agents.

## Original Content

一个反直觉的观察：很多人刚上手OpenClaw就急着配置一堆workspace。架构图画得漂亮，角色分工清晰、职责边界明确。然后每个workspace都空空如也，Coordinator自己就能干完所有事。

差生为什么文具多？因为买文具比写作业容易，整理文具比解题愉快。

科斯的问题：当「拆成多个Agent的收益」>「协调成本」，才值得拆。否则，就是差生文具多。

在你急着配置第二个workspace之前，问自己：
1. 一个workspace + skills真的做不到吗？
2. 拆了之后，协调成本你准备好了吗？
3. 你是在解决问题，还是在享受「设计复杂系统」的快感？

---
title: "OpenClaw：主人，我也想玩app — 60分钟技能通关指南"
author: "@onehopeA9"
source_url: "https://x.com/onehopea9/status/2027729025414865251"
source_type: twitter-thread
date_saved: 2026-03-01
date_published: 2026-03-01
tags: [openclaw, ai-agents, automation, productivity, workshop]
summary: "Step-by-step 60-minute guide for OpenClaw beginners — 4 levels from security baseline to combined workflows. Covers skill-vetter, weather, search (Tavily/multi-search-engine), self-improving-agent, proactive-agent, gog (Google Workspace), GitHub integration. Includes the phone analogy: deploying OpenClaw = phone without apps."
language: zh
---

# OpenClaw：60分钟技能通关指南

## Core Analogy

OpenClaw without Skills = a phone that can only call and text. Skills = the apps that make it useful. ClawHub has 12,325 skills (as of 2026.2.28), but most beginners only need a handful.

## The 3 Failure Scenarios (Why 90% Quit)

1. Deploy → ask it to check email → "I can't access your inbox" → disappointment
2. Install 20 skills at once → can't configure them, don't know how to use them
3. Want to do real work but don't know which skills or what order

## Level 1: First 10 Minutes — Security + First Win

**Security first: skill-vetter**
- Feb 2026: Koi Security audit found 341 malicious skills on ClawHub
- ClawHub cleaned 2,419 suspicious entries overnight
- Always scan before installing: `"用 skill-vetter 扫描 <skill_name>"`

**First success: weather**
- Zero config, no API key, 100% success rate
- Builds confidence before tackling harder skills

## Level 2: 15-30 Minutes — Internet Access + Intelligence

**Search capability (choose one):**
- **Multi Search Engine** — no API key needed, 17 search engines, but noisy results
- **Tavily Search** — needs API key (free 1000/month), AI-optimized structured results

**Intelligence boost:**
- **self-improving-agent** — records failures, learns from mistakes, avoids repeating errors
- **proactive-agent** — breaks complex tasks into steps, identifies dependencies, warns about problems

## Level 3: 30-45 Minutes — Choose Your Path

**Path A: Office workers → gog (Google Workspace)**
- Gmail, Calendar, Drive, Docs, Sheets via OAuth
- Test: check unread email, add calendar event, create doc

**Path B: Developers → GitHub + summarize**
- Search repos, manage issues, summarize READMEs
- Test: search OpenClaw projects by stars, summarize a README

## Level 4: 45-60 Minutes — Combined Workflows

**Task 1: Research + Report** (all users)
- multi-search → tavily deep → summarize → 500-word report in 15-20 min (vs 1-2 hours manual)

**Task 2: Office Automation** (office workers)
- gog check email → draft urgent replies → generate daily report in 10-15 min

**Task 3: Code Research** (developers)
- GitHub search → summarize top 3 READMEs → comparative analysis in 15-20 min

## 60-Minute Checklist
- [ ] skill-vetter installed
- [ ] weather works
- [ ] Real-time search works (Tavily or multi-search)
- [ ] AI can plan tasks (proactive-agent)
- [ ] 2+ productivity tasks completed (gog or GitHub)
- [ ] 1 combined workflow completed

## Security Note: ClawHavoc Incident (Dec 2025)
Malicious skills attacked by: reading API keys from env vars, uploading user data to external servers, executing unauthorized system commands. Always vet before installing.

---
title: "Mac mini x OpenClaw 保姆级配置教程 (全网最简单)"
author: "@pluvio9yte (雪踏乌云)"
source_url: "https://x.com/pluvio9yte/status/2027428387937996998"
source_type: twitter-thread
date_saved: 2026-03-01
date_published: 2026-02-27
tags: [openclaw, ai-agents, self-hosted, automation, workshop]
summary: "Step-by-step Mac mini OpenClaw setup tutorial for Chinese users. Key trick: install Claude Code FIRST, then use it to fix any OpenClaw issues. Covers Homebrew→Node→Claude Code→OpenClaw→Telegram bot setup→proxy config→model config→UU Remote for headless access. Targets users without official model subscriptions using third-party API providers."
language: zh
---

# Mac mini x OpenClaw 保姆级配置教程

## Key Insight: Install Claude Code First

The smartest tip: install Claude Code before OpenClaw, so if anything breaks during setup, you can ask Claude Code to fix it.

## Setup Flow

1. **Dependencies**: Homebrew → Node.js
2. **Claude Code**: `npm install -g @anthropic-ai/claude-code` + set API base URL/key
3. **OpenClaw**: `curl -fsSL https://... | bash` → `openclaw onboard`
4. **Model config**: Skip official model login if no subscription; have Claude Code configure third-party API provider instead
5. **Telegram bot**: Create via @BotFather (3 minutes), give token to Claude Code with "帮我配置到OpenClaw中"
6. **Proxy**: If behind GFW, enable TUN mode in Clash Verge, then tell Claude Code "帮我配置OpenClaw的环境，使其适配目前的网络代理"
7. **Remote access**: UU Remote for headless Mac mini control from phone/laptop

## Model Options Mentioned

- Claude Sonnet/Opus (strongest for OpenClaw)
- Author runs a semi-charity reverse-proxy station: ¥15 for $100 worth of API calls (AWS Kiro reverse, unstable)
- AnyRouter: free with LinuxDo login, 25$/day sign-in bonus
- Alternatives: GPT-5 (Codex), GLM-5, MiniMax, Kimi (weaker but cheaper)

## China-Specific Notes

- Proxy/VPN required for Telegram
- Third-party API providers are the norm (no direct Anthropic/OpenAI access)
- Mac mini as 24/7 server is popular in Chinese OpenClaw community
- UU Remote for managing headless setup without monitor

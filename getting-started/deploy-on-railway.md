---
id: workshop-railway-deployment-guide
title: "Deploy OpenClaw on Railway — Beginner Guide"
source_type: internal
date_saved: 2026-02-28
tags: [openclaw, workshop, self-hosted, singapore]
category: research/ai
summary: Step-by-step guide for workshop participants to deploy OpenClaw on Railway in under 20 minutes. Cloud-based, no Mac mini needed.
---

# Deploy OpenClaw on Railway — Beginner Guide

*Target: workshop participants with no prior OpenClaw experience*
*Time: ~15-20 minutes*
*Cost: ~$5/month (Railway Hobby plan)*

---

## What you need before starting

- Laptop (Mac, Windows, Linux — doesn't matter)
- Credit card for Railway ($5/month, cancel anytime)
- Telegram account
- An AI API key — pick one:
  - **Anthropic Claude** — claude.ai/api (recommended, best results)
  - **OpenAI** — platform.openai.com
  - **OpenRouter** — openrouter.ai (cheapest, free tier available)

---

## Step 1: Create a Telegram bot (5 min)

1. Open Telegram, search for **@BotFather**
2. Send `/newbot`
3. Give it a name (e.g. "My OpenClaw Bot")
4. Give it a username ending in `bot` (e.g. `myopenclawbot`)
5. BotFather gives you a **token** — looks like `7123456789:AAFxxx...`
6. Save this token — you'll need it in Step 3

---

## Step 2: Deploy on Railway (5 min)

1. Go to **railway.app** and sign up (GitHub login is easiest)
2. Click **"Deploy from template"**
3. Search for **"openclaw"** or use this direct link:
   `railway.app/template/openclaw`
4. Click **"Deploy Now"**
5. Railway will ask you to connect your GitHub account — do it
6. Wait ~2 minutes for the build to finish (green checkmark = done)

---

## Step 3: Configure your agent (5 min)

Once deployed, go to your Railway project → **Variables** tab. Add these:

| Variable | Value |
|---|---|
| `TELEGRAM_BOT_TOKEN` | Your token from Step 1 |
| `ANTHROPIC_API_KEY` | Your Claude API key |
| `AGENT_NAME` | Whatever you want to call your agent |

Then click **Redeploy** (top right). Takes ~1 minute.

---

## Step 4: Test it (2 min)

1. Open Telegram
2. Search for your bot username (e.g. `@myopenclawbot`)
3. Send `/start`
4. Say hello

If it responds — you're live. Your agent is running 24/7.

---

## What you have now

- An AI agent connected to Telegram
- It runs in the cloud on Railway (no laptop needed)
- It responds to messages, can browse the web, remember things
- Ready for the hands-on portion of the workshop

---

## Common issues

**Bot doesn't respond after /start**
→ Check Railway logs (your project → Deployments → View Logs)
→ Usually a wrong token or missing API key

**"Unauthorized" error in logs**
→ Telegram token is wrong — copy it again from BotFather

**Build failed on Railway**
→ Template may need a manual trigger — click "Deploy" again

**API key error**
→ Make sure there are no spaces before/after the key in Railway Variables

---

## Cost breakdown

| Item | Cost |
|---|---|
| Railway Hobby plan | $5/month |
| Claude API (light use) | ~$1-5/month |
| **Total** | **~$6-10/month** |

You can pause the Railway deployment when not using it to save money.

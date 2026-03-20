---
id: workshop-troubleshooting-cheatsheet
title: "OpenClaw Troubleshooting Cheatsheet — Workshop Edition"
source_type: internal
date_saved: 2026-02-28
tags: [openclaw, workshop, ai-agents, singapore]
category: research/ai
summary: Quick fixes for the top issues beginners hit during OpenClaw setup and first use. Written for the hands-on portion of the Singapore workshop.
---

# OpenClaw Troubleshooting Cheatsheet

*For the hands-on portion of the workshop. Keep this open.*

---

## Bot doesn't respond at all

**Most likely cause:** wrong Telegram token or deployment not running.

**Fix:**
1. Open Railway → your project → Deployments
2. Click the latest deployment → View Logs
3. Look for red errors at the top
4. If you see `Unauthorized` → your Telegram token is wrong (copy it fresh from @BotFather)
5. If logs are empty → the service crashed, click "Redeploy"

---

## Bot responds with "I don't have access to that" or refuses tasks

**Cause:** the model API key is wrong or has no credits.

**Fix:**
1. Railway → Variables → check your `ANTHROPIC_API_KEY` or `OPENAI_API_KEY`
2. Make sure there are no spaces or quotes around the key
3. Log into the API provider and confirm you have credits
4. Redeploy after fixing

---

## Bot keeps forgetting things between conversations

**Cause:** memory not configured, or using the default in-memory store.

**Fix:**
This is normal for a fresh setup. To enable persistent memory:
- Your deployment needs a volume attached in Railway (Storage tab)
- Or use the LanceDB memory plugin if configured

For the workshop, don't worry about this yet — focus on getting responses working first.

---

## Skill isn't being triggered

**Cause:** the description in SKILL.md doesn't match what you're saying.

**Fix:**
1. Open your SKILL.md
2. Read the `description` field — your message needs to match that intent
3. Try saying exactly what the description says
4. If it still doesn't trigger, the skill folder may not be in the right place

Check the skill is at: `workspace/skills/your-skill-name/SKILL.md`

---

## "Rate limit exceeded" error

**Cause:** too many API calls too fast.

**Fix:**
- Wait 60 seconds and try again
- If using a free API tier, you may have hit the monthly limit
- Switch to a different model provider in Railway Variables

---

## Railway build fails

**Cause:** usually a code error in a skill file, or a bad environment variable.

**Fix:**
1. Railway → Deployments → click failed deployment → View Logs
2. Look for the first red error (everything after that is usually noise)
3. Common culprits: syntax error in a `.json` or `.md` file, missing variable
4. Fix the issue, push to GitHub or redeploy manually

---

## Bot responds but answers are very short / low quality

**Cause:** using a weak model or the system prompt isn't loading.

**Fix:**
1. Check which model is set in your config (Railway Variables → `MODEL` or equivalent)
2. Try Claude Sonnet or GPT-4o instead of mini/small variants
3. Make sure your AGENTS.md or SOUL.md loaded correctly

---

## "I can't browse the web" or web search not working

**Cause:** no search API key configured.

**Fix:**
- Add `BRAVE_API_KEY` to Railway Variables (get free key at brave.com/search/api)
- Or use the built-in web fetch which doesn't need a key (just slower)

---

## Workshop assistant agent is down / not responding

**Cause:** Ray's agent may be overloaded or restarting.

**Fix:**
- Wait 2 minutes and try again
- In the meantime, ask the person next to you or check this cheatsheet
- Ray is your fallback for anything not covered here

---

## General debugging rule

When something goes wrong, always check in this order:
1. **Railway logs** — what does the error actually say?
2. **Variables** — is the right key/token set?
3. **File location** — is the skill/config where OpenClaw expects it?
4. **Redeploy** — sometimes a fresh start fixes transient issues

Most problems are either a wrong token, a missing API key, or a file in the wrong place. Start there.

---
id: workshop-skill-writing-template
title: "Write Your First OpenClaw Skill — 5-Minute Template"
source_type: internal
date_saved: 2026-02-28
tags: [openclaw, workshop, ai-agents, singapore]
category: research/ai
summary: Dead-simple template for writing an OpenClaw skill. Covers the minimum structure needed, with three ready-to-use examples participants can adapt.
---

# Write Your First OpenClaw Skill — 5-Minute Template

A skill is just a folder with a `SKILL.md` file inside. That's it.

---

## The minimum structure

```
skills/
└── my-skill/
    └── SKILL.md
```

---

## SKILL.md template

Copy this, fill in the blanks:

```markdown
---
name: [skill-name]
description: [One sentence: what does this skill do and when should it activate?]
---

# [Skill Name]

## What you do

[2-3 sentences explaining the task. Be specific. "When Ray sends a URL, 
save it to the library" is better than "process content".]

## How to do it

1. [Step 1]
2. [Step 2]
3. [Step 3]

## Output format

[What should the response look like? A summary? A file? A message?]

## Examples

**Input:** [example of what the user sends]
**Output:** [example of what the agent should do/say]
```

---

## Three ready-to-use examples

### Example 1: Daily news digest

```markdown
---
name: news-digest
description: Summarize today's top news when user asks for a briefing.
---

# Daily News Digest

## What you do
When the user asks for news, today's briefing, or morning update — 
search for the top 5 headlines relevant to AI, Singapore, and markets.
Summarize each in 1-2 sentences. Keep it under 300 words total.

## How to do it
1. Search for "AI news today", "Singapore news today", "market news today"
2. Pick the 5 most relevant/interesting headlines
3. Write a short summary for each
4. End with one "thing to watch" today

## Output format
Short bullets. No filler. Lead with the most important story.
```

---

### Example 2: Save a link to my library

```markdown
---
name: save-link
description: When user sends a bare URL, save it to the personal library.
---

# Save Link to Library

## What you do
When the user sends just a URL (no other text), fetch the content,
summarize it, and save it as a markdown file in the library folder.

## How to do it
1. Fetch the URL content
2. Write a 2-3 sentence summary
3. Identify 3-5 tags that describe the content
4. Save to library/saves/ as YYYY-MM-DD__slug.md
5. Confirm: "Saved: [title] → [path]"

## Output format
Single confirmation message with title and file path.
```

---

### Example 3: Meeting prep

```markdown
---
name: meeting-prep
description: When user mentions an upcoming meeting, prepare a briefing.
---

# Meeting Prep

## What you do
When the user says "I have a meeting with [person/company] about [topic]",
research the person/company and prepare a 1-page briefing.

## How to do it
1. Search for the person or company name
2. Find: role, background, recent news, anything relevant to the topic
3. Write a briefing: who they are, what they care about, 3 smart questions to ask

## Output format
Short briefing — 200 words max. Bullet points where possible.
```

---

## Tips for writing good skills

**Be specific about the trigger.** "When the user sends a URL" is clear. "When relevant" is not.

**One skill, one job.** Don't try to do 5 things in one SKILL.md. Make 5 skills.

**Write the output format explicitly.** Your agent will match whatever format you describe.

**Test it immediately.** After saving the skill, send the exact trigger phrase and see what happens. Adjust the instructions based on what you get.

---

## Where to put your skill

On Railway, you can't easily edit files directly. Two options:

1. **Connect a GitHub repo** — put your skills folder there, Railway pulls from it
2. **Use the OpenClaw web UI** — some versions have a file editor at your Railway URL
3. **Edit via Telegram** — ask your agent to create the skill file for you (it has file access)

Option 3 is the most beginner-friendly: just describe the skill you want and ask Bob to write and save the SKILL.md file.

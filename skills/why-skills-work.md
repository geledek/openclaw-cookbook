---
id: 2026-02-26__gabrielchua-skills-explained-markdown-folders
title: "Skills, Explained: Why Folders of Markdown Files Are So Effective"
source_type: x
source_url: "https://x.com/gabrielchua/status/2026687426593436066"
author: "Gabriel Chua (@gabrielchua)"
date_saved: 2026-02-26
date_published: 2026-02-25
tags: [openclaw, ai-agents, productivity, automation, twitter-thread, workshop]
category: saves/x
summary: "Gabriel Chua's deep explainer on why Skills (markdown folders of prompts + resources) beat ad-hoc prompting — covering progressive disclosure, modularity, and team knowledge codification."
---

# Skills, Explained: Why Folders of Markdown Files Are So Effective

> Gabriel Chua's deep explainer on why Skills (markdown folders of prompts + resources) beat ad-hoc prompting — covering progressive disclosure, modularity, and team knowledge codification.

Most people who use AI tools have, at some point, ended up with a prompt that "mostly works." It might be a checklist, a workflow, or a set of rules like "don't do this" and "always check that." You tweak it a few times until the output looks right, and then you save it somewhere so you can reuse it later.

Over time, that prompt slowly changes. You add another rule after something breaks. You delete a line that no longer seems necessary. Someone else copies it into a different project and modifies it slightly. Eventually, there are three or four versions of the same process floating around, and no one is quite sure which one produces the output you actually want.

A skill is essentially a way of formalizing that habit. At its core, a skill is just a collection of prompts written down in a markdown file, sometimes with additional reference files or scripts that the model can use.

In that sense, it is not fundamentally different from prompting. It is prompting, made reusable.

Instead of keeping instructions in a document or a notes app, you place them into a folder, usually as a skill.md file, alongside any examples, templates, or scripts that make the workflow actually work end to end. That folder becomes something the agent can use as a repeatable process rather than a one-off attempt. Skills are a way of organizing prompts and resources in a way that is intuitive to models but also to humans, since we still need to manage collections of workflows across projects and teams.

## Why Prompting Still Matters

You might hear people say that prompting matters less now because models are getting better. That is true in the sense that you do not need to discover some magical phrasing or formatting trick to make the model behave.

But like talking to any human, clear and unambiguous instructions still help. The model cannot read your mind. It can only perform a task based on the instructions you provide and the context it receives.

A skill is simply a way of doing the prompting work once instead of rediscovering it every time. Instead of asking every user to rediscover the right set of instructions each time, the workflow is written down once in a way that reflects how the task is actually meant to be done. With a well-designed skill, the person invoking it can give much simpler instructions and still get consistent results.

## What Actually Changes When You Use a Skill

There are three main conceptual differences between reusable prompts and skills.

### 1. Progressive Disclosure

You are usually not loading the entire workflow into the model's context from the beginning. Each skill comes with a short description that explains what it is for. The agent can look at that description and decide whether the skill is relevant to the task it is trying to complete. Only when it determines that the skill applies does it inspect the full instructions in the skill.md file, or access appendices such as a reference.md, scripts, MCP servers, or APIs.

In practice, this behaves like a glossary of available workflows. The agent knows what tools are available, but only opens the detailed instructions when needed.

It's a bit like going to a library. You start with the catalogue to see what books exist on a topic. Once you've found the relevant book, you don't read the whole thing — you flip to the index or glossary to locate the exact chapter or page you need. The detailed instructions stay closed until they're actually relevant to the task at hand.

### 2. Structure

Modern models are quite good at traversing file systems. The fact that something lives in a particular folder already conveys information about how it should be used. In the same way that you organize your own desktop by project or purpose, the structure of a skills directory yields context to the model.

This also introduces modularity. A skill becomes a packaged unit of workflow that can be reused, shared, versioned, or composed with other skills. Rather than copy-pasting slightly different versions of the same prompt into every project, you can treat workflows as modules that can be distributed across projects and between team members.

### 3. Access to Additional Resources

A reusable prompt is usually limited to whatever you remembered to paste in. A skill, on the other hand, can include appendices, examples, scripts, evaluation rubrics, or even executable tooling that the model can use while carrying out the task. This might include calling MCP servers, running a CLI script, or referencing internal guidelines captured in a reference.md.

In that sense, a skill is not just telling the model what to do, but also giving it access to the supporting materials needed to do it well. The workflow becomes grounded not only in instructions, but in context and tools.

## Why This Matters for Teams — Big or Small

Much of what counts as expertise inside an organization is not a set of facts but a sequence of habits and checks. It is knowing what to verify before deploying something, what assumptions need to be tested, and what kind of output is considered acceptable.

Normally this knowledge is passed around informally or buried in outdated documentation. With skills, that procedural knowledge can be packaged into something the agent can follow directly. In practice, this allows teams to codify and amplify expertise that would otherwise remain tacit or inconsistently applied. Everyone ends up running the same steps, and new team members do not have to reverse engineer the process from scratch.

This applies whether you are in a large enterprise or working in a small team. In both cases, skills allow you to standardize how recurring tasks are performed without relying on personal prompting styles or institutional memory. When the process changes, you update the skill once rather than asking everyone to adjust their own prompts.

## In Practice

Skills do not expand what the model is capable of doing, but they make it easier to perform repeatable tasks in a predictable way. They let you codify and share processes instead of relying on memory or copy-paste.

If you find yourself repeating the same process more than a few times, that is usually a sign that it can be turned into a skill. What skills introduce is not new capability, but a way to turn tacit process into something explicit, shareable, and consistently executable.

> Disclaimer: This article reflects Gabriel Chua's own views on skills. Intended as an intuitive explanation, not official product documentation.

❤️ 647  🔁 51  💬 8

---
*Saved: 2026-02-26 | Source: x.com (@gabrielchua)*

# Contributing to OpenClaw Cookbook

## What we're looking for

- **Production war stories** — what actually worked or failed when running OpenClaw
- **Non-English community content** — especially Chinese, Japanese, Korean OpenClaw writing
- **Cost/performance benchmarks** — real numbers, not marketing
- **Security analyses** — CVEs, attack surfaces, hardening guides
- **Comparison pieces** — honest assessments of OpenClaw vs alternatives

## Format

Each file should have YAML frontmatter:

```yaml
---
title: "Your Title"
author: "Author Name (@handle)"
source_url: "https://..."
date_saved: 2026-03-20
tags: [openclaw, relevant-tags]
summary: "One-line summary"
language: en  # or zh, ja, ko, etc.
---
```

Followed by the content in markdown.

## Where to put it

| Content type | Folder |
|---|---|
| Setup/install guides | `getting-started/` |
| Production patterns | `patterns/` |
| Skill development | `skills/` |
| Under-the-hood analysis | `architecture/` |
| Case studies | `real-world/` |
| Tool comparisons | `comparisons/` |
| Cost optimization | `cost/` |
| Fix guides | `troubleshooting/` |
| Industry takes | `perspectives/` |

## Process

1. Fork the repo
2. Add your file to the right folder
3. Open a PR with a brief description

We'll review and merge within a few days. No bureaucracy.

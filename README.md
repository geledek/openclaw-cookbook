# 🦞 OpenClaw Cookbook

A practitioner's field guide to OpenClaw — real patterns, real use cases, real cost.

Not another link directory. This is full-text content: deep dives, source code analyses, translated Chinese community wisdom, workshop materials, and lessons from running OpenClaw in production daily.

**Bilingual** 🇬🇧🇨🇳 — many entries include both English and Chinese content, reflecting the vibrant Chinese OpenClaw community that's producing some of the best practical writing on agents right now.

---

## 📖 Contents

### [Getting Started](getting-started/)
New to OpenClaw? Start here.

| Guide | What you'll learn |
|---|---|
| [Before You Start](getting-started/before-you-start.md) | Miles Deutscher's 3-phase framework — don't spend money before doing these 3 things |
| [Learning Path](getting-started/learning-path.md) | Structured beginner → advanced path (Jason Zhu) |
| [Mac Mini Setup](getting-started/mac-mini-setup.md) | Step-by-step Mac mini tutorial 🇨🇳 — the "install Claude Code first" trick |
| [Deploy on Railway](getting-started/deploy-on-railway.md) | Cloud deployment in 20 min, ~$5/month |
| [Workshop Outline](getting-started/workshop-outline.md) | 2-hour beginner workshop structure |

### [Skills](skills/)
Skills are what make OpenClaw useful. These explain what they are, how to write them, and how to go deep.

| Guide | What you'll learn |
|---|---|
| [Why Skills Work](skills/why-skills-work.md) | Why markdown folders beat ad-hoc prompting (Gabriel Chua) |
| [Write Your First Skill](skills/write-your-first-skill.md) | 5-minute template with 3 ready-to-use examples |
| [60-Min Skill Guide](skills/60-min-skill-guide.md) | From zero to combined workflows in 60 minutes 🇨🇳 |
| [Bootstrap Hooks](skills/bootstrap-hooks.md) | Code-traced teardown of OpenClaw's 4 bootstrap mechanisms 🇨🇳 |

### [Patterns](patterns/)
Production patterns from people who actually run OpenClaw daily.

| Guide | What you'll learn |
|---|---|
| [Memory Architecture](patterns/memory-architecture.md) | 5-layer memory system based on cognitive science (Ray Wang) 🇨🇳 |
| [Memory Plugins Compared](patterns/memory-plugins-compared.md) | 7 memory systems benchmarked — native vs Supermemory vs mem0 vs others 🇨🇳 |
| [Personal Brain OS](patterns/personal-brain-os.md) | 80+ file workspace that gives agents full personal context |
| [Avoid Overengineering](patterns/avoid-overengineering.md) | Why you probably don't need 4 workspaces (Coase's theory applied) 🇨🇳 |
| [Multi-Agent Setup](patterns/multi-agent-setup.md) | 7-step system for autonomous multi-agent OpenClaw |
| [Anthropic Academy Optimizations](patterns/anthropic-academy-optimizations.md) | 17 changes after completing Anthropic's 13 courses 🇨🇳 |

### [Architecture](architecture/)
For those who want to understand what's under the hood.

| Guide | What you'll learn |
|---|---|
| [Source Code Analysis](architecture/source-code-analysis.md) | 2-day deep dive: 4-layer architecture, comparison with AutoGPT/LangChain/CrewAI 🇨🇳 |
| [System Prompt Deep Dive](architecture/system-prompt-deep-dive.md) | The 16k token system prompt dissected — every layer exposed 🇨🇳 |
| [Claws: New AI Layer](architecture/claws-new-ai-layer.md) | Karpathy's take: claws as orchestration layer, security concerns, NanoClaw |

### [Real-World Use Cases](real-world/)
Verified by actual users, not hypothetical.

| Case | What it covers |
|---|---|
| [13 Verified Use Cases](real-world/13-verified-use-cases.md) | Community-curated across 4 categories — each tested for at least 1 day 🇨🇳 |
| [Eddie: $73k/month B2C](real-world/eddie-73k-month.md) | OpenClaw agent automating content + influencer outreach for app business |
| [Howie's 6 Use Cases](real-world/howie-6-use-cases.md) | Calendar, typesetting, daily digest, reading OS — "Personal Context is the only moat" 🇨🇳 |
| [Company Notes with AI](real-world/company-notes-with-ai.md) | Vault-based knowledge system turning meeting transcripts into org brain |

### [Comparisons](comparisons/)
Honest assessments — including reasons NOT to use OpenClaw.

| Guide | What you'll learn |
|---|---|
| [OpenClaw vs Cowork vs n8n](comparisons/openclaw-vs-cowork-vs-n8n.md) | Reddit community consensus: when to use which |
| [Toy or Tool?](comparisons/toy-or-tool.md) | 30+ real cases analyzed, 14+ CVEs covered (incl. CVE-2026-33579), security reality check 🇨🇳 |
| [Claude Desktop Alternative](comparisons/claude-desktop-alternative.md) | Replicate 80% of OpenClaw features without command line 🇨🇳 |
| [Who Doesn't Need OpenClaw](comparisons/who-doesnt-need-openclaw.md) | Contrarian take: 99% aren't ready — and why that's fine 🇨🇳 |

### [Cost](cost/)

| Guide | What you'll learn |
|---|---|
| [Reduce Costs by 90%](cost/reduce-costs-90-percent.md) | Model routing, prompt caching, local models, ClawRouter |

### [Troubleshooting](troubleshooting/)

| Guide | What you'll learn |
|---|---|
| [Common Issues](troubleshooting/common-issues.md) | Quick fixes for top beginner issues during setup and first use |

### [Perspectives](perspectives/)
Bigger-picture thinking on where agents are headed.

| Piece | What it covers |
|---|---|
| [Karpathy: Multi-Agent Research](perspectives/karpathy-multi-agent.md) | 8 agents, 4 GPUs — "it doesn't work yet" and why |
| [SaaS is Dead, AaaS Forever](perspectives/saas-dead-aaas-forever.md) | The SaaSpocalypse: $285B wiped, agent market at 46% CAGR 🇨🇳 |
| [OpenFang: Agent Workflows](perspectives/openfang-workflow-standardization.md) | From agent ability to agent organization — the "Hands" concept 🇨🇳 |
| [Chinese Community Top 12](perspectives/chinese-community-top-12.md) | Curated best-of from 100+ Chinese OpenClaw posts 🇨🇳 |

### [Workshops](workshops/)
Materials from live workshops.

### [Daily Scans](daily-scans/)
Daily signal digests — top posts, articles, and community discussions curated from Reddit, HN, DEV.to, and X.

| Scan | Highlights |
|---|---|
| [2026-04-12](daily-scans/2026-04-12.md) | GLM-5.1/4.7 as new model defaults · Gemma 4 on MacBook Air 16GB · @steipete on Anthropic ban · bypass culture |
| [2026-04-11](daily-scans/2026-04-11.md) | Anthropic cuts OpenClaw from subscriptions · CVE-2026-33579 · Claude Code/OpenClaw convergence _(catch-up: Mar 29–Apr 11)_ |
| [2026-03-28](daily-scans/2026-03-28.md) | Breaking update migration pain · Forbes/NVIDIA enterprise legitimacy · WebTop zero-install onboarding |
| [2026-03-27](daily-scans/2026-03-27.md) | |
| [2026-03-26](daily-scans/2026-03-26.md) | |
| [2026-03-25](daily-scans/2026-03-25.md) | |
| [2026-03-24](daily-scans/2026-03-24.md) | |
| [2026-03-23](daily-scans/2026-03-23.md) | |
| [2026-03-22](daily-scans/2026-03-22.md) | Security & isolation dominates · Red Hat BYOA integration · 215k GitHub stars |

---

## 🇨🇳 Why Chinese Content?

The Chinese OpenClaw community is producing some of the most thorough, practical content on AI agents — source code deep dives, architectural analyses, honest "don't bother" takes. Most of this doesn't exist in English. We translate and curate the best of it here.

Entries marked 🇨🇳 are primarily in Chinese with English summaries.

## Contributing

Found a great OpenClaw article, thread, or guide? Open an issue or PR. We especially welcome:
- Production war stories (what actually worked/failed)
- Non-English community content
- Cost/performance benchmarks
- Security analyses

## About

Maintained by [Ray Han](https://rayhan.ai) — running OpenClaw in production since early 2026. This cookbook is a living document updated through automated content scanning, with daily signal digests in [`daily-scans/`](daily-scans/).

Also see: [awesome-openclaw](https://github.com/SamurAIGPT/awesome-openclaw) for a comprehensive link directory.

## License

Content in this repository is shared under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). Original authors are credited in each file's frontmatter.

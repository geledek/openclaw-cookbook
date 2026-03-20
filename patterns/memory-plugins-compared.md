---
title: "OpenClaw 记忆增强生态系统 — 7大系统深度对比"
author: "@zstmfhy (AI奶爸)"
source_url: "https://x.com/zstmfhy/status/2027927177090797994"
source_type: twitter-thread
date_saved: 2026-03-01
date_published: 2026-03-01
tags: [openclaw, ai-agents, embeddings, rag, llm]
summary: "Deep comparison of 7 memory enhancement systems for OpenClaw. Native memory scores 58.3% recall on MemoryBench. Covers Supermemory (85.9%), mem0 (48.3k stars, +26% vs OpenAI), OpenViking, EvoMap, Nowledge, Memori (SQL-native, 80-90% cheaper), MemOS (+159% on time reasoning). Includes 4-quadrant matrix, scenario decision trees, cost analysis, and Graph Memory trend prediction."
language: zh
---

# OpenClaw 记忆增强生态系统

## The Problem

OpenClaw native memory: 58.3% recall accuracy on MemoryBench — 2 out of 5 conversations "forget."

## The 7 Systems

### 1. Supermemory (85.9% MemoryBench, 16.7k ⭐)
- Storage: Cloudflare KV + Vector DB + Graph Layer
- Key innovation: Hooks for implicit memory capture — no explicit tool calls needed
- Integration: MCP Server / OpenClaw Plugin / Claude Code Skill
- Cost: $20/month

### 2. mem0 (48.3k ⭐, largest community)
- Storage: Vector (24+ options) + Redis + Neo4j Graph
- Key innovation: Multi-level scopes (user/agent/run/app), multi-agent shared memory
- +26% accuracy vs OpenAI memory on LOCOMO benchmark
- Cloud ↔ Self-hosted seamless switch

### 3. OpenViking (Volcengine/ByteDance, 4.2k ⭐)
- Storage: AGFS (Agent File System) + vector index
- Key innovation: viking:// URI, visual retrieval tracing — no more RAG black box
- 6 memory categories: profile/preferences/entities/events/cases/patterns
- Enterprise: self-hosted, China data compliance

### 4. EvoMap (117 ⭐, emerging)
- Storage: Graph DB (phylogenetic tree) + decentralized network
- Key innovation: Genetic evolution of AI capabilities — one agent learns, millions inherit
- GEP Protocol fills gap between MCP (tools) and Skills (steps)
- Natural selection: low-quality memories auto-eliminated

### 5. Nowledge (closed source)
- 100% local — data never leaves device, on-device AI models
- BM25 + vector + GraphRAG hybrid
- Browser extension + global launcher (⌘⇧K)
- Risk: vendor lock-in (closed source)

### 6. Memori/GibsonAI (12.3k ⭐)
- SQL-native: SQLite/PostgreSQL/MySQL, NO vector DB
- Cost: 80-90% cheaper than vector solutions at scale
- 3-agent architecture: capture → analyze → select
- Key innovation: SQL simplicity, zero vendor lock-in, full audit

### 7. MemOS (6k ⭐, academic: Shanghai Jiao Tong/Zhejiang U)
- MemCube: self-contained memory units, 3 layers (Parametric/Activation/Plaintext)
- +159% on time reasoning vs OpenAI memory, +38.9% LOCOMO, 94% latency reduction
- Memory as OS resource: schedulable, migratable, governable

## 4-Quadrant Matrix

| | Cloud-native | Local-first |
|---|---|---|
| **Personal** | Supermemory (implicit), Nowledge (privacy) | Memori (SQL), EvoMap (evolution) |
| **Enterprise** | mem0 Platform (fast), OpenViking (file system) | mem0 Self-hosted (full), MemOS (OS-level) |

## Scenario Decision Trees

- **Privacy-sensitive**: Nowledge → Memori (SQLite) → mem0 Self-hosted
- **Multi-agent teams**: mem0 → MemOS → OpenViking
- **High-frequency personal**: Supermemory → Memori → mem0
- **Enterprise knowledge base**: OpenViking → mem0 Enterprise → MemOS

## Cost Insight
Memori (SQL-native) at scale = 10-20% of vector DB solutions. When conversations >1000/month, self-hosted beats SaaS.

## Trend Predictions
- Memory layer becoming standard infra for AI agents (like databases for web apps)
- Graph Memory will be standard for relationship-dense scenarios (>10k entities)
- "Edge Memory" emerging: store on device, sync only summaries to cloud
- Evolution from static RAG → memory layer → dynamic memory OS

## Core Decision: 3 dimensions
1. Privacy → cloud vs local
2. Collaboration scale → single vs shared
3. Budget → managed vs self-hosted

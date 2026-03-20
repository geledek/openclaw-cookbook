---
id: 2026-03-02__gosailglobal-openclaw-learning-path
title: "没人告诉你的OpenClaw学习路径 — Jason Zhu (@GoSailGlobal)"
source_type: x
source_url: "https://x.com/gosailglobal/status/2028305981722292345?s=46"
author: "Jason Zhu (@GoSailGlobal)"
date_saved: 2026-03-02
tags: [openclaw, ai-agents, tutorial, workshop, ebook]
category: saves/x
summary: "Structured OpenClaw learning path (beginner → advanced) covering Agentic AI concepts, platform setup, intermediate skills (memory, multi-agent, gateway HA), and the engineering experience required for mid/advanced levels."
---

# 没人告诉你的OpenClaw学习路径

> Structured OpenClaw learning path (beginner → advanced) covering Agentic AI concepts, platform setup, intermediate skills (memory, multi-agent, gateway HA), and the engineering experience required for mid/advanced levels.

## 一、何为Agentic AI

智能 AI ≠ RAG。智能体人工智能 ≠ RPA + LLM。

真正的智能体人工智能包括：
- 目标所有权
- 规划
- 记忆
- 工具使用
- 反馈回路
- 多智能体协调

它执行目标，而不仅仅是提示，而OpenClaw是目前最接近Agentic AI的。

## 二、OpenClaw基础认知

OpenClaw构成：
1. **渠道（Channels）** — 用户或应用发来请求的地方
2. **代理人（Agents）** — 处理请求的智能助手
3. **工具（Tools）** — 代理人用来完成任务的外部功能；Skills是工具的高级版，多个工具的封装集合
4. **模型（Models）** — 提供智能和决策的核心大脑
5. **平台（Platforms）** — 整个系统运行的基础设施
6. **网关与运维（Gateway & Ops）** — 中心枢纽，负责路由、安全和监控

## 三、平台选择

- 个人/简单高效 → MacOS 本机运行
- 安全隔离/测试 → 本机 Docker
- 大规模远程部署 → 服务器（从小 VPS 起步测试反爬配置）

## 四、OpenClaw部署

- 选项1：ChatGPT客户端 + Warp，一步步安装
- 选项2：Codex、Claude Code 一键安装
- 模型配置：先用国内minimax跑起来，再用 cc-switch 统一管理（`~/.cc-switch/config.json` 同步到服务器）

## 五、初级使用

1. 聊天、定时任务干活

## 六、中阶使用

1. 装上眼睛 — 让OpenClaw读X等前沿信息源
2. 权限管理 — 先紧后松
3. 模型兜底 — 中转站不稳定时有备用（稳定优先，贵一点可以）
4. Skills — 装上适合任务的手脚
5. 多Gateway — 避免单点宕机，实现自行修复（身体1）
6. 多Agent — 实现协作（身体2）
7. Memory机制（身体3）

---
*Saved: 2026-03-02 | Source: x.com/@GoSailGlobal*

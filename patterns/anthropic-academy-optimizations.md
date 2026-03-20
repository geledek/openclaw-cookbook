---
id: 2026-03-02__ohxiyu-anthropic-academy-17-changes
title: "看完 Anthropic Academy 13 门课后，我对 OpenClaw 系统做了 17 个改动 — @ohxiyu"
source_type: x
source_url: "https://x.com/ohxiyu/status/2028445432729506095?s=46"
author: "@ohxiyu"
date_saved: 2026-03-02
tags: [openclaw, ai-agents, llm, tutorial, productivity]
category: saves/x
summary: "Practical distillation of Anthropic Academy's 13 free courses into 17 actionable changes for Claude-based multi-agent systems — covering adaptive thinking, Think Tool, token optimization, prompt engineering, and MCP advanced features, ranked by ROI."
---

# 看完 Anthropic Academy 13 门课后，我对 OpenClaw 系统做了 17 个改动

> Practical distillation of Anthropic Academy's 13 free courses into 17 actionable changes for Claude-based multi-agent systems — adaptive thinking, Think Tool, token optimization, prompt engineering, and MCP advanced features, ranked by ROI.

## 一、3 句话总结

1. **Adaptive Thinking 是必须切换的**：Opus 4.6 的 `type: "adaptive"` + `effort` 参数让 Claude 自动判断思考深度，简单任务 0 thinking tokens，复杂任务全力思考——比固定 budget 省 30-50%。
2. **Think Tool 是 Agent 系统的隐藏武器**：在 tool use 密集场景添加一个 "think" 工具，让 Claude 在工具调用之间进行结构化推理，Anthropic 实测显著提升准确性和规则遵循率。
3. **MCP 三大高级特性被严重低估**：Sampling（server 反向调 LLM）、Roots（目录声明）、Elicitation（向用户提问）——大多数系统只用了 MCP 的 10%。

## 二、Extended Thinking 策略（最高 ROI）

❌ 旧（已废弃）：`{"thinking": {"type": "enabled", "budget_tokens": 32000}}`
✅ 新（推荐）：`{"thinking": {"type": "adaptive"}, "output_config": {"effort": "high"}}`

**effort 参数分级：**
- `low`：日常对话、状态查询、简报生成、简单路由
- `medium`：推文写作、信息整合、日常监控
- `high`：深度分析、代码生成、财务计算、复杂决策

**Think Tool（工具调用间的思考）**

Extended Thinking 是调用前思考，Think Tool 是调用间思考。二者互补。

```json
{
  "name": "think",
  "description": "Use this tool to think through complex problems step by step before taking action.",
  "input_schema": {
    "type": "object",
    "properties": {
      "thought": {"type": "string", "description": "Your step-by-step reasoning"}
    },
    "required": ["thought"]
  }
}
```

用 Think Tool：路由/调度、分析/研究、代码、权限检查类 Agent。
不用：纯创意输出、单步操作 Agent。

## 三、Token 优化

**Prompt Caching（最大 ROI）**
- Cache hit 只收 1/10 价格
- 静态内容前置，动态内容后置
- 可设 `"ttl": "1h"` 降低低频场景开销

**System Prompt 分层：**
核心身份（50 tokens）→ 关键规则（200 tokens）→ 参考信息（按需）

## 四、Prompt Engineering 精华

1. **XML 标签分离指令与数据** — `<instructions>` vs `<reference_data>`
2. **Speaking for Claude** — assistant 消息预填输出开头，格式错误率大降
3. **Few-shot 示例** — 格式敏感输出加 1-2 个示例，效果远超长篇描述
4. **防幻觉指令** — 事实类 Agent 必加："如果不确定，明确说'需要验证'"
5. **Prompt Chaining** — 复杂任务拆成多次调用，每步输出为下步输入

## 五、MCP 高级特性

- **Sampling** — server 反向调 LLM，server 端无需 API key
- **Roots** — 正式声明哪些目录对 LLM 可见，更安全
- **Elicitation** — MCP server 主动向用户提问，适合需要人工确认的场景

## 六、Agent 自动化模式

- **并行子 Agent** — 识别可并行子任务，同时 spawn
- **自动重试** — 第一次失败自动重试，第二次才通知用户；涉及资金/发送/删除的操作永远不重试
- **System Prompt 分层** — 全局规则 → Agent 级规则 → 任务级规则

## 七、优先行动清单（按 ROI）

🔴 今天就做：切换 Adaptive Thinking / 添加 Think Tool / 按 Agent 配置 Effort
🟡 本周做：XML 重构 System Prompt / SOUL 分层 / Few-shot 示例 / 防幻觉指令
🟢 有空再做：MCP Sampling/Roots/Elicitation / 并行 Agent / Prompt Caching

## 附：Anthropic Academy 课程推荐顺序

| 优先级 | 课程 | 耗时 |
|---|---|---|
| ⭐⭐⭐ | Prompt Engineering Tutorial | 2-3h |
| ⭐⭐⭐ | Extended Thinking | 1h |
| ⭐⭐ | Building with Claude API | 2h |
| ⭐⭐ | MCP Mastery | 2h |
| ⭐ | Claude Code in Action | 1h |

全部免费，有证书：https://anthropic.skilljar.com

---
*Saved: 2026-03-02 | Source: x.com/@ohxiyu*

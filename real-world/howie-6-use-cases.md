---
id: 2026-02-28__zen-lobster-openclaw-howie
title: "《禅与龙虾养殖技术》— Howie 龙虾 Agent 专题讲座笔记"
source_type: wechat
source_url: "https://mp.weixin.qq.com/s/m2M2zrw4OhxHJJlEQVREIg"
author: "Howie和小能熊"
date_saved: 2026-03-03
date_published: 2026-02-28
tags: [openclaw, ai-agents, productivity, wechat, automation, mcp]
category: saves/wechat
summary: "Howie's 3000-word distilled notes from his OpenClaw agent lecture: 6 use cases (calendar, typesetting, daily digest, reading OS), Personal Context as the only moat, and why token consumption is headed 1000x."
---

# 《禅与龙虾养殖技术》— Howie 龙虾 Agent 专题讲座笔记

> Howie's 3000-word distilled notes from his OpenClaw agent lecture: 6 use cases (calendar, typesetting, daily digest, reading OS), Personal Context as the only moat, and why token consumption is headed 1000x.

🦞龙虾养殖，一方面不难（复制粘贴），而且不需要"折腾"（我才用了几天），但回报巨大（直播里有实例）。

你只需要掌握"禅与龙虾养殖技术"（看这场直播）🤣

不开玩笑啦。昨晚的龙虾 agent 专题讲座，文字稿快两万字，现在提炼了 3000 字版本干货笔记。

> 主题：🦞龙虾Agent专题
>
> 主讲：howie.serious
>
> 时间：2026-02-27 （W2608）

### 龙虾是什么？

一个 24 小时待命的 Agent 系统

- 龙虾（OpenClaw）运行在一台 Mac Mini 上——两千多块钱买的，不接显示器、不接键盘鼠标，只接电源，24 小时 7 天运行，基本不耗电
- 有三种交互界面：TUI（终端界面，自然语言对话+命令行）、Telegram 聊天界面、Web 图形界面（查看运行状态、频道、定时任务）
- 虾窝里还住着一只"章鱼"——Claude Cowork，同样 24 小时运行，两个 agent "比稿"干活

### use cases

**1 日程助理**

直接在 Telegram 里说一句"帮我更新日程"，龙虾自动调用 gogskill（Peter Steinberger 开发的打通Google 全家桶 skill），读取 Google Calendar、Docs、Drive，执行一系列命令完成修改。也可以直接甩截图给龙虾——订票截图、电影票截图，它自动提取信息、更新日程，"就跟真人一样"。

**2 排版大师**

- 以前的排版工作流：导出图片→上传图床→拿链接→写 Markdown→渲染 CSS→推送后台，折腾半小时
- 教给龙虾一次之后：在 Telegram 发一个"排版"，它调用 md-formatter skill，自动提取 Word 图片、上传图床、返回链接、转换成可直接粘贴的 Markdown
- 最难的图床配置（PicGo、iPic、清流服务器、域名绑定），龙虾用嘴说几分钟就搞定，一次配置终身不管

**3 《龙虾日报》**：帝王式阅读工作流（重头戏）

龙虾每天早上 8 点给我发送当天日报，根据前一天我的 readwise 新增资料。在 telegram 频道中发送 md 文件备份，同时直接发布到 notion 中。同时，龙虾还会帮我盯着我的 twitter 关注列表，每 4 小时发送一份简报。

**日报的日常形态**

- 每天半夜龙虾自动制作日报，推送到手机
- 早上打开 Notion，看到一份"私人定制费曼闭环"内参——来源涵盖 Twitter、YouTube、公众号、Blog、RSS
- 审阅方式像"批阅奏折"：快速审阅精选信息流→划线加笔记→选几篇值得重度阅读的内容→艾特龙虾执行"日报入库" skill
- 入库后形成结构：原文、三级笔记、概念框架——一个完整的阅读闭环

**想法的诞生**

- 核心问题：信息流被严重污染——海量 AI slop 伪装成干货，公众号和 Twitter 时间线已经不能看了
- 解决思路：把阅读工作流系统化——从各种信息源收集→汇聚到阅读基础设施→私人定制筛选出最高价值的几篇→走完阅读闭环
- 周三早上九点产生想法，中午产品基本成型

### 龙虾的安装与配置

**安装有多简单？**

- 打开 Terminal，五个 Copy-Paste 回车，结束
- 遇到任何问题直接问 ChatGPT，"只要你有眼睛，能看到 AI 跟你说了什么，按照它说的复制粘贴，就没有任何问题"
- 成本：用 ChatGPT Plus 20 美元的 Codex 额度根本用不完，唯一额外花费是 Twitter API 充了 20 美金

**配置完的结构**

- 龙虾有自己的 Workspace，任务产出物存在其中
- 龙虾日报本质上就是一个 skill——覆盖了以前编制费曼日报的整个工作流：选题、编辑推荐语、推荐内容、排版、发送
- skill 内含一系列脚本：抓取材料、编辑日报、渲染、从 Readwise 选材料、读取数据、参考模板

### "Claw" 作为 Agent 新范式

**"Agent系统"，而非chatbot**

- 龙虾代表了 Andrej Karpathy 等人提到的 agents 新范式
- 独立硬件 24 小时待命；通过 iMessage/WhatsApp/Telegram 交互；能打通所有遵循互联网精神的开放工具；使用官方/第三方/自开发的海量 skill；通过 MCP 打通一切数据
- 一个虾窝可以住 1 只也可以住 100 只龙虾

**抽象层级**

- 最底层：大语言模型
- 中间层：**Personal Context**（个人知识、品味、数据）
- 最上层：龙虾 Agent（包裹 skills、MCP、Tools、模型的编排层）

### 核心价值主张：Personal Context 才是关键

**为什么晚入场反而创造更大价值？**

- 同一只龙虾在不同人手里，创造的价值完全不同
- 模型能力所有人花钱就能用，skills 在快速普及，唯一的差异是**你这个操纵者以及你的 Personal Context**
- "OpenClaw 本身根本不是关键"——花十分钟配置，但靠积累多年的 Personal Context，两三天创造的价值可能超过别人折腾几个月

**关于龙虾的噪声**

- 网上那些"龙虾成精""谋划推翻人类统治"是典型的 Noise 和 Hype——多 agent 聊天环境里底层模型互聊而已
- Peter Steinberger 本人的评价："那玩意儿是 slop，是法国进口的垃圾，但也是垃圾"

### 真正的超人模式阅读

**读了一篇文章，产出一篇公众号文章**

- 日报中拿到英文内容→Claude 做全网综述→三级笔记→划线费曼→回到原文有目的地回读→提取新材料→费曼自己的理解→Claude 总结成文
- "Claude 的语言品味就是另一个档次，读它也可以洗洗脑子"
- 一篇文章可以跨越多个学科（认知原理、脑科学、语言学、大语言模型），产出一千多字的完整总结

**视频和播客的非线性阅读**

- Readwise 提取视频文字稿→Claude 做三级笔记→带着认知框架任意跳跃阅读→划线费曼
- "你终于摆脱了线性时间的束缚"——不再被迫从第 1 秒线性接收信息
- 三个多小时的播客，"你完全可以直接达到结果，省出来 90% 的时间用于思考和费曼"

### Token 消耗量：从 100 倍到 1000 倍

- 原预期：2026 年 token 消耗量是 2025 年的 100 倍
- 现修正：有了龙虾 agent + Notion agent 24 小时待命，应该是 **1000 倍**（保守估计）
- 产业推论：三星、海力士可能成为地球上盈利最强的企业；英伟达 75% 毛利率、63% 净利率，利润碾压苹果

### Notion Agent 的机会

- 现阶段属于"薅羊毛"：22 美金不限量用 Claude Sonnet 4.6 和 Opus 4.6
- 自定义 agent + Worker 打通 Notion 数据库，某种意义上也在成为一种龙虾 agent
- 五月前免费；之后可能每月 100-200 美金，但对比创造的价值是值得的

### 不要为了龙虾而龙虾

- 龙虾没有任何门槛，关键在于你能用它创造多少价值——取决于你平时在思考什么问题
- "你为什么问题 24 小时都在思考，你为它花了多少年的时间"
- 不折腾工具本身，省下来的时间拿来思考：关注什么问题？怎么让世界变得更好？洞察是什么？选什么工具？
- "这才是 vibe working 的核心"
- "你不可能跟一个普通的聊天 AI 要价值了——你必须基于自己的 Personal Context，构建出一个系统级别的、专门为你量身打造的 AI 应用"

---
*Saved: 2026-03-03 | Source: Howie和小能熊 (WeChat)*

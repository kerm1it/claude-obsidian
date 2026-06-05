---
type: source
title: "Every Agentic Engineering Hack I Know (June 2026)"
source_url: https://x.com/i/status/2061877533885473181
source_kind: tweet-article
fetched: 2026-06-05
published: 2026-06-02
author: "[[MattVanHorn|Matt Van Horn]]"
address: c-000592
created: 2026-06-05
tags:
  - claude-code
  - codex
  - agentic-engineering
  - workflow
  - plan-execute
status: ingested
related:
  - "[[concepts/PlanExecute循环]]"
  - "[[concepts/DynamicWorkflows]]"
  - "[[concepts/Loop机制]]"
  - "[[concepts/模型即产品]]"
  - "[[MattVanHorn]]"
---

# Every Agentic Engineering Hack I Know (June 2026)

Matt Van Horn（@mvanhorn，June/Lyft 前身联合创始人）分享的 22 条 Agentic Engineering 实践技巧。基于 Claude Code + Codex 双引擎、Compound Engineering 插件生态的日常工作流。

## 核心模式：Plan-Execute 循环 → [[concepts/PlanExecute循环]]

1. **`/ce-plan`**：有想法立即生成 `plan.md`——并行 fan-out 研究 Agent（代码库 + 历史方案 + 外部文档）→ 结构化计划
2. **不用读 plan**：计划是给 Agent 的，人类只需 "TLDR?" 或 "eli5 this plan"
3. **`/ce-work`**：按计划构建；上下文溢出→新 session 指向计划→续传
4. **Plan for the plan**：让 Agent 先规划如何产出再执行——"让 LLM 不偷懒的最强技巧"

## 关键洞察

### 人=信号（Human Signal）
跑 6 个 Agent 时，你的角色是提供品味、方向和重定向。"Be the taste. Let them be the hands."

### 语音驱动
LLM 理解上下文→不需要完美转录。Monologue/Wispr Flow（Mac）+ Apple 听写（手机）。

### 多 Agent 并行
4-6 个 cmux tab 同时跑：一个计划、一个构建、一个修 bug。终端默认打开 Claude Code，不先进 shell。

### 笔记=Agent 知识库
Bear（十年笔记，CLI）+ Obsidian + gbrain + supermemory。选带 CLI/API 的工具→指向 Agent→跨 session 知识复利。

### AI 精神病警示
"Agent 本应做所有工作，但每个朋友都更努力了。" 构建 Agent 是"史上最好玩的电子游戏"——会上瘾。建议：确认有人真的需要你做的东西。

## 工具栈

| 类别 | 工具 |
|------|------|
| 计划执行 | Compound Engineering 插件（`/ce-plan` `/ce-work` `/ce-brainstorm`） |
| 终端 | cmux（多 tab），Orca（手机），Ghostty |
| 语音 | Monologue，Wispr Flow |
| 笔记 | Bear，Obsidian，gbrain，supermemory |
| 会议 | Granola（原始转录→LLM） |
| 远程 | Mosh + Tmux + Hermes + OpenClaw |
| 视频 | HyperFrames（script.md→MP4） |
| 文档 | Proof（plan.md→可读文档+评论） |
| 研究 | last30days（26K+ ⭐，多平台并行搜索） |
| CLI 舰队 | Printing Press（3.7K+ ⭐，Tesla/Instacart/ESPN/Alaska） |
| 认证 | Agent Cookie（浏览器 session 同步，无密码） |
| 邮箱 | AgentMail（Claude 独立邮箱→触发 session） |

## 开源贡献

Matt 数百 PR 合并进 Python/Go/OpenCV/Vercel Agent Browser 等项目。使用 `/ce-plan`+`/ce-work` 循环做开源贡献。加入项目 Discord→认识维护者→真朋友。通过此渠道招聘了工程师。

## 收敛

- **Plan-Execute 循环** ↔ [[concepts/DynamicWorkflows]] Fan-out-and-synthesize + Loop until done
- **人=信号** ↔ [[concepts/创始人编排者角色]]（Anthropic Playbook）
- **笔记=Agent 知识库** ↔ [[concepts/代码仓库即记录系统]]（OpenAI）+ 本 vault 的 [[hot]] 模式
- **语音驱动** ↔ [[concepts/模型即产品]]（Logan Kilpatrick）
- **"Plan for the plan"** ↔ [[concepts/Grilling模式]]（Matt Pocock）——都是对抗 Agentic Laziness 的 prompt 技巧

## 作者

[[MattVanHorn]] — June（Weber 收购）/ Lyft 前身联合创始人，last30days（26K+ ⭐）、Printing Press（4.1K+ ⭐）开源作者，Compound Engineering #3 贡献者。

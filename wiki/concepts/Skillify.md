---
type: concept
address: c-000035
title: "Skillify"
created: 2026-05-11
updated: 2026-05-30
tags:
  - agent-design
  - skill
  - workflow
status: active
related:
  - "[[entities/GBrain]]"
  - "[[sources/gbrain-2026-05-11]]"
  - "[[concepts/Skill与ToolMemory边界]]"
---

# Skillify

**来源**：[[entities/GBrain]] by [[people/GarryTan]]
**类型**：Agent Skill 固化模式

---

## 是什么

Skillify 是将一次性 Agent 修复（one-off fix）转化为**可持久、可测试、可路由 Skill** 的流程。它解决的问题是：Agent 每次遇到同类问题都要重新"想办法"，既低效又不稳定。

## Skill 的形态

在 GBrain 中，Skill 是**"胖 Markdown 文档"**（Fat Markdown Documents）——包含完整工作流编码的结构化说明文件，供 Agent 读取并执行。

GBrain 共有 **34 个专用 Skill**，覆盖：
- 内容摄入（会议、邮件、推文、PDF）
- 实体富化（人物、公司、关系）
- 脑操作（搜索、更新、蒸馏）
- 研究（自主调研、交叉引用）

## Skillify 10 项合规清单

将一个 fix 升级为 Skill 需要通过 10 项检查（具体条目未公开，但包括：可路由性、有测试用例、幂等性、错误处理、文档等）。

## 类比

类似于工程中的"从脚本到服务"——把一次性 bash 脚本封装成有 API、有文档、有测试的微服务。Skillify 把 Agent 的"临时技巧"变成"标准能力"。

## 与本 wiki 的关系

本 vault 使用的 `skills/` 目录（`wiki-ingest`、`wiki-query` 等）与 GBrain 的 Skill 模式高度相似，均是 fat-markdown 驱动的 Agent 工作流编码。

在 [[domains/AI知识体系]] 中，Skillify 是第 8 层 self-improvement 反哺第 4 层的典型路径：反复失败或一回成功经验先进入 memory / trace，再被整理成可测试、可路由、可版本化的 skill。

## Hivemind 的自动 Skillify

[[entities/Hivemind]]（Activeloop，2026）实现了全自动版本的 Skillify：

- 每 20 turns 自动从 agent traces 挖掘重复模式
- 无需人工 10 项合规清单审查
- 挖掘结果直接注入团队所有 Agent（`skillify pull`）
- 属于 Capture→Codify→Propagate 循环的 Codify 阶段

GBrain Skillify 偏向"人工审查固化"，Hivemind Skillify 偏向"全自动传播"。两者是同一模式在不同信任级别上的实现。

## 关联

- [[entities/GBrain]] — Skillify 的实现系统
- [[entities/Hivemind]] — 全自动 Skillify 实现
- [[concepts/CompiledTruth时间线模式]] — Skill 摄入结果存储的结构
- [[concepts/Skill与ToolMemory边界]] — skill / tool / memory / workflow 稳定边界
- [[concepts/Agent共享记忆]] — Hivemind 共享记忆概念

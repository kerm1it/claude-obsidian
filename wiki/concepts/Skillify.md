---
type: concept
address: c-000035
title: "Skillify"
created: 2026-05-11
updated: 2026-05-11
tags:
  - agent-design
  - skill
  - workflow
status: active
related:
  - "[[entities/GBrain]]"
  - "[[sources/gbrain-2026-05-11]]"
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

## 关联

- [[entities/GBrain]] — Skillify 的实现系统
- [[concepts/CompiledTruth时间线模式]] — Skill 摄入结果存储的结构

---
type: concept
address: c-000614
title: "PM 意图文档化"
created: 2026-06-12
updated: 2026-06-12
tags:
  - ai-shipping
  - documentation
  - intent
  - audit
  - agent-skills
status: active
related:
  - "[[entities/PMSkills]]"
  - "[[concepts/技能市场]]"
  - "[[concepts/ProductFeedbackClosureActionability边界]]"
  - "[[sources/pm-skills-2026-06-12]]"
---

# PM 意图文档化

**来源**：[[entities/PMSkills]] 的 `pm-ai-shipping` 插件（phuryn，2026）  
**所属体系层**：第 7 层（产品与组织）

---

## 是什么

PM 意图文档化（intent documentation for AI-generated code）是一个解决"AI 写代码快但不留意图"问题的模式：AI Agent 在生成代码的同时或之后，自动文档化"原本打算构建什么"（intended），并与"实际构建了什么"（implemented）进行审计对比。

---

## 解决的问题

> "AI agents write code fast but leave no record of intent."

传统软件开发中，PRD → 技术 spec → 代码的链条由人类维护。AI Agent 可以跳过中间步骤直接从模糊指令生成代码，导致：

- 没有"这个功能意图是什么"的记录
- 没有"代码和设计意图的差距在哪"的审计
- 后续维护者无法理解"为什么这样实现"

---

## pm-ai-shipping 的两层设计

| 层 | Skill | 功能 |
|----|-------|------|
| 文档化 | `shipping-artifacts` | 从代码反向生成意图文档（系统架构、功能描述、设计决策） |
| 审计 | `intended-vs-implemented` | 对比文档与代码，发现差距、遗漏、偏差 |

---

## 对应命令

| 命令 | 功能 |
|------|------|
| `/ship-check` | 全面检查：文档完整度、代码-文档一致性 |
| `/document-app` | 为代码库生成结构化文档 |
| `/derive-tests` | 从文档推导测试场景 |
| `/security-audit-static` | 静态安全审计 |
| `/performance-audit-static` | 静态性能审计 |

---

## 在 AI 知识体系中的位置

- **第 7 层（产品与组织）**：意图文档化是产品反馈闭环（[[concepts/ProductFeedbackClosureActionability边界]]）的一种实现——从"AI 写了代码"到"我们知道 AI 写了什么以及是否按意图写了"
- **与 self-improvement 的连接**：intended-vs-implemented 的审计结果可以反哺 skills 和 prompt（哪些 skill 容易产生偏差？哪些 prompt 不够精确？）

---

## 来源

- [[sources/pm-skills-2026-06-12]]

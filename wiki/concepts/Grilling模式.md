---
type: concept
address: c-000089
title: "Grilling 模式（任务前对齐审讯）"
created: 2026-05-15
updated: 2026-06-12
status: active
tags:
  - agent-workflow
  - alignment
  - engineering
related:
  - "[[people/MattPocock]]"
  - "[[concepts/共享领域语言]]"
  - "[[concepts/JIT规划]]"
  - "[[sources/mattpocock-skills-2026-05-15]]"
---

# Grilling 模式（任务前对齐审讯）

Matt Pocock 提出的 AI agent 工作流模式：在开始任何任务之前，让 agent 用一系列详细问题"审讯"你，直到所有决策分支都明确。

**核心洞察**（Pragmatic Programmer）："No-one knows exactly what they want." 最常见的软件开发失败模式是对齐失败——你以为 agent 理解了你的需求，等它交付时才发现完全跑偏。

## 两种变体

| Skill | 场景 | 额外功能 |
|---|---|---|
| `/grill-me` | 通用任务，非代码场景 | 仅对齐 |
| `/grill-with-docs` | 代码变更 | 对齐 + 更新 [[concepts/共享领域语言]]（CONTEXT.md）+ 写/更新 ADR |

Matt 的建议：**每次想做变更都先 grill**，哪怕你觉得你已经想清楚了。

## 工作方式

1. 你描述想做什么（粗略也可以）
2. Agent 开始提问：边界、约束、边缘情况、依赖、成功标准...
3. Agent 持续追问，直到决策树的所有分支都解决
4. Agent 生成对齐后的计划（或直接开始执行）

## 与相关概念的对比

| 概念 | 时机 | 关注点 |
|---|---|---|
| Grilling 模式 | 任务开始前 | 对齐：确保 agent 理解你真正的意图 |
| [[concepts/JIT规划]] | 任务规划层 | 节奏：只在需要时做足够的规划，避免计划过时 |
| [[concepts/瓶颈转移论]] | 组织层 | 瓶颈：编码不再稀缺，验证/理解成为新稀缺 |

三者收敛于同一认知：**AI 时代的瓶颈在于人机对齐和需求理解，不在于代码生成速度。**

## 来源

- [[sources/mattpocock-skills-2026-05-15]]
- [[people/MattPocock]]

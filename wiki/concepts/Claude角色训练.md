---
type: concept
address: c-000137
title: "Claude 角色训练（Character Training）"
created: 2026-05-21
updated: 2026-05-21
tags:
  - claude-character
  - training
  - agent-trust
  - anthropic
status: active
related:
  - "[[people/AlexAlbert]]"
  - "[[concepts/Claude意识研究]]"
  - "[[concepts/AnthropicDreaming]]"
  - "[[sources/alex-albert-building-next-claude-2026-05-21]]"
---

# Claude 角色训练（Character Training）

**来源**：[[sources/alex-albert-building-next-claude-2026-05-21]]  
**提出者**：[[people/AlexAlbert]]（Anthropic Research PM）

---

## 核心思想

> "Claude's character — we think this is very very important. The questions of what its character is and what it cares about are very important."

Claude 的**信仰、价值观和行为方式**（统称 Character）不是装饰，是正式训练目标。随着 Agent 长时间自主运行需要大量判断决策，Character 已成为信任基础。

---

## 为什么 Character 很重要

| 阶段 | 重要性 |
|------|--------|
| 早期（工具时代）| 被忽视——"告诉它做什么它就做什么" |
| 现在（Agent 时代）| **极其重要**——Agent 长时间运行，做架构决策、判断调用，无处不在 |

> "If this thing is writing all your code and deciding which database system you're going to use and making all these architectural decisions, you kind of want to trust it to some degree."

---

## Character 包含什么

- Claude 如何代表自己（self-representation）
- 它的信仰和价值观（beliefs & values）
- 面对特定场景的行为（behavior under scenarios）
- 不奉承/sycophantic：在正确的地方 push back

---

## Eval 方法

1. **定量指标**：用 Claude 评估 Claude 自身输出（比如：这段回答听起来怎么样？）
2. **定性直觉**：研究员大量阅读 transcript，建立对"模型感觉"的直觉
3. **组合判断**："It's a bit of both." — 不依赖单一分数

> "You kind of develop this sharper intuition as you just read hundreds and thousands of model transcripts."

---

## 与 Agent 信任的关系

- Agent 运行时间越长 → 需要做的判断决策越多 → Character 的权重越高
- 这是 [[concepts/Claude意识研究]] 的实用动机之一：即使不确定 Claude 是否有意识，研究它如何思考也能改善产品

---

## 关联概念

- [[concepts/Claude意识研究]] — Character 研究的延伸：意识和 Agent 责任
- [[concepts/AnthropicDreaming]] — 自主维护记忆也依赖 Character（判断什么该保留/删除）
- [[concepts/模型即产品]] — Character 是模型规格的"非功能性需求"

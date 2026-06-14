---
address: c-000312
type: source
title: "CharacterFlywheel"
source_url: https://arxiv.org/abs/2603.01973
source_type: paper
author: "Character.AI"
published: 2026-03-03
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - data-flywheel
  - production-llm
  - user-feedback
status: active
related:
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/模型即产品]]"
---

# CharacterFlywheel

**来源**：arXiv
**URL**：https://arxiv.org/abs/2603.01973

## 摘要

CharacterFlywheel 描述面向生产对话模型的迭代改进框架。它把用户交互、偏好信号、模型训练和产品质量连接成循环，目标是让模型更符合长期用户体验。

## 关键贡献

- 生产对话系统可用真实交互数据构建持续改进循环。
- 用户反馈不是单一标签，包含 engagement、preference、quality 和 safety 等多个维度。
- 飞轮需要区分短期 engagement 和长期质量，否则容易出现 KPI gaming。
- 对本 vault 的意义：第 7 层数据飞轮必须被第 6 层 anti-gaming 和质量门约束。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：2. 模型构建层、6. 评估与可靠性层

## 关联

- [[concepts/DataFlywheelFeedbackLoop边界]]
- [[concepts/模型即产品]]

---
address: c-000308
type: source
title: "Rules of Machine Learning"
source_url: https://developers.google.com/machine-learning/guides/rules-of-ml
source_type: documentation
author: "Google"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - mlops
  - feedback-loop
  - training-serving-skew
status: active
related:
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
---

# Rules of Machine Learning

**来源**：Google Developers
**URL**：https://developers.google.com/machine-learning/guides/rules-of-ml

## 摘要

Google Rules of ML 是生产机器学习经验规则。对 data flywheel 最关键的是：线上 serving 产生的特征和日志必须能支持训练与验证，同时要持续检查 training-serving skew。

## 关键贡献

- 训练和服务路径不一致会导致线上表现与离线评估脱节。
- 需要保存 serving-time features，以便后续训练、调试和验证。
- 新模型上线前要检查数据、指标和线上行为是否一致。
- 对本 vault 的意义：反馈数据不是直接回灌，而是先进入可验证的数据管线。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层、2. 模型构建层

## 关联

- [[concepts/DataFlywheelFeedbackLoop边界]]
- [[Research: Data flywheel feedback loop 边界]]

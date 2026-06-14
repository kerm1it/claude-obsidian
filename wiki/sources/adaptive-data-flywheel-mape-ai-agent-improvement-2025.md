---
address: c-000585
type: source
title: "Adaptive Data Flywheel: Applying MAPE Control Loops to AI Agent Improvement"
source_url: https://arxiv.org/abs/2510.27051
source_type: paper
author: "Shukla et al."
published: 2025-10-30
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: medium
tags:
  - data-flywheel
  - agents
  - mlops
  - control-loop
status: active
related:
  - "[[concepts/ProductFeedbackClosureActionability边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
---

# Adaptive Data Flywheel

**来源**：arXiv
**URL**：https://arxiv.org/abs/2510.27051

## 摘要

论文提出用 MAPE-K control loop operationalize enterprise AI agent data flywheel。案例是 NVIDIA 的 NVInfo AI 知识助手：在三个月部署期内监控反馈、分析负样本、识别 routing 和 query rephrasal 失败，再用 targeted fine-tuning 改进准确率、延迟和模型大小。

## 关键贡献

- 将 Monitor、Analyze、Plan、Execute 的控制环用于 AI agent 持续改进。
- 用 human-in-the-loop feedback 和 production negative samples 识别可行动失败模式。
- 展示 routing、query rephrasal 等子模块可以被分开修复，而不是把所有问题都归因给“大模型不够好”。
- 对本 vault 的意义：product feedback closure 可以被定义为一个控制环是否真正完成，而不是仅收集反馈。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：5. Agent 系统层、6. 评估与可靠性层、8. 自我改进与前沿层

## 关联

- [[concepts/ProductFeedbackClosureActionability边界]]
- [[concepts/DataFlywheelFeedbackLoop边界]]
- [[Research: Product feedback closure data flywheel actionability 边界]]

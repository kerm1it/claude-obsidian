---
address: c-000309
type: source
title: "MLOps: Continuous delivery and automation pipelines in machine learning"
source_url: https://cloud.google.com/architecture/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning
source_type: documentation
author: "Google Cloud"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - mlops
  - continuous-training
  - data-validation
status: active
related:
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
---

# MLOps: Continuous delivery and automation pipelines in machine learning

**来源**：Google Cloud Architecture Center
**URL**：https://cloud.google.com/architecture/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning

## 摘要

Google Cloud 的 MLOps 指南把机器学习系统拆成数据验证、模型验证、部署、监控和自动化 retraining pipeline。它说明反馈闭环必须有验证门、监控和可重复 pipeline。

## 关键贡献

- Continuous training 不是简单“有新数据就训练”，而是 pipeline 化的数据验证、模型验证和部署流程。
- 生产监控可以触发重新训练，但触发条件和验证门需要明确。
- 对本 vault 的意义：data flywheel 进入第 8 层 self-improvement 前，必须先经过第 6 层数据质量和模型质量 gate。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层、8. 自我改进与前沿层

## 关联

- [[concepts/DataFlywheelFeedbackLoop边界]]
- [[concepts/EvalResultInterpretationDecisionThreshold边界]]
- [[Research: Data flywheel feedback loop 边界]]

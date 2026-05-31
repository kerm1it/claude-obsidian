---
address: c-000468
type: source
title: "Performance monitoring and continuous improvement for generative AI applications"
source_url: https://docs.aws.amazon.com/prescriptive-guidance/latest/gen-ai-lifecycle-operational-excellence/prod-monitoring.html
source_type: official-docs
author: "AWS Prescriptive Guidance"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - genaiops
  - production-monitoring
  - continuous-improvement
status: active
related:
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/ProductFeedbackClosureActionability边界]]"
---

# Performance Monitoring and Continuous Improvement for Generative AI Applications

**来源**：AWS Prescriptive Guidance
**URL**：https://docs.aws.amazon.com/prescriptive-guidance/latest/gen-ai-lifecycle-operational-excellence/prod-monitoring.html

## 摘要

AWS 把 generative AI production monitoring 和 continuous improvement 定义为维持可靠性、有效性和安全性的核心运营能力。文档把生产监控分为 application health monitoring、business metrics tracking、model quality assessment，并把 drift detection、feedback loop 和 structured improvement 放在同一套运行机制中。

## 关键贡献

- 明确 GenAI 应用在动态用户行为和数据模式下需要持续监控。
- 把 model quality、business metric、application health 同时纳入生产监控。
- 强调 monitoring、drift detection、feedback loop 和 improvement action 需要工程化闭环。
- 对本 vault 的意义：post-release eval drift 不是只看 eval 分数，而是把质量、安全、业务、成本和反馈一起映射回发布证据。
- 对 feedback closure 的意义：monitoring 和 feedback 必须产生 structured improvement action，否则只是在观察生产系统。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层、8. 自我改进与前沿层

## 关联

- [[concepts/PostReleaseEvalDrift边界]]
- [[Research: Post-release eval drift 边界]]
- [[concepts/ProductFeedbackClosureActionability边界]]

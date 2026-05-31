---
address: c-000444
type: synthesis
title: "Research: Eval uncertainty communication release card 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - evals
  - uncertainty
  - release-card
status: active
related:
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/IntolerableRiskThresholdStopRule边界]]"
sources:
  - "[[sources/nist-ai-evaluation-statistical-models-2026]]"
  - "[[sources/adding-error-bars-evals-2024]]"
  - "[[sources/model-cards-for-model-reporting-2019]]"
  - "[[sources/riskcards-language-model-deployment-2023]]"
  - "[[sources/sphere-evaluation-card-2025]]"
  - "[[sources/google-model-card-toolkit-2026]]"
  - "[[sources/openai-gpt-4o-system-card-2024]]"
  - "[[sources/openai-trustworthy-third-party-evaluations-2026]]"
  - "[[sources/betterbench-benchmark-quality-2024]]"
---

# Research: Eval uncertainty communication release card 边界

## Overview

本轮研究把 eval uncertainty communication / release card 归入第 6 层评估与可靠性层，并把它作为第 6 层到第 7 层 release gate、safety governance 和组织 owner 的证据表达接口。

稳定结论：**eval 不确定性不能只藏在统计脚注里；它必须被翻译成决策语言：pass、fail、gray zone、canary、human review、no-go、rollback 或补证据。**

## Key Findings

- NIST 2026 AI benchmarking 统计报告指出，benchmark 指标常因评估设定假设和 uncertainty 估计不当而产生无效结论，并区分 benchmark accuracy 与 generalized accuracy。（Source: [[sources/nist-ai-evaluation-statistical-models-2026]]）
- Anthropic / Evan Miller 的 eval error bars 工作把 eval 明确视为实验，建议报告 SEM、clustered standard errors、paired differences、重复采样和 power，而不是只报告点估计。（Source: [[sources/adding-error-bars-evals-2024]]）
- Model Cards 框架把 intended use、性能特征、跨群体评估、评估流程和限制写成模型发布文档，为 release/eval card 的结构提供稳定先例。（Source: [[sources/model-cards-for-model-reporting-2019]]）
- RiskCards 把语言模型风险绑定到具体使用场景、harm taxonomy、风险显现路径和 prompt-output 样例，说明风险沟通要围绕 deployment context 而不是模型均值。（Source: [[sources/riskcards-language-model-deployment-2023]]）
- SPHERE evaluation card 用五个问题组织 human-AI system evaluation：评估什么、怎么评、谁参与、何时评、如何验证；这直接支撑 eval card 的字段设计。（Source: [[sources/sphere-evaluation-card-2025]]）
- Google Model Card Toolkit 显示 model card 可以工程化生成并嵌入 ML pipeline，关键用途包括模型构建者与产品开发者的信息交换、使用决策和公共问责。（Source: [[sources/google-model-card-toolkit-2026]]）
- OpenAI GPT-4o system card 是 system-level 发布透明度样例：它把多模态能力、限制、安全评估、外部红队和 mitigations 放进发布材料。（Source: [[sources/openai-gpt-4o-system-card-2024]]）

## 主归属

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游：eval run、dataset/grader version、uncertainty、slice、validity check、risk threshold、production monitor
- 下游：release card、decision memo、review action、exception、rollback trigger、post-release validation

## 稳定框架

```text
eval evidence
    -> uncertainty and validity assessment
    -> limitations and blind spots
    -> decision band and risk language
    -> release/eval card with owner, exception, monitor, rollback trigger
    -> release gate / safety governance / post-release comparison
```

## 与相邻概念的边界

- [[concepts/EvalResultInterpretationDecisionThreshold边界]] 回答“分数如何解释成阈值”；本轮回答“阈值、不确定性和限制如何被组织看懂并审查”。
- [[concepts/ModelReleaseRollbackGate边界]] 回答“谁执行发布/回滚”；本轮提供 gate 消费的证据卡。
- [[concepts/JudgeDriftGraderObservability边界]] 回答“评分器是否健康”；本轮要求把 judge health 状态显式进入卡片。
- [[concepts/IntolerableRiskThresholdStopRule边界]] 回答“哪些风险必须 no-go”；本轮要求把 hard stop 放在 release card 的高优先级字段。

## Open Questions

- 对高风险系统，release card 和 full safety case 的边界应如何划分？
- 对在线 eval / canary，哪些 uncertainty signal 应实时进 dashboard，哪些必须冻结到 card？
- 对多产品线组织，release card 字段如何在轻量和审计完整性之间取平衡？

## Sources

- [[sources/nist-ai-evaluation-statistical-models-2026]]
- [[sources/adding-error-bars-evals-2024]]
- [[sources/model-cards-for-model-reporting-2019]]
- [[sources/riskcards-language-model-deployment-2023]]
- [[sources/sphere-evaluation-card-2025]]
- [[sources/google-model-card-toolkit-2026]]
- [[sources/openai-gpt-4o-system-card-2024]]
- [[sources/openai-trustworthy-third-party-evaluations-2026]]
- [[sources/betterbench-benchmark-quality-2024]]

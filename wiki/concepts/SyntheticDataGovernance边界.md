---
address: c-000370
type: concept
title: "Synthetic Data Governance 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - synthetic-data
  - data-quality
  - governance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
sources:
  - "[[sources/model-collapse-nature-2024]]"
  - "[[sources/is-model-collapse-inevitable-2024]]"
  - "[[sources/self-instruct-2022]]"
  - "[[sources/anthropic-constitutional-ai-rlaif-2022]]"
  - "[[sources/openai-model-distillation-2024]]"
  - "[[sources/openai-fine-tuning-data-quality-2026]]"
  - "[[sources/data-cards-2022]]"
  - "[[sources/w3c-prov-overview-2013]]"
  - "[[sources/machine-unlearning-comprehensive-survey-2024]]"
  - "[[sources/anthropic-hh-rlhf-2022]]"
  - "[[sources/llm-evaluators-self-preference-2024]]"
  - "[[sources/automated-self-testing-quality-gate-llm-applications-2026]]"
---

# Synthetic Data Governance 边界

Synthetic data governance 是第 6 层评估与可靠性层的合成样本准入门：它判断由模型、仿真器、规则系统、teacher model、self-improvement loop 或数据增强流程生成的样本，能否进入训练、eval、RAG、memory、skill、router 或产品反馈闭环。

一句话：**合成数据不是脏数据，也不是免费真相；它是候选证据，必须按用途过质量门。**

## 主归属

- 主归属：6. 评估与可靠性层
- 上游输入：目标缺口、seed data、generator model、prompt、teacher outputs、simulation state、data rights、真实 hold-out
- 下游输出：accepted synthetic training samples、synthetic eval cases、rejected samples、data card、lineage、contamination warning
- 训练接口：2. 模型构建层
- 组织接口：7. 产品与组织层
- 自我改进接口：8. 自我改进与前沿层

## 稳定链路

```text
target gap / use case
    -> seed data rights and provenance
    -> generator model, prompt, version, sampling policy
    -> synthetic sample generation
    -> dedup, leakage, diversity, label, realism, and safety filters
    -> split isolation and hold-out contamination check
    -> downstream validation on real and private evals
    -> route to training, eval, RAG, memory, skill, simulation, or reject
    -> monitor drift, collapse, and downstream impact
```

## 用途分流

| 用途 | 可用条件 | 主要风险 |
|---|---|---|
| SFT / instruction tuning | 多样任务、过滤无效/相似样本、真实 hold-out 验证 | 风格单一、错误标签、过拟合生成器 |
| Distillation | teacher 输出覆盖稳定行为，student 通过独立 eval | teacher 偏差被压进小模型 |
| RLAIF / synthetic preference | AI feedback 与 human/rule baseline 校准 | judge bias、reward hacking |
| Synthetic eval / red-team | 只做测试集或回归集，不泄漏进训练 | benchmark contamination、过度贴合生成器 |
| Privacy substitute | 证明不可重识别且不泄漏 seed data | 把“合成”误当成“匿名” |
| Simulation / world-model data | 环境状态和物理/业务规则可验证 | sim-to-real gap |
| RAG / memory / knowledge | 只作为摘要或候选，不替代来源事实 | fabricated provenance、stale fact |

## 与相邻概念区别

- 与 [[concepts/DataQualityLabelQuality边界]]：data quality 是通用质量门；synthetic data governance 是合成样本的专门准入规则。
- 与训练数据：生成合成数据属于第 2 层候选数据生产；是否进入训练由第 6 层 gate 决定。
- 与 [[concepts/DataRightsPrivacyConsent边界]]：合成样本仍可能继承 seed data、prompt、用户内容或 teacher output 的权利限制。
- 与 eval：合成 eval 适合扩覆盖和生成 adversarial cases，但不能替代真实私有 hold-out。
- 与 [[concepts/RewardHackingEvalOverfitting边界]]：如果同一模型家族生成训练、评分和 eval，系统容易自我确认。
- 与 [[concepts/Dream与SelfImprovement工程原语]]：dream 可以提出 synthetic cases；应用前必须通过本页的质量、权利和 hold-out gates。
- 与 [[concepts/DatasetLineageProvenanceGraph边界]]：合成样本必须能追溯 generator、prompt、seed data、filter、split、用途和下游影响，否则无法做污染检测和 collapse 监控。
- 与 [[concepts/DataDeletionUnlearningImpact边界]]：如果 seed data、prompt、teacher output 或真实用户样本被删除，合成派生样本也要通过 lineage 查询进入删除、隔离、重算或例外审查。
- 与 [[concepts/HumanFeedbackAnnotationOps边界]]：AI feedback、LLM-as-judge 和 synthetic labels 可以降低人工成本，但必须用 human gold、rubric、adjudication 和 downstream eval 校准。
- 与 [[concepts/LLMJudgeAIFeedbackCalibration边界]]：AI judge / AI annotator 是合成证据生成器的一种；它的标签、偏好和 critique 先过 judge calibration，再进入 synthetic data governance 的用途准入。
- 与 [[concepts/SelfImprovementGateChangeRiskBudget边界]]：self-improvement 可以提出 synthetic eval、teacher output 或 augmentation；本页判断合成样本能不能用，self-improvement gate 决定由这些样本触发的 diff 能不能落地。

## 评估方式

- Downstream real-holdout delta：合成数据加入后，真实私有 eval 是否改善。
- Synthetic-real gap：合成分布与真实分布差距，尤其是长尾和风险场景。
- Diversity and coverage：任务、用户、语言、格式、边界案例是否足够多样。
- Dedup / contamination rate：与训练集、eval、公开 benchmark、seed data 是否重复或近重复。
- Label / judge calibration：AI label、teacher output 或 judge 与 human/rule/gold-set 是否一致。
- Privacy leakage：是否能重构个人数据、商业秘密、prompt 或 seed examples。
- Model collapse signal：递归使用合成数据后，分布是否变窄、错误是否累积、尾部是否消失。
- Lineage completeness：每条样本能否追溯 generator、prompt、seed、filter、用途和版本。

## 过时风险

- 生成器能力会提升，但“生成样本要经过 provenance、rights、quality、contamination、hold-out validation”这个结构稳定。
- 模型越强，合成数据越像真实数据，反而更容易污染 eval 和隐藏 provenance。
- 合成数据比例、混合策略和过滤器会随任务变化；不要固化单一阈值。

## 一句话归类

Synthetic data governance 主属第 6 层，是合成样本进入第 2 层训练、第 6 层 eval、第 4 层知识机制、第 7 层产品反馈或第 8 层自我改进前的质量、权利、污染和下游验证门。

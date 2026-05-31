---
address: c-000345
type: synthesis
title: "Research: Data quality label quality 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - data-quality
  - label-quality
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
sources:
  - "[[sources/tensorflow-data-validation-2026]]"
  - "[[sources/google-rules-of-ml-2026]]"
  - "[[sources/datasheets-for-datasets-2021]]"
  - "[[sources/data-cards-2022]]"
  - "[[sources/data-cascades-high-stakes-ai-2021]]"
  - "[[sources/openai-fine-tuning-data-quality-2026]]"
  - "[[sources/label-errors-benchmarks-2021]]"
  - "[[sources/huggingface-dataset-cards-2026]]"
---

# Research: Data quality label quality 边界

## Overview

Data quality / label quality 主属第 6 层评估与可靠性层。它是数据进入 eval、training、RAG、memory、skill 或 router 前的质量门，防止 data flywheel 把噪声、错误标签、过时知识、未授权数据、benchmark leakage 和低质量反馈放大成系统性退化。

## Key Findings

- TensorFlow Data Validation 将 schema、统计、异常检测和训练/服务数据分析放进 ML pipeline，说明 data validation 是持续流程而不是一次性清洗（Source: [[sources/tensorflow-data-validation-2026]]）。
- Google Rules of ML 强调 freshness、training-serving skew、held-out data 和数据 join 的风险，支持把数据质量接入线上系统设计（Source: [[sources/google-rules-of-ml-2026]]）。
- Datasheets for Datasets 提出用标准化文档记录动机、组成、收集过程、推荐用途和限制，解决数据消费者无法判断数据适用性的缺口（Source: [[sources/datasheets-for-datasets-2021]]）。
- Google Data Cards 强调 dataset documentation 必须服务不同生命周期 stakeholder，记录来源、采集、标注、伦理、用途和模型影响（Source: [[sources/data-cards-2022]]）。
- Data Cascades 研究显示高风险 AI 中数据问题会产生延迟、隐形、连锁的下游负面影响，说明 data quality 是安全问题而非后勤问题（Source: [[sources/data-cascades-high-stakes-ai-2021]]）。
- OpenAI fine-tuning best practices 将训练集质量作为微调效果关键，强调修正错误、覆盖边界案例、保持一致格式和验证集（Source: [[sources/openai-fine-tuning-data-quality-2026]]）。
- Pervasive Label Errors in Test Sets 发现常用 benchmark 测试集也存在标签错误，标签噪声会 destabilize model selection 和 benchmark ranking（Source: [[sources/label-errors-benchmarks-2021]]）。
- Hugging Face dataset cards 把 license、language、size、bias、intended use 等信息放入 dataset README，说明公开数据复用也需要文档和元数据质量（Source: [[sources/huggingface-dataset-cards-2026]]）。

## Stable Definition

```text
candidate signal
    -> rights + provenance
    -> validity + freshness + dedup
    -> label/rubric quality
    -> leakage/split check
    -> fit-for-purpose routing
    -> downstream impact measurement
```

## Boundary Rules

| 问题 | 稳定答案 |
|---|---|
| 真实用户反馈能否直接训练？ | 不能；先经过授权、去噪、归因、label/rubric 和 hold-out 检查。 |
| Eval 样本是否越多越好？ | 不是；eval 更重视代表性、清晰预期、无泄露和稳定复现。 |
| 错误标签只影响训练吗？ | 不只；错误 test/eval label 会让 model selection 和 safety gate 失真。 |
| 数据质量是否有通用分数？ | 没有；必须绑定用途：eval、SFT、RAG、memory、skill 或 router。 |
| 合成数据是否天然干净？ | 不是；它需要 provenance、diversity、dedup、judge bias 和 self-contamination 检查。 |

## Open Questions

- LLM-as-judge 生成 label 时，如何校准 judge drift、偏见和自我污染。
- 多轮 agent trace 的“正确标签”常依赖最终状态，如何标准化 trace-level label quality。
- 数据删除请求如何影响已进入 eval、training candidate、RAG cache 和 skill examples 的样本。

## Sources

- [[sources/tensorflow-data-validation-2026]]
- [[sources/google-rules-of-ml-2026]]
- [[sources/datasheets-for-datasets-2021]]
- [[sources/data-cards-2022]]
- [[sources/data-cascades-high-stakes-ai-2021]]
- [[sources/openai-fine-tuning-data-quality-2026]]
- [[sources/label-errors-benchmarks-2021]]
- [[sources/huggingface-dataset-cards-2026]]

---
address: c-000377
type: synthesis
title: "Research: Dataset lineage provenance graph 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - data-lineage
  - provenance
status: developing
related:
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
sources:
  - "[[sources/w3c-prov-overview-2013]]"
  - "[[sources/tensorflow-ml-metadata-2026]]"
  - "[[sources/openlineage-spec-2026]]"
  - "[[sources/eu-ai-act-data-governance-2024]]"
  - "[[sources/nist-genai-profile-data-privacy-2024]]"
---

# Research: Dataset lineage provenance graph 边界

## Overview

Dataset lineage / provenance graph 的稳定核心不是“数据平台功能”，而是 AI 证据链：记录 artifact、activity、actor、version、rights 和 downstream impact，让训练、eval、RAG、memory、skill、synthetic data 和 incident response 能被审计与回滚。

主归属固定为第 6 层评估与可靠性层，因为它决定证据是否可追溯、可污染检测、可复现、可删除和可用于质量门；它同时连接第 2 层训练、第 4 层知识、第 5 层 agent trace、第 7 层治理和第 8 层自我改进。

## Key Findings

- W3C PROV 给出跨系统 provenance 的稳定抽象：entity、activity、agent，以及可用于判断质量、可靠性和可信度的来源信息。（Source: [[sources/w3c-prov-overview-2013]]）
- TFX ML Metadata 把 ML workflow 具体化为 artifact、execution、event、context，并支持从任意 artifact 递归回溯到上游输入、查询哪些模型使用了某个 dataset。（Source: [[sources/tensorflow-ml-metadata-2026]]）
- OpenLineage 把数据作业标准化为 run event、job、dataset、run 和 facet，适合把 batch / streaming / SQL / orchestration 系统的数据血缘统一成可扩展事件。（Source: [[sources/openlineage-spec-2026]]）
- EU AI Act 的高风险系统要求训练、验证、测试数据治理覆盖数据来源、准备操作、偏差和记录能力；这把 lineage 从工程便利推到合规证据。（Source: [[sources/eu-ai-act-data-governance-2024]]）
- 对 AI 系统，lineage graph 必须扩展到模型外部知识和 agent runtime：RAG chunk、memory entry、skill candidate、tool trace、prompt、provider/model version、eval case 和 release decision 都要能进入同一证据链。

## Stable Classification

- 主归属：6. 评估与可靠性层
- 上游：data flywheel、synthetic generation、annotation、RAG ingest、agent trace、tool calls、pipeline runs
- 下游：eval/training/RAG/memory/skill/router 准入，删除/导出/回滚，incident evidence package，audit trail
- 关键连接：第 7 层 data rights 定义可用性，第 6 层 lineage 证明发生了什么，第 2/4/5/8 层消费或产出被追踪 artifact。

## Concept Boundaries

- Lineage 不是 data quality：quality 判断是否可信，lineage 记录可信判断所需的来源、转换和影响面。
- Lineage 不是 data card：card 是人读文档，lineage 是机器查询的图。
- Lineage 不是日志：日志记录事件，lineage 把事件产物接成跨版本、跨 pipeline、跨 agent 的因果图。
- Lineage 不是训练数据管理：训练只是一个消费者；RAG、memory、eval、skill、incident 和 self-improvement 同样需要 lineage。

## Engineering Practice

1. 给所有关键 artifact 分配稳定 ID、hash、版本、tenant、权限、retention 和用途标签。
2. 把每个转换写为 activity/execution：输入、输出、代码版本、prompt、模型、参数、actor、时间。
3. 把 trace 变成 lineage edge：tool call、RAG retrieval、memory write、skill update、eval run、release gate 都要可关联。
4. 在进入训练/eval 前跑污染查询：公开 benchmark、hold-out、synthetic seed、teacher output、RAG cache 和历史训练集是否重复。
5. 在删除、导出、事故、provider fallback、self-improvement diff 时做 downstream impact query。

## Evaluation

- Coverage：关键 artifact 和 activity 的记录覆盖率。
- Completeness：source、rights、transform、version、split、owner、downstream edge 是否完整。
- Contamination detection：train/eval/hold-out/benchmark/synthetic seed 的重复与近重复命中率。
- Reproducibility：能否用 lineage 重建某个模型、eval、memory、skill 或事故产物。
- Deletion impact：能否定位并处理数据主体请求影响的下游 artifact。
- Incident reconstruction：能否还原 prompt、context、RAG、memory、tool、identity、provider、model 和 policy。

## Open Questions

- AI agent 的 tool trace 与传统数据 lineage 的最佳统一 schema 仍在演化。
- 样本级 lineage 成本较高；不同风险等级需要不同粒度策略。
- Privacy 与 lineage 有张力：记录太少不可审计，记录太多会泄露敏感元数据。
- 对已训练模型的“删除影响”常常无法完全逆转，需要和 unlearning、retraining、model replacement 策略联动。

## Sources

- [[sources/w3c-prov-overview-2013]]：W3C PROV 概念模型与互操作标准。
- [[sources/tensorflow-ml-metadata-2026]]：ML workflow artifact / execution / event lineage 实现。
- [[sources/openlineage-spec-2026]]：数据作业 lineage 的开放事件规范。
- [[sources/eu-ai-act-data-governance-2024]]：高风险 AI 系统的数据治理和记录要求。
- [[sources/nist-genai-profile-data-privacy-2024]]：GenAI 风险管理中的数据、隐私、透明度和治理锚点。

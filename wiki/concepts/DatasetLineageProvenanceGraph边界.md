---
address: c-000376
type: concept
title: "Dataset Lineage / Provenance Graph 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - data-lineage
  - provenance
  - evals
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
sources:
  - "[[sources/w3c-prov-overview-2013]]"
  - "[[sources/tensorflow-ml-metadata-2026]]"
  - "[[sources/openlineage-spec-2026]]"
  - "[[sources/slsa-provenance-v1-2-2026]]"
  - "[[sources/safety-case-maintenance-slr-2021]]"
  - "[[sources/eu-ai-act-data-governance-2024]]"
  - "[[sources/nist-genai-profile-data-privacy-2024]]"
  - "[[sources/machine-unlearning-sisa-2019]]"
  - "[[sources/label-studio-annotation-quality-2026]]"
  - "[[sources/openai-evals-framework-2026]]"
---

# Dataset Lineage / Provenance Graph 边界

Dataset lineage / provenance graph 是第 6 层评估与可靠性层的证据血缘图：它记录样本、文档、label、trace、RAG chunk、memory entry、skill example、synthetic sample、eval case、model checkpoint、prompt、tool run 和 release decision 之间的来源、转换、版本和下游影响。

一句话：**data quality 问“这条证据可靠吗”；lineage graph 问“这条证据从哪来、经过什么、影响了什么、能不能删除或回滚”。**

## 主归属

- 主归属：6. 评估与可靠性层
- 上游输入：raw data、user feedback、trace、tool result、documents、labels、synthetic samples、pipeline runs、model/eval versions
- 下游输出：可查询 provenance、污染检测、删除/回滚影响面、incident evidence package、dataset/model card、audit trail
- 模型接口：2. 模型构建层
- 知识接口：4. 上下文与知识层
- Agent 接口：5. Agent 系统层
- 组织接口：7. 产品与组织层
- 自我改进接口：8. 自我改进与前沿层

## 稳定链路

```text
artifact / sample / trace / doc / label
    -> source and rights capture
    -> transformation activity: ingest, clean, label, generate, filter, split, chunk, embed, train, eval, deploy, memory-write, skill-update
    -> versioned dataset / manifest / card / graph edge
    -> route to training, eval, RAG, memory, skill, router, product, or reject
    -> downstream model/product/eval impact query
    -> deletion, rollback, audit, incident reconstruction
```

## 核心对象

| 对象 | 例子 | 稳定问题 |
|---|---|---|
| Entity / artifact | 原始文档、样本、label、RAG chunk、memory、eval case、model checkpoint | 它是什么，版本和 hash 是什么 |
| Activity / execution | ingest、clean、label、generate、dedup、split、train、eval、deploy | 谁用什么输入生成了什么输出 |
| Agent / actor | 用户、标注员、模型、pipeline、agent run、provider | 谁或什么系统负责这个动作 |
| Edge | used、generatedBy、derivedFrom、versionOf、invalidatedBy、evaluatedBy | 两个对象之间是什么因果关系 |
| Metadata | rights、consent、tenant、retention、source、time、transform version、split、quality score | 能否使用、保留、删除、审计 |

## 与相邻概念区别

- 与 [[concepts/DataQualityLabelQuality边界]]：data quality 评估证据是否可信；lineage graph 记录证据来源、转换和下游影响。
- 与 [[concepts/SyntheticDataGovernance边界]]：synthetic governance 要求每条合成样本记录 generator、prompt、seed、filter 和用途；lineage graph 是承载这些关系的底座。
- 与 [[concepts/DataRightsPrivacyConsent边界]]：data rights 判断是否允许使用；lineage graph 支持删除、导出、用途审计和授权影响面查询。
- 与 [[concepts/DataDeletionUnlearningImpact边界]]：deletion/unlearning 消费 lineage 的影响面查询；lineage 负责证明哪些 chunks、memory、eval、training rows、synthetic derivatives、model versions、provider state 和 backups 受影响。
- 与 [[concepts/HumanFeedbackAnnotationOps边界]]：annotation ops 产生 label、rank、review、rubric 和 annotator cohort 证据；lineage 记录它们的来源、版本、split、用途和下游模型/eval 影响。
- 与 [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]：eval lifecycle 消费 lineage 来证明样本来源、split、版本、训练接触历史和访问范围，避免 hold-out、benchmark 与训练数据互相污染。
- 与 [[concepts/EvidenceFreshnessStaleProof边界]]：lineage graph 证明证据依赖哪些 artifact 和 transformation；freshness/stale proof 用这些依赖判断证据是否过期、被替代或被失效。
- 与 [[concepts/EvidenceAttestationSignedEvalArtifact边界]]：lineage graph 记录证据血缘和影响面；attestation 给具体 artifact、eval result 或 release evidence 加 subject digest、签名、producer 和 policy verification。
- 与 data card / dataset card：card 是给人读的文档；lineage graph 是机器可查询的证据关系图。
- 与 observability / tracing：trace 记录运行时行为；lineage 把 trace 及其产物持久接到数据、模型、eval 和产品影响面。
- 与版本控制：版本控制跟踪文件或代码差异；lineage 跟踪样本级、artifact 级和 pipeline 级因果依赖。

## 工程实践

1. 给 artifact 统一 ID、hash、版本、tenant、权限和保留期。
2. 把每个数据转换写成 execution / activity，记录输入、输出、代码版本、prompt、模型、参数和时间。
3. 对训练、eval、RAG、memory、skill、router 和 self-improvement 候选保留 split 与用途标签。
4. 在数据进入 eval 或训练前查询近重复、公开 benchmark、hold-out 和 synthetic seed 的 lineage。
5. 让 deletion/export 请求能查询下游影响：哪些 chunks、memory、eval、training run、model、skill 或 report 受影响。
6. 事故发生时输出 evidence package：prompt、context、RAG docs、memory state、tool trace、model/provider version、policy decision 和受影响数据。
7. 对 self-improvement diff 要求引用 lineage：为什么改，证据来自哪条 trace/eval/数据，影响哪些版本。

## 评估方式

- Lineage coverage：关键 artifact 中有来源、活动和下游边的比例。
- Unknown provenance rate：来源、权限、transform 或 owner 缺失比例。
- Orphan artifact rate：找不到上游或下游的样本、模型、eval、memory、skill。
- Split contamination rate：train、eval、hold-out、公开 benchmark、synthetic seed 之间重复或近重复。
- Deletion/export impact time：从请求到定位下游影响并执行删除/导出的时间。
- Incident reconstruction completeness：能否重建事故涉及的 model、prompt、context、tool、identity、provider、data 和 policy。
- Rollback precision：能否只回滚受污染 artifact，而不误伤无关数据或模型。
- Lineage freshness：数据图是否落后于真实 pipeline、agent trace 或产品状态。

## 过时风险

- 具体 lineage 工具、schema 和存储会变化，但 entity / activity / agent / edge / metadata 的结构稳定。
- 过细粒度会带来成本和隐私风险；过粗粒度会无法做污染检测、删除和事故取证。
- Lineage 只能证明“来源和转换链”，不能自动证明语义正确、标签正确或权限合法；它必须连接 data quality 和 data rights。

## 一句话归类

Dataset lineage / provenance graph 主属第 6 层，是训练、eval、RAG、memory、skill、synthetic data、incident response 和 self-improvement 之间的证据血缘底座；它让“可追溯、可污染检测、可删除、可回滚、可审计”成为系统能力。

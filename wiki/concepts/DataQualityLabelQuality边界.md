---
address: c-000344
type: concept
title: "Data Quality / Label Quality 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - data-quality
  - label-quality
  - evals
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/RAG与Memory边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
sources:
  - "[[sources/tensorflow-data-validation-2026]]"
  - "[[sources/google-rules-of-ml-2026]]"
  - "[[sources/datasheets-for-datasets-2021]]"
  - "[[sources/data-cards-2022]]"
  - "[[sources/data-cascades-high-stakes-ai-2021]]"
  - "[[sources/openai-fine-tuning-data-quality-2026]]"
  - "[[sources/label-errors-benchmarks-2021]]"
  - "[[sources/huggingface-dataset-cards-2026]]"
  - "[[sources/eu-ai-act-data-governance-2024]]"
  - "[[sources/model-collapse-nature-2024]]"
  - "[[sources/w3c-prov-overview-2013]]"
  - "[[sources/tensorflow-ml-metadata-2026]]"
  - "[[sources/google-machine-unlearning-challenge-2023]]"
  - "[[sources/label-studio-annotation-quality-2026]]"
  - "[[sources/labelbox-quality-analysis-2026]]"
  - "[[sources/openai-evaluation-best-practices-2026]]"
---

# Data Quality / Label Quality 边界

Data quality / label quality 是第 6 层评估与可靠性层的数据质量门：它判断从产品、用户反馈、人工标注、合成数据、RAG 文档、agent trace 和外部数据源来的样本，是否足够可靠、授权、可追溯、可复现，能进入 eval、training、RAG、memory、skill 或 router。

一句话：**数据飞轮产生候选信号；data quality gate 决定这些信号能不能成为证据。**

## 主归属

- 主归属：6. 评估与可靠性层
- 上游输入：raw logs、feedback、labels、trace、RAG docs、synthetic data、human annotations、benchmark items
- 下游输出：accepted eval samples、training candidates、RAG updates、memory entries、skill candidates、rejected/review queue
- 权限门：7. 产品与组织层、[[concepts/DataRightsPrivacyConsent边界]]
- 反哺层级：2. 模型构建层、4. 上下文与知识层、6. eval、8. 自我改进

## 稳定链路

```text
raw data / label / feedback / trace
    -> rights and provenance check
    -> schema / validity / freshness / dedup checks
    -> label rubric and ambiguity review
    -> leakage / contamination / split check
    -> route to eval, training, RAG, memory, skill, or reject
    -> measure downstream impact and drift
```

## 数据质量维度

| 维度 | 问题 |
|---|---|
| Provenance | 数据从哪里来，谁生成，何时生成，用途权限是什么 |
| Validity | schema、格式、字段范围、类型和约束是否成立 |
| Completeness | 必要字段、上下文、label rationale、source 是否缺失 |
| Freshness | 数据是否过时，是否代表当前产品、模型和用户分布 |
| Representativeness | 是否覆盖真实任务、长尾、风险场景和用户群 |
| Dedup / leakage | 是否和训练集、公开 benchmark、hold-out 或历史样本重复 |
| Label correctness | 标注是否正确、一致、可解释，是否存在 ambiguity |
| Fit-for-purpose | 是否适合 eval、training、RAG、memory 或 skill 的具体目标 |

## 路由规则

| 候选数据 | 首选去向 | 质量门 |
|---|---|---|
| 真实失败案例 | Eval / regression | 可复现、预期结果明确、无泄露、权限清晰 |
| 高质量人工示范 | SFT / preference / distillation | rubric 清楚、label 校准、覆盖稳定行为 |
| 外部事实文档 | RAG / knowledge base | 来源可信、更新机制、chunk 质量、权限继承 |
| 用户偏好 | Memory / settings | 主体明确、时间戳、可见可删、冲突处理 |
| 重复成功 trace | Skill / workflow | 多次验证、无 secrets、可泛化、可测试 |
| 成本/延迟 telemetry | Router / serving | 可归因、样本足够、和质量指标分离 |
| 模糊或低置信标注 | Review / reject | 不能直接训练或进入 hold-out eval |

## 与相邻概念区别

- 与 [[concepts/DataFlywheelFeedbackLoop边界]]：data flywheel 产生信号；data quality 判断信号是否能成为证据。
- 与 [[concepts/DataRightsPrivacyConsent边界]]：data rights 判断能不能用；data quality 判断用起来是否可信。
- 与 eval：eval 是评测系统；data quality 决定 eval 样本本身是否可靠。
- 与训练数据：training data 是下游；label quality gate 防止错误、重复、污染、过时或不授权样本进入训练。
- 与 RAG：RAG 文档不只要“有内容”，还要来源、更新、权限、chunk 和 citation 质量。
- 与 reward hacking：低质量 label、污染 hold-out 和 benchmark leakage 会让指标被优化压力利用。
- 与 incident response：[[concepts/AIIncidentResponsePostmortem边界]] 产生事故样本；data quality gate 判断这些样本能否进入 regression eval、training、RAG、memory 或 skill。
- 与 synthetic data governance：[[concepts/SyntheticDataGovernance边界]] 是本页在合成样本上的专门规则，额外检查 generator、prompt、seed、contamination、model collapse 和 synthetic-real gap。
- 与 dataset lineage：[[concepts/DatasetLineageProvenanceGraph边界]] 提供来源、转换、split、版本和下游影响证据；data quality 使用这些证据判断样本是否可信。
- 与 data deletion / unlearning impact：[[concepts/DataDeletionUnlearningImpact边界]] 会删除或隔离不授权、错误或事故相关数据；本页负责复核清理后的 eval/training/RAG/memory/skill 质量和回归影响。
- 与 human feedback / annotation ops：[[concepts/HumanFeedbackAnnotationOps边界]] 负责人类标注、偏好、示范和复审流程；本页使用其 gold、consensus、rubric、adjudication 和 drift 证据判断 label 是否可信。
- 与 eval dataset lifecycle / benchmark governance：[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]] 管理整套 eval 的 split、版本、泄漏、刷新和退役；本页判断其中每条样本和 label 是否足够可信。

## 评估方式

- Schema anomaly rate：字段、类型、范围、分布异常比例。
- Label error estimate：抽样复审、confident learning、gold set、专家仲裁估计错误率。
- Inter-annotator agreement：标注员一致性和 rubric 清晰度。
- Leakage / contamination rate：train/eval/hold-out/benchmark 之间重复或近重复。
- Drift / skew：训练-服务偏差、时间漂移、用户群漂移、任务分布漂移。
- Dataset documentation completeness：dataset card / datasheet 是否说明来源、用途、限制、偏差和处理过程。
- Downstream impact：清洗或重标后 eval 稳定性、训练收益、真实任务成功率是否改善。

## 过时风险

- 具体数据验证工具会变化，但 provenance、schema、label、leakage、freshness、representativeness 和 downstream impact 稳定。
- 合成数据和 LLM-as-judge 会降低部分标注成本，也会引入模式坍缩、同质化、judge bias 和自我污染。
- 数据质量不能用单一分数表示；必须绑定下游用途。

## 一句话归类

Data quality / label quality 主属第 6 层，是 data flywheel、RAG、memory、skill、training 和 eval 之间的数据质量门；它防止“有数据”被误当成“有可用证据”。

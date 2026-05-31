---
address: c-000393
type: concept
title: "Evaluation Dataset Lifecycle / Benchmark Governance 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - benchmark-governance
  - dataset-lifecycle
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
sources:
  - "[[sources/openai-evaluation-best-practices-2026]]"
  - "[[sources/offline-metrics-predict-online-recsys-2020]]"
  - "[[sources/openai-evals-framework-2026]]"
  - "[[sources/openai-simple-evals-2026]]"
  - "[[sources/in-toto-test-result-predicate-2026]]"
  - "[[sources/helm-holistic-evaluation-2022]]"
  - "[[sources/safety-case-maintenance-slr-2021]]"
  - "[[sources/dynabench-2021]]"
  - "[[sources/livebench-2024]]"
  - "[[sources/benchmarking-benchmark-leakage-2024]]"
  - "[[sources/openai-sycophancy-gpt4o-rollback-2025]]"
  - "[[sources/llm-judges-alignment-vulnerabilities-2024]]"
---

# Evaluation Dataset Lifecycle / Benchmark Governance 边界

Evaluation dataset lifecycle / benchmark governance 是第 6 层评估与可靠性层的 eval 数据治理边界：它管理 eval set、private hold-out、public benchmark、regression suite、red-team set、canary set 和 production shadow set 从创建、校准、运行、版本化、泄漏防护、刷新到退役的完整生命周期。

一句话：**eval 不是一次性表格；它是会泄漏、饱和、漂移、被优化、需要版本和退役的质量门资产。**

## 主归属

- 主归属：6. 评估与可靠性层
- 上游输入：产品目标、风险场景、失败 trace、人工反馈、benchmark、production logs、incident、data rights、lineage
- 下游输出：versioned eval suite、private hold-out、public benchmark result、release gate、regression signal、retirement decision
- 产品接口：7. 产品与组织层
- 模型接口：2. 模型构建层
- 自我改进接口：8. 自我改进与前沿层

## 稳定链路

```text
capability / product / risk gap
    -> eval objective, owner, decision it controls
    -> sample sourcing with rights, provenance, coverage, and difficulty target
    -> split: dev/tuning, regression, private hold-out, public benchmark, adversarial, canary, shadow production
    -> rubric, grader, metric, human calibration, and flakiness check
    -> versioned dataset card, lineage, leakage controls, access policy
    -> run in CI, release gate, model/provider comparison, post-market monitoring
    -> analyze drift, saturation, contamination, production correlation, and actionability
    -> refresh, expand, quarantine, promote, or retire samples
    -> feed fixes to context, tools, RAG, model routing, training, product, or incident process
```

## Eval Set 类型

| 类型 | 控制什么决策 | 主要风险 |
|---|---|---|
| Dev / tuning set | prompt、grader、tool、router 和模型选择迭代 | 被反复优化后失去泛化性 |
| Regression suite | 防止已修复行为回归 | 只覆盖旧 bug，忽略新分布 |
| Private hold-out | 真实泛化和发布门 | 泄漏、样本过少、代表性不足 |
| Public benchmark | 横向模型比较和社区透明度 | 训练污染、leaderboard gaming、饱和 |
| Red-team / adversarial set | 安全和边界行为 | 攻击模式过时或泄漏 |
| Canary set | 监控 silent model/provider change | 样本太少、误报 |
| Production shadow eval | 真实流量分布和 drift | 权限、隐私、标注成本 |
| Live / renewable benchmark | 抗污染、抗饱和 | 更新机制、可复现性和成本 |

## 与相邻概念区别

- 与 eval harness：eval harness 运行任务和 grader；本页治理 eval dataset 本身的来源、split、版本、泄漏、刷新和退役。
- 与 [[concepts/ReasoningEvalVerifier边界]]：verifier/grader 是评分器；本页决定哪些样本进入哪个 eval set，以及这些样本何时可信、泄漏或退役。
- 与 [[concepts/DataQualityLabelQuality边界]]：data quality 判断单条样本/label 是否可用；本页管理整套 eval 的覆盖、代表性、生命周期和决策用途。
- 与 [[concepts/HumanFeedbackAnnotationOps边界]]：annotation ops 生产 gold labels、rubric 和 expert review；本页把它们组织成可重复运行的 eval suites。
- 与 [[concepts/RewardHackingEvalOverfitting边界]]：reward hacking 是失效模式；benchmark governance 是防线，负责 hold-out、leakage、refresh、anti-gaming 和 retirement。
- 与 [[concepts/DatasetLineageProvenanceGraph边界]]：lineage 证明 eval 样本来源、split、版本和训练接触历史；本页消费这些证据做 governance decision。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：本页维护 release gate 所消费的 eval 数据资产；release/rollback gate 决定候选变更能否进入真实流量、灰度或回滚。
- 与 [[concepts/LLMJudgeAIFeedbackCalibration边界]]：eval suite 中的 LLM judge 也是资产的一部分，必须记录 judge model、prompt、rubric、gold anchor、bias tests 和 drift。
- 与 [[concepts/JudgeDriftGraderObservability边界]]：本页维护 canary、hold-out 和 shadow eval samples；grader observability 用这些样本持续检测评分器漂移。
- 与 [[concepts/EvalPortfolioMetricHierarchy边界]]：本页治理每个 eval asset；eval portfolio 决定这些 asset 在 hard stop、guardrail、primary、slice、online 或 diagnostic 证据中的位置。
- 与 [[concepts/EvidenceFreshnessStaleProof边界]]：本页决定 eval asset 何时刷新或退役；freshness/stale proof 给具体 eval result 记录是否仍能支持当前 decision。
- 与 [[concepts/EvidenceAttestationSignedEvalArtifact边界]]：本页治理 eval asset 生命周期；signed eval artifact 保护某次 eval run、result、dataset split、grader 和 config 在进入 release gate 前没有被替换。
- 与 [[concepts/EvalResultInterpretationDecisionThreshold边界]]：本页治理 eval 数据和 benchmark 是否可信；decision threshold 解释这些结果是否足以支持发布、回滚或继续调查。
- 与 [[concepts/OfflineOnlineEvalCorrelation边界]]：本页管理 eval asset 的生命周期；offline/online correlation 用真实生产 outcome 评估这些 asset 是否仍能预测上线效果。
- 与 [[concepts/ProductionContractCompatibilityTest边界]]：production contract 把产品承诺映射成 eval suites；本页负责这些 suites 的版本、覆盖、泄漏、刷新和退役。
- 与 public benchmark：public benchmark 是 eval asset 的一种；不能替代 private product eval 和 production monitoring。

## 工程实践

1. 每个 eval set 必须记录 objective、owner、decision、scope、risk tier、data rights、version 和 freshness。
2. 明确 split：开发调参集、回归集、私有 hold-out、公开 benchmark、red-team set 不混用。
3. 给每条样本保存 lineage：来源、创建时间、model/version exposure、rubric version、grader、labeler、权限和下游使用。
4. 对公开 benchmark 做 contamination check：近重复、训练数据命中、公开可见时间、异常低 perplexity、模型声明 transparency card。
5. 对私有 eval 做 leakage control：访问控制、最小共享、结果聚合、样本轮换和不可直接训练规则。
6. 给 eval 设置刷新和退役条件：饱和、漂移、泄漏、真实任务不相关、grader 不稳定、产品目标改变。
7. 把 eval failure 转成 action：context/RAG/tool/prompt/router/training/product/incident，而不是只记录分数。

## 评估方式

- Coverage：真实任务、长尾、风险场景、用户群、语言、模态和工具路径是否覆盖。
- Production correlation：eval 分数变化是否预测真实成功率、投诉、人工接管、事故和 ROI。
- Leakage / contamination rate：样本是否进入训练、公开网页、调参或模型选择反馈。
- Saturation：强模型是否都接近满分，导致无法区分能力。
- Freshness / drift：样本是否代表当前产品、知识、用户和模型行为。
- Grader calibration：自动 grader、LLM judge 和人工 gold 是否一致。
- Flakiness：同一模型/配置重复运行分数是否稳定。
- Actionability：失败是否能归因并转成具体修复。
- Retirement precision：是否及时移除过时、泄漏、重复、低区分度或不再相关样本。

## 过时风险

- 具体 benchmark 会持续变化，但 eval asset lifecycle 稳定：create → calibrate → version → run → monitor → refresh → retire。
- 越流行的公开 benchmark 越容易污染和饱和；产品系统必须维护私有、动态、生产相关的 eval。
- Live benchmark 和 synthetic benchmark 能缓解污染，但也引入可复现性、质量和生成器偏差问题。
- LLM-as-judge 会降低评分成本，也会带来 grader hacking 和 judge drift，需要 human gold 校准。

## 一句话归类

Evaluation dataset lifecycle / benchmark governance 主属第 6 层，是 eval 数据集作为质量门资产的生命周期治理；它把 data quality、human feedback、lineage、anti-leakage、public benchmark、private hold-out 和 release gate 连接成稳定闭环。

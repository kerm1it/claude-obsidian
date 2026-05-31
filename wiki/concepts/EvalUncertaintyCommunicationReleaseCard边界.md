---
address: c-000443
type: concept
title: "Eval Uncertainty Communication / Release Card 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - uncertainty
  - release-card
  - reliability
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/MetricConflictResolution边界]]"
  - "[[concepts/IntolerableRiskThresholdStopRule边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/MonitorTabletopRunbookDrill边界]]"
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
sources:
  - "[[sources/responsible-ai-tensions-tradeoffs-2023]]"
  - "[[sources/slsa-verification-summary-attestation-v1-2-2026]]"
  - "[[sources/nist-sp800-37-risk-response-2018]]"
  - "[[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]"
  - "[[sources/fema-hseep-exercise-evaluation-2020]]"
  - "[[sources/nist-ai-evaluation-statistical-models-2026]]"
  - "[[sources/adding-error-bars-evals-2024]]"
  - "[[sources/model-cards-for-model-reporting-2019]]"
  - "[[sources/riskcards-language-model-deployment-2023]]"
  - "[[sources/sphere-evaluation-card-2025]]"
  - "[[sources/google-model-card-toolkit-2026]]"
  - "[[sources/sigstore-cosign-verifying-attestations-2026]]"
  - "[[sources/openai-gpt-4o-system-card-2024]]"
  - "[[sources/openai-trustworthy-third-party-evaluations-2026]]"
  - "[[sources/betterbench-benchmark-quality-2024]]"
  - "[[sources/langsmith-evaluation-types-2026]]"
  - "[[sources/nist-deployed-ai-monitoring-challenges-2026]]"
  - "[[sources/openai-evals-business-framework-2025]]"
  - "[[sources/dynamic-safety-cases-changing-world-2025]]"
  - "[[sources/nist-sp800-53-au11-audit-record-retention-2025]]"
  - "[[sources/nist-sp800-55-measurement-guide-2024]]"
---

# Eval Uncertainty Communication / Release Card 边界

Eval uncertainty communication / release card 是第 6 层评估与可靠性层到第 7 层产品与组织层的证据表达边界：它把 eval 分数、置信区间、方差、slice 风险、judge health、coverage gap、hard stop、例外和后续监控，整理成决策者能消费的 release / eval card。

一句话：**第 6 层负责测量和解释不确定性；release card 负责让第 7 层看懂“这份证据能支持什么决策、不能支持什么决策”。**

## 主归属

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游输入：eval objective、benchmark/report、metric table、uncertainty interval、slice count、grader health、coverage limitation、risk threshold、production monitor
- 下游输出：release card、eval card、decision memo、dashboard annotation、gray-zone review、exception record、post-release validation plan
- 执行接口：[[concepts/ModelReleaseRollbackGate边界]]

## 稳定链路

```text
eval package and decision question
    -> score table with baseline, sample size, confidence interval, repeated trials, slice counts, flakiness
    -> validity notes: dataset scope, benchmark quality, judge health, leakage, production correlation, known blind spots
    -> decision language: pass, fail, gray zone, canary, human review, no-go, rollback, more evidence
    -> release card: claim, evidence, uncertainty, limitations, risk owner, exception, rollback trigger, monitor
    -> decision owner acts through release gate or safety governance
    -> post-release comparison refreshes eval, threshold, card template, and production monitor
```

## Release / Eval Card 字段

| 字段 | 回答的问题 | 常见缺口 |
|---|---|---|
| Decision claim | 这张卡支持哪个发布、回滚、路由或训练决策？ | 只报告分数，不说控制什么动作 |
| System under test | 测的是哪个 model/prompt/router/tool/RAG/provider 版本？ | 模型 alias 或 prompt hash 不清 |
| Evidence table | baseline、candidate、CI、样本量、重复次数、slice | 只有平均分，没有区间和分布 |
| Validity scope | eval 覆盖哪些任务、人群、语言、工具路径和风险？ | 把 benchmark 外推到所有产品场景 |
| Grader health | judge、rubric、human anchor、schema failure 是否稳定？ | 评分器漂移还继续使用结果 |
| Limitations | 这次 eval 不能证明什么？ | 把无证据说成“未发现风险” |
| Decision band | pass/fail/gray-zone/canary/no-go 规则是什么？ | 灰区被隐藏成单一通过/失败 |
| Owner and exception | 谁能接受 residual risk，例外期限和复审条件是什么？ | 例外无 owner、无过期日 |
| Rollback / monitor | 上线后看哪些信号，何时回滚或补证据？ | 离线 eval 与生产结果断开 |

## 与相邻概念区别

- 与 [[concepts/EvalResultInterpretationDecisionThreshold边界]]：decision threshold 把分数解释成 pass/fail/gray-zone；本页把解释结果、 uncertainty 和 limitation 打包成可审查的决策材料。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 执行发布、灰度、回滚；release card 是 gate 消费的证据包，不是 gate 本身。
- 与 [[concepts/JudgeDriftGraderObservability边界]]：grader observability 判断评分器是否健康；本页要求把 judge health 和 score quarantine 状态显式写进卡片。
- 与 [[concepts/EvalPortfolioMetricHierarchy边界]]：eval portfolio 定义本次变更需要哪些证据和优先级；release card 把 portfolio 的结果、冲突、限制和 owner 写给决策者。
- 与 [[concepts/MetricConflictResolution边界]]：metric conflict resolution 决定冲突怎么处理；release card 把冲突、rationale、override、owner、expiry 和 monitor 写下来。
- 与 [[concepts/IntolerableRiskThresholdStopRule边界]]：stop rule 定义 hard no-go；release card 必须把 hard stop 和 residual risk 放在平均分之前。
- 与 [[concepts/OverrideGovernanceResidualRiskAcceptance边界]]：release card 表达 override rationale 和证据局限；override governance 定义批准权限、期限、监控、回滚、续期和撤销规则。
- 与 [[concepts/OfflineOnlineEvalCorrelation边界]]：release card 写明上线前预测、局限和 monitor；offline/online correlation 在上线后检验这些预测是否和真实 outcome 同向。
- 与 [[concepts/PostReleaseEvalDrift边界]]：release card 固化发布时的证据和监控计划；post-release eval drift 检查卡片里的证据、阈值和 monitor 何时变 stale。
- 与 [[concepts/EvidenceFreshnessStaleProof边界]]：release card 需要消费 freshness 状态，明确每条证据是 fresh、stale、expired、superseded、invalidated 还是 unknown。
- 与 [[concepts/EvidenceAttestationSignedEvalArtifact边界]]：release card 表达证据、局限和决策；signed evidence bundle 让卡片引用的 eval result、artifact、prompt、judge 和 policy verification 可被机器验证。
- 与 [[concepts/VerifierPolicyTrustRootRotation边界]]：release card 记录 verification summary、policy version 和 trust-root version；verifier policy 决定这些引用证据是否仍能被接受。
- 与 [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]：release card 是某次决策的证据摘要；audit packet lifecycle 保存卡片背后的 eval runs、bundles、approvals、policy context、monitor snapshots 和 disposition record。
- 与 [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]：release card 记录单次例外和证据局限；override debt dashboard 聚合多张 card 中的例外率、续期和事故转化。
- 与 [[concepts/MonitorOwnershipEscalationLadder边界]]：release card 记录 post-release monitor 和 owner；monitor ownership 定义信号触发后谁响应、何时升级和如何关闭。
- 与 [[concepts/MonitorTabletopRunbookDrill边界]]：release card 写明 monitor、rollback trigger、owner 和 limitation；tabletop/drill 验证这些字段是否能指导真实交接和行动。
- 与 [[concepts/SafetyCaseAssuranceCase边界]]：release card 是单次变更的证据摘要；safety case 是高风险系统把多轮证据组织成 claims-arguments-evidence 的完整论证包。
- 与 model card / system card：model/system card 是模型或系统级透明度文档；release card 是某一次变更或用例的决策文档。
- 与 dashboard：dashboard 持续展示信号；release card 固化某次决策时点的证据、局限、owner 和行动。
- 与 safety case：safety case 是更完整的论证包；release card 是日常 AI 变更 gate 的轻量证据卡。

## 工程实践

1. 每个 eval report 先写 decision question：发布、回滚、router 调整、训练数据准入、人工复核还是补样本。
2. 指标表必须同时给出 baseline、candidate、样本量、CI/SEM/bootstrap、重复次数、slice count 和 flakiness。
3. 分开 primary、guardrail、diagnostic 指标；guardrail 和 hard stop 不被平均质量提升抵消。
4. 把“what this eval cannot prove”写成固定字段：覆盖缺口、数据陈旧、judge 弱点、prompt/tool 路径缺失、生产相关性不足。
5. 灰区必须有动作：canary、human review、专家复核、补样本、延迟发布、限制范围或 no-go。
6. 把 release card 绑定 artifact identity：model snapshot、prompt hash、router version、skill/tool package、RAG index 和 provider region。
7. 卡片要链接 live dashboard，但 dashboard 不能替代卡片；决策需要冻结证据版本和 owner。
8. 发布后比较 card 预测与真实 outcome：投诉、人工接管、incident、cost、latency、SLO、用户满意度和 rollback。

## 评估方式

- Decision-maker comprehension：reviewer 是否能准确说出证据支持的决策和限制。
- False confidence reduction：卡片是否减少“分数高就安全”的错误解读。
- Traceability：每个 claim 是否能追溯到 eval run、dataset version、grader version 和 source。
- Gray-zone handling：不确定结果是否进入明确复核动作，而不是被默认放行。
- Exception quality：例外是否有 owner、期限、缓解、监控和复审。
- Production correlation：release card 中的风险判断是否和生产 signal 同向。
- Freshness：卡片是否在 model/provider/prompt/rubric/data 分布变化后被标记 stale。

## 过时风险

- 具体卡片模板、dashboard 工具和统计方法会变化，但“证据 → uncertainty/limitations → decision language → owner/action → monitor”的链路稳定。
- 模型越强，单一平均分越会制造 false confidence；release card 必须越来越重视 slice、tool path、judge health、production correlation 和 hard stop。
- 如果卡片只做对外透明而不绑定 release gate，它会退化成文档；如果只做内部 gate 而不写 limitation，它会放大组织误判。

## 一句话归类

Eval uncertainty communication / release card 主属第 6 层，是 eval evidence 进入第 7 层 release、rollback、safety governance 和组织 owner 前的证据表达边界；它保证不确定性、灰区和局限不会在决策链路中丢失。

---
address: c-000400
type: concept
title: "Model Release / Rollback Gate 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - release-gate
  - rollback
  - governance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/SkillLibraryRouting生命周期]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/MetricConflictResolution边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/MonitorTabletopRunbookDrill边界]]"
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
  - "[[concepts/IntolerableRiskThresholdStopRule边界]]"
  - "[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
  - "[[concepts/ReleaseGateDebtBypassDetection边界]]"
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
sources:
  - "[[sources/google-sre-canarying-releases-2018]]"
  - "[[sources/sigstore-policy-controller-2026]]"
  - "[[sources/nist-sp800-37-risk-response-2018]]"
  - "[[sources/aws-security-ir-simulations-2026]]"
  - "[[sources/nist-sp800-61r3-incident-response-2025]]"
  - "[[sources/microsoft-ai-incident-response-readiness-2026]]"
  - "[[sources/openai-sycophancy-gpt4o-rollback-2025]]"
  - "[[sources/openai-model-deprecations-2026]]"
  - "[[sources/openai-model-release-notes-2026]]"
  - "[[sources/anthropic-model-deprecations-2026]]"
  - "[[sources/google-cloud-deploy-automation-2026]]"
  - "[[sources/github-actions-deployment-protection-rules-2026]]"
  - "[[sources/gitlab-protected-environments-deployment-approvals-2026]]"
  - "[[sources/google-cloud-deploy-approvals-policies-audit-2026]]"
  - "[[sources/test-before-you-deploy-llm-supply-chain-2026]]"
  - "[[sources/slsa-verifying-artifacts-v1-2-2026]]"
  - "[[sources/openssf-model-signing-2026]]"
  - "[[sources/google-mlops-continuous-delivery-2026]]"
  - "[[sources/openai-preparedness-framework-2025]]"
  - "[[sources/aws-prescriptive-genai-production-monitoring-2026]]"
  - "[[sources/openai-evals-business-framework-2025]]"
  - "[[sources/cmu-sei-drift-monitoring-ml-systems-2026]]"
  - "[[sources/nist-sp800-92r1-log-management-2023]]"
  - "[[sources/google-sre-good-housekeeping-error-budget-debt-2018]]"
  - "[[sources/sigstore-policy-controller-2026]]"
  - "[[sources/automated-self-testing-quality-gate-llm-applications-2026]]"
  - "[[sources/moss-self-evolution-source-rewriting-2026]]"
---

# Model Release / Rollback Gate 边界

Model release / rollback gate 是第 7 层产品与组织层的变更控制边界：它把第 6 层 eval、monitoring、risk evidence 和 lineage，转成模型、prompt、router、skill、tool、provider 或 policy 变更能否发布、灰度、暂停、回滚或迁移的可执行决策。

一句话：**eval 说明候选是否达标；release gate 决定它能不能进真实流量，并准备坏了以后怎么退回来。**

## 主归属

- 主归属：7. 产品与组织层
- 质量输入：6. 评估与可靠性层
- 上游输入：candidate model/prompt/router/skill/tool/provider、eval suite、risk tier、lineage、SLO、data rights、incident history、migration deadline
- 下游输出：release decision、canary/AB/shadow plan、rollback plan、release notes、migration task、owner、audit evidence
- 影响层级：2. 模型构建层、3. 推理与能力层、4. 上下文与知识层、5. Agent 系统层、6. 评估与可靠性层

## 稳定链路

```text
change proposal: model / prompt / router / skill / tool / provider / policy
    -> artifact identity, version pin, owner, blast radius, and risk tier
    -> required eval suite: regression, private hold-out, safety, cost/latency, tool/data/provider checks
    -> release checkpoint: thresholds, exception path, approval authority, rollback criteria
    -> staged deployment: shadow, canary, A/B, beta/alpha, region or tenant ramp
    -> online monitoring: quality, safety, latency, cost, complaints, incident signals, provider drift
    -> decision: promote, hold, rollback, disable, route around, or migrate
    -> release notes, audit trail, postmortem, regression update, and next gate revision
```

## 变更对象

| 对象 | 典型 gate | 主要回滚动作 |
|---|---|---|
| Model snapshot / alias | private eval、safety eval、behavior eval、latency/cost、canary | pin old snapshot、restore alias、route to fallback |
| Prompt / system policy | regression、red-team、style/behavior checks | revert prompt version、disable feature flag |
| Router / cascade | cost-quality frontier、false downgrade、escalation eval | freeze router、force strong model、restore previous weights |
| Skill / tool | invocation eval、permissioning、sandbox、supply-chain scan | disable skill/tool、revoke credential、rollback package |
| Provider / region | data rights、retention、SLA、quality parity、fallback drill | route away、fail closed、switch provider |
| RAG / memory / knowledge base | groundedness、staleness、privacy、deletion impact | restore index, tombstone bad docs, disable memory write |

## 与相邻概念区别

- 与 [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]：eval lifecycle 维护可置信的测试资产；release gate 消费这些资产来做上线/回滚决策。
- 与 [[concepts/EvalPortfolioMetricHierarchy边界]]：eval portfolio 决定哪些指标可拦发布、哪些只诊断；release gate 消费这个分层证据组合来执行行动。
- 与 [[concepts/MetricConflictResolution边界]]：metric conflict resolution 决定多指标冲突时 block、restrict、canary、hold 或 override；release gate 执行这些动作。
- 与 [[concepts/EvalResultInterpretationDecisionThreshold边界]]：decision threshold 把 eval 分数、不确定性和风险容忍度解释成 pass/fail/gray-zone；release gate 负责执行灰度、发布、回滚或例外。
- 与 [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：release card 是 gate 的证据包，记录 claim、uncertainty、limitation、owner、exception 和 rollback trigger；release gate 负责行动。
- 与 [[concepts/OfflineOnlineEvalCorrelation边界]]：release gate 放行后，线上 canary/A-B/monitoring 要反校准离线 eval；相关性下降时，gate 应降权或冻结对应指标。
- 与 [[concepts/PostReleaseEvalDrift边界]]：release gate 执行 canary、rollback、disable 或 refresh；post-release eval drift 提供证据 stale、分布漂移和 monitor breach 的触发信号。
- 与 [[concepts/EvidenceFreshnessStaleProof边界]]：release gate 不应消费 expired、invalidated 或 unknown 证据；freshness 状态决定是否需要补证据、灰度或回滚。
- 与 [[concepts/EvidenceAttestationSignedEvalArtifact边界]]：release gate 执行动作；attestation 是 gate 在放行前验证 eval bundle、model、prompt、judge、container 和 policy verification 的证据完整性检查。
- 与 [[concepts/VerifierPolicyTrustRootRotation边界]]：release gate 执行 block、hold、fallback、rollback 或 override review；verifier policy 决定 signed evidence 是否按当前 trust root 和 policy 通过。
- 与 [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]：release gate 消费 verifier 结果；cross-verifier conformance test 防止 CI 通过、gate 拒绝或 admission 放行这类策略漂移。
- 与 [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]：release gate 生成 release/rollback/override 决策；audit packet lifecycle 把 gate 消费和产出的证据打包留存，供多年后检索、重验和处置。
- 与 [[concepts/MonitorOwnershipEscalationLadder边界]]：release gate 执行动作；monitor ownership 决定哪个 monitor breach 由谁确认、何时 hold rollout、何时 rollback 或升级 incident。
- 与 [[concepts/MonitorTabletopRunbookDrill边界]]：release gate 定义 hold、canary、rollback 和 fallback；runbook drill 验证这些动作的权限、owner、证据和沟通链是否能按时执行。
- 与 [[concepts/SafetyCaseAssuranceCase边界]]：高风险 release gate 需要 safety case 作为论证依据；gate 执行 safety case 得出的 deploy、restrict、pause、rollback 或 external review 决策。
- 与 [[concepts/ProductionContractCompatibilityTest边界]]：production contract 定义什么叫产品行为仍兼容；release gate 消费 compatibility report 来执行迁移、灰度、回滚或 provider route-around。
- 与 [[concepts/IntolerableRiskThresholdStopRule边界]]：release gate 执行 hard stop；intolerable risk threshold 定义哪些风险触发 no-go、pause、限制、外部审查或 rollback。
- 与 [[concepts/OverrideGovernanceResidualRiskAcceptance边界]]：release gate 执行例外放行、限制、hold 或 rollback；override governance 决定例外是否具备 authority、expiry、monitor 和 residual-risk record。
- 与 [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]：release gate 执行单次发布动作；override debt dashboard 发现 gate 是否被重复 exception、过期例外或 shadow approval 稀释。
- 与 [[concepts/ReleaseGateDebtBypassDetection边界]]：release gate 执行单次放行、灰度和回滚；gate bypass detection 证明真实生产变更都经过 gate，或发现 direct-to-prod、admin bypass、stale exception 和 unprotected environment。
- 与 [[concepts/SelfImprovementGateChangeRiskBudget边界]]：release gate 控制一般生产变更；self-improvement gate 控制系统自己提出的 proposed diff，并把中高风险改动升级到本页的 release/rollback gate。
- 与 [[concepts/AISafetyOpsGovernance边界]]：safety ops 定义风险 owner、阈值和例外；release gate 是这些规则在每次变更上的执行点。
- 与 [[concepts/AIIncidentResponsePostmortem边界]]：incident response 是出事后的止血和复盘；rollback gate 要在发布前就准备好可执行回退。
- 与 [[concepts/MultiProviderGovernance边界]]：provider governance 决定哪些供应商有资格；release gate 决定具体 provider/model 更新何时进入流量。
- 与 [[concepts/ModelRoutingMixture边界]]：routing 是运行时选择路径；release gate 控制 routing policy 或 model pool 的变更。
- 与普通 CI/CD：AI release gate 还要评估非确定性行为、模型漂移、prompt/context 依赖、tool 副作用、数据权利和 provider silent update。

## 工程实践

1. 固定 artifact identity：model snapshot、prompt hash、router version、skill package、tool schema、provider region 和 data policy。
2. 给每次变更写 release card：目标、非目标、风险层、owner、影响用户、迁移窗口、rollback owner。
3. 把第 6 层 eval suite 绑定到 gate：regression、private hold-out、red-team、behavior、latency/cost、permission、data rights、provider parity。
4. 使用 staged rollout：shadow、internal dogfood、opt-in alpha、canary、A/B、tenant/region ramp。
5. 设置 rollback trigger：eval miss、用户投诉、SLO 破坏、cost spike、安全告警、provider incident、data rights violation。
6. 对 silent provider update 和 model alias 漂移，使用 canary prompts、contract tests、snapshot pinning 和 compatibility gates。
7. 发布后写 release notes 和 audit trail；事故或回滚后把失败样本加入 regression eval。

## 评估方式

- Gate precision：阻断的变更是否真的高风险，放行的变更是否稳定。
- Rollback readiness：是否能在目标时间内回到上一个稳定版本或 fallback path。
- Canary detection：小流量阶段能否捕捉真实质量、安全、延迟、成本和行为回归。
- Version coverage：关键 artifact 是否都有版本、owner、lineage 和 release card。
- Migration health：弃用或供应商变更是否有影响面、替代方案、测试结果和截止日期。
- Drift detection：provider silent update、alias 变化、prompt/context 改动后是否被 contract tests 发现。
- Post-release incident rate：发布后事故、回滚、热修、用户投诉和 regression escape 的频率。

## 过时风险

- 具体发布平台、模型 API 和 provider 生命周期会变化，但 artifact identity → eval gate → staged rollout → monitoring → rollback → regression 的链路稳定。
- 模型越强，越需要行为、人格、工具副作用和长程任务 gate；只看 benchmark 或单轮 accuracy 会越来越不够。
- Provider 托管模型会带来 silent update 与 deprecation 风险，应用侧需要自己的 compatibility gate。

## 一句话归类

Model release / rollback gate 主属第 7 层，是 AI 变更进入真实产品流量的组织执行边界；它消费第 6 层 eval 和 monitoring，约束第 2/3/4/5 层 artifact 的上线、灰度、回滚和迁移。

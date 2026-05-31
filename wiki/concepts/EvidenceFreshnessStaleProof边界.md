---
address: c-000476
type: concept
title: "Evidence Freshness / Stale Proof 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - evidence
  - freshness
  - assurance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/MonitorTabletopRunbookDrill边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
sources:
  - "[[sources/slsa-verifying-artifacts-v1-2-2026]]"
  - "[[sources/tuf-root-metadata-api-2021]]"
  - "[[sources/nist-sp800-84-tte-program-2006]]"
  - "[[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]"
  - "[[sources/safety-case-maintenance-slr-2021]]"
  - "[[sources/dynamic-safety-cases-changing-world-2025]]"
  - "[[sources/runtime-confidence-safety-arguments-2026]]"
  - "[[sources/cmu-sei-drift-monitoring-ml-systems-2026]]"
  - "[[sources/nist-deployed-ai-monitoring-challenges-2026]]"
  - "[[sources/openai-evaluation-best-practices-2026]]"
  - "[[sources/google-ml-test-score-2016]]"
  - "[[sources/nist-sp800-92r1-log-management-2023]]"
---

# Evidence Freshness / Stale Proof 边界

Evidence freshness / stale proof 是第 6 层评估与可靠性层的证据有效期边界：它给每条 eval、release card、safety case、benchmark、judge、monitor、red-team、contract test 和 production outcome 证据记录“在什么条件下仍然有效、什么时候过期、什么变化会使它失效、如何证明它仍可用于当前决策”。

一句话：**证据不是越多越好，而是要知道哪份证据现在还能支持哪个决策。**

## 主归属

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游输入：evidence artifact、claim、artifact identity、validity scope、assumptions、runtime monitor、change event、lineage、owner
- 下游输出：fresh / stale / expired / superseded / invalidated / unknown 状态、stale proof、refresh task、quarantine、release-card update、safety-case refresh
- 证据底座：[[concepts/DatasetLineageProvenanceGraph边界]]

## 稳定链路

```text
decision claim and evidence artifact
    -> freshness metadata: collected_at, observed_window, valid_until, owner, scope, assumptions
    -> dependency map: model, prompt, tool, RAG, dataset, judge, provider, policy, user segment
    -> freshness triggers: time expiry, artifact change, distribution drift, monitor breach, incident, policy/risk change
    -> stale proof: identity match, no invalidating change, current distribution within scope, monitor healthy
    -> decision: use, downgrade, quarantine, refresh, restrict, rollback, or safety-case update
    -> record result in release card, evidence ledger, eval portfolio, and post-release drift loop
```

## 证据状态

| 状态 | 含义 | 典型动作 |
|---|---|---|
| Fresh | 证据仍在有效窗口和适用范围内 | 可进入 threshold / release card |
| Stale | 证据可能过期，但未被明确推翻 | 降权、补证据、灰区 |
| Expired | 时间窗口或复审期限已过 | 重新运行 eval / review |
| Superseded | 有新证据替代旧证据 | 更新 evidence map |
| Invalidated | 关键假设、artifact 或分布变化已推翻证据 | quarantine、rollback、case refresh |
| Unknown | 缺少 lineage、owner、时间或依赖信息 | 不得作为高风险 gate 证据 |

## 与相邻概念区别

- 与 [[concepts/PostReleaseEvalDrift边界]]：post-release drift 监控证据是否因线上变化失效；本页定义每条证据的有效期、失效触发器和 stale proof 字段。
- 与 [[concepts/EvalPortfolioMetricHierarchy边界]]：portfolio 定义哪些证据组成质量门；freshness/stale proof 判断这些证据还能不能被使用。
- 与 [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：release card 表达某次决策的证据和限制；本页要求卡片标明每份证据的 freshness 状态和刷新条件。
- 与 [[concepts/SafetyCaseAssuranceCase边界]]：safety case 组织 claims-arguments-evidence；本页维护 evidence、assumptions 和 operational data 是否仍支撑对应 claim。
- 与 [[concepts/MonitorOwnershipEscalationLadder边界]]：freshness 判断证据状态；monitor ownership 决定 stale、expired、invalidated 或 unknown 证据由谁刷新、降权、隔离或升级。
- 与 [[concepts/MonitorTabletopRunbookDrill边界]]：freshness 定义 stale/expired/invalidated/unknown 状态；tabletop/drill 验证这些状态触发后谁刷新证据、谁 hold release、谁更新 safety case。
- 与 [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]：eval lifecycle 管测试资产；本页给每个 eval result 和 dataset version 加有效期、依赖和失效证明。
- 与 [[concepts/EvidenceAttestationSignedEvalArtifact边界]]：freshness 判断已验证证据是否仍适用；attestation 先证明证据 artifact、签名、subject digest、producer 和 verifier policy 是否可信。
- 与 [[concepts/VerifierPolicyTrustRootRotation边界]]：freshness 判断证据是否仍支持 claim；verifier policy 判断信任根、签名身份、policy version 和 TUF metadata 是否仍可接受。
- 与 [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]：freshness 判断证据是否仍可用于当前 claim；retention lifecycle 决定 stale/expired 证据是否仍要作为历史发布、事故或审计证据保存。
- 与 generic timestamp：timestamp 只说明何时产生；stale proof 说明为什么现在仍可用于当前 claim。

## 工程实践

1. 每条证据必须带 claim id、decision id、artifact identity、owner、collected_at、observed_window、valid_until 和 confidence。
2. 记录 validity scope：任务、人群、语言、风险层、工具路径、provider、model/prompt/RAG/judge 版本。
3. 区分时间过期和事件失效：到期只是 expired；模型、prompt、tool、RAG、judge、provider、policy、用户分布变化可直接 invalidated。
4. 给 release card 和 safety case 建 evidence ledger，显示每条证据的状态、依赖、刷新 SLA 和下一位 owner。
5. 高风险证据默认需要 active monitor 或 runtime performance indicator；没有 monitor 的证据只能有较短有效期。
6. stale 证据可以作为背景，不应直接支持 hard stop 之外的放行决策；unknown 证据不得进入高风险 gate。
7. 自动触发 refresh：post-release drift、incident、provider silent update、eval set contamination、judge health 下降、policy/risk tolerance 变化。

## 评估方式

- Freshness coverage：release card / safety case 里有多少证据带完整 freshness metadata。
- Stale-evidence escape：已 stale / invalidated 的证据是否仍进入 release gate。
- Refresh SLA：证据过期或失效后多久被重跑、替换或降权。
- Dependency coverage：model、prompt、RAG、tool、dataset、judge、provider、policy 是否都在依赖图中。
- Invalidation precision / recall：触发器是否准确识别真正影响 claim 的变化。
- Audit traceability：审查者能否从 claim 追溯到最新证据、失效触发器和 owner。
- Decision impact：freshness gate 是否减少 false pass、事故、回滚和 stale safety case。

## 过时风险

- 具体证据平台、签名方式和自动化工具会变化，但 evidence ledger、validity scope、dependency map、stale trigger、refresh action 稳定。
- 对快速变化的 LLM 产品，证据有效期通常比传统软件短；尤其是 provider alias、judge、prompt、RAG corpus、tool schema 和用户分布。
- 如果 freshness 只靠人工审查，会随证据数量扩张而失效；高风险系统需要事件触发和自动 stale flag。

## 一句话归类

Evidence freshness / stale proof 主属第 6 层，是 eval、release card、safety case、post-release drift 和 release gate 之间的证据有效期边界；它不新增顶层，而是保证第 6 层证据在第 7 层决策时没有过期。

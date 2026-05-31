---
address: c-000525
type: concept
title: "Evidence Retention / Audit Packet Lifecycle 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - governance
  - evidence
  - audit
  - records-management
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
  - "[[concepts/ReleaseGateDebtBypassDetection边界]]"
sources:
  - "[[sources/nist-sp800-53-au11-audit-record-retention-2025]]"
  - "[[sources/nist-sp800-53-au3-pii-audit-record-minimization-2025]]"
  - "[[sources/nist-sp800-92r1-log-management-2023]]"
  - "[[sources/nara-general-records-schedules-2025]]"
  - "[[sources/iso-15489-records-management-2016]]"
  - "[[sources/in-toto-archivista-2026]]"
  - "[[sources/slsa-source-requirements-evidence-expunging-2026]]"
  - "[[sources/slsa-verifier-provenance-bundle-2026]]"
  - "[[sources/nist-sp800-55-measurement-guide-2024]]"
  - "[[sources/open-policy-agent-policy-testing-2026]]"
  - "[[sources/github-actions-reviewing-deployments-admin-bypass-2026]]"
  - "[[sources/gitlab-protected-environments-deployment-approvals-2026]]"
  - "[[sources/google-cloud-deploy-approvals-policies-audit-2026]]"
---

# Evidence Retention / Audit Packet Lifecycle 边界

Evidence retention / audit packet lifecycle 是第 7 层产品与组织层的证据记录治理边界：它规定 release card、eval result、signed bundle、VSA、verifier policy、trust root、safety case、monitor evidence、incident packet 和 override record 要保留多久、以什么粒度保留、如何索引检索、何时 legal hold、何时重验、何时压缩归档、何时安全销毁。

一句话：**第 6 层产出证据；第 7 层要保证几年后仍能找回、读懂、重验、解释和按政策处置这些证据。**

## 主归属

- 主归属：7. 产品与组织层
- 质量输入：6. 评估与可靠性层
- 上游输入：eval/run logs、release card、signed evidence bundle、trust-root version、safety case、incident evidence、override record、data rights/deletion/legal hold
- 下游输出：audit packet、retention class、hot/warm/cold storage、search index、reverification task、legal hold、disposition/destruction record
- 证据接口：[[concepts/EvidenceAttestationSignedEvalArtifact边界]]、[[concepts/VerifierPolicyTrustRootRotation边界]]

## 稳定链路

```text
release / eval / safety / incident decision
    -> evidence manifest: artifacts, hashes, policy versions, owners, claims, retention class
    -> packet assembly: card, eval, signed bundles, logs, monitor snapshots, approvals, rollback plan
    -> storage tiering: hot searchable, warm archived, cold immutable, legal hold
    -> retrieval and interpretation: index, schema, docs, verifier, dependency map
    -> reverify or refresh when root/policy/artifact changes
    -> disposition: expire, preserve, anonymize, tombstone, destroy, or transfer
    -> record destruction / hold / access audit
```

## Audit Packet 字段

| 字段 | 作用 |
|---|---|
| Decision id / claim id | 绑定某次 release、rollback、override、safety case 或 incident |
| Artifact manifest | model、prompt、tool、dataset、judge、container、provider、RAG index 的 digest/version |
| Evidence bundle | eval result、signed attestation、VSA、logs、monitor snapshot、release card |
| Policy context | verifier policy、trust root、threshold、risk tier、data rights、retention class |
| Owner / authority | 谁能解释、批准、legal hold、销毁或导出证据 |
| Storage tier | hot searchable、warm object store、cold archive、immutable store、air-gap export |
| Reverification hook | policy/root/provider变化后是否需要重验 |
| Disposition record | 何时销毁、保留、匿名化、legal hold、transfer 或 tombstone |

## 与相邻概念区别

- 与 [[concepts/EvidenceAttestationSignedEvalArtifact边界]]：attestation 证明证据没有被替换；retention lifecycle 保证证据长期可找回、可解释、可重验、可销毁。
- 与 [[concepts/EvidenceFreshnessStaleProof边界]]：freshness 判断证据是否仍能支持当前 claim；retention 决定即使 stale 也是否要作为历史发布依据或事故证据保留。
- 与 [[concepts/VerifierPolicyTrustRootRotation边界]]：verifier policy 判断现在是否通过；audit packet 保存当时使用的 policy/root 版本，并在 root/policy 变化后触发 reverify。
- 与 [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：release card 是证据摘要；audit packet 是可审计证据包，包含卡片背后的 run、bundle、approval、monitor 和 disposition。
- 与 [[concepts/SafetyCaseAssuranceCase边界]]：safety case 组织 claims-arguments-evidence；audit packet lifecycle 管这些 evidence 的保存、检索、legal hold 和退役。
- 与 [[concepts/AIIncidentResponsePostmortem边界]]：incident response 需要证据包止血和复盘；本页定义证据包如何长期保留并支持复发审计。
- 与 [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]：retention lifecycle 保存 override / exception / residual-risk packets；dashboard 读取这些记录来计算债务、趋势和整改动作。
- 与 [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]：retention lifecycle 保存当时的 conformance report、policy digest、root version 和 verifier engine，支持事故后重放验收语义。
- 与 [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]：retention lifecycle 决定证据保存、检索和处置；privacy-preserving packet 决定哪些字段能长期保留、哪些只能摘要化或放入 private annex。
- 与 [[concepts/ReleaseGateDebtBypassDetection边界]]：bypass detection 产生 ungated change finding、admin bypass record、stale exception 和 gate config drift 证据；retention lifecycle 决定这些 gate debt record 如何留存、检索、重验和处置。
- 与 [[concepts/DataDeletionUnlearningImpact边界]]：删除请求可能影响 logs、evidence 和 training traces；retention lifecycle 决定哪些证据可删、需保留、需匿名化或需 legal hold。

## 工程实践

1. 每次 release / rollback / override / safety review 自动生成 evidence manifest，不靠人工收集截图。
2. 分层保存：最近证据 hot searchable，长期证据 cold immutable，敏感原始日志做摘要化或加密归档。
3. 保存能重验的最小充分集：artifact digest、policy/root version、eval config、dataset split id、judge version、signed bundle、decision owner。
4. 对高风险系统定义 retention class：普通变更、重大 release、frontier safety case、incident、法律/监管 hold 分开。
5. 建立 evidence index：按 artifact digest、decision id、claim id、source data、provider、risk tier、owner 和时间检索。
6. Root/policy/provider 变化后，自动标记相关 packet 需要 reverify 或注明只能作为 historical evidence。
7. 销毁要有 disposition record：谁批准、按哪个 schedule、销毁了什么、保留了什么 tombstone。
8. Legal hold 优先于普通到期；解除 hold 后再执行原 retention/disposition 策略。

## 评估方式

- Retrieval SLA：审计者能否在规定时间内找到某次 release 的完整证据包。
- Packet completeness：release card、eval、signed bundle、policy/root、owner、monitor、approval 是否齐全。
- Reverification success：旧 evidence packet 是否能在当前或历史 verifier 环境下重验。
- Retention compliance：证据是否按风险、合同、法律和组织策略保存或销毁。
- Over-retention risk：是否保留了超过必要范围的敏感 prompt、用户数据、trace 或 eval hold-out。
- Disposition auditability：销毁、匿名化、transfer、legal hold 是否都有可审计记录。
- Incident reconstruction：事故后能否重建当时模型、prompt、context、工具、证据和发布决策。

## 过时风险

- 具体存储、归档和法规会变化，但 manifest、retention class、retrieval, legal hold, re-verification 和 disposition record 稳定。
- AI evidence 体积会膨胀；全部原始日志永久保存会带来隐私、成本和泄漏风险，因此需要最小充分证据包。
- 如果只保留 dashboard 链接和聊天结论，几年后无法重验、无法解释、也无法证明当时决策依据。

## 一句话归类

Evidence retention / audit packet lifecycle 主属第 7 层，是第 6 层证据进入组织审计、事故、监管、复盘和长期学习前的记录治理边界；它不新增顶层，而是保证证据链路不会在发布后丢失或无序膨胀。

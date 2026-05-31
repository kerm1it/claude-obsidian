---
address: c-000496
type: concept
title: "Evidence Attestation / Signed Eval Artifact 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - attestation
  - provenance
  - supply-chain
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
  - "[[concepts/ReleaseGateDebtBypassDetection边界]]"
sources:
  - "[[sources/slsa-provenance-v1-2-2026]]"
  - "[[sources/slsa-verifying-artifacts-v1-2-2026]]"
  - "[[sources/slsa-verification-summary-attestation-v1-2-2026]]"
  - "[[sources/sigstore-cosign-custom-components-trust-root-2026]]"
  - "[[sources/in-toto-test-result-predicate-2026]]"
  - "[[sources/sigstore-cosign-verifying-attestations-2026]]"
  - "[[sources/openssf-model-signing-2026]]"
  - "[[sources/nist-ssdf-sp800-218-2022]]"
  - "[[sources/attesting-llm-pipelines-release-claims-2026]]"
  - "[[sources/in-toto-archivista-2026]]"
  - "[[sources/slsa-verifier-provenance-bundle-2026]]"
  - "[[sources/sigstore-cosign-attestation-policy-cue-rego-2026]]"
  - "[[sources/ietf-rfc9901-sd-jwt-selective-disclosure-2025]]"
  - "[[sources/w3c-vc-bbs-selective-disclosure-2026]]"
  - "[[sources/google-cloud-deploy-approvals-policies-audit-2026]]"
---

# Evidence Attestation / Signed Eval Artifact 边界

Evidence attestation / signed eval artifact 是第 6 层评估与可靠性层的证据完整性边界：它把 eval result、benchmark run、judge output、release card、model snapshot、prompt、RAG index、tool/skill package、container 和 dependency 的 identity、hash、producer、run context、signature、policy verification 和 trust root 绑定起来，使第 7 层 release gate 能判断“这份证据确实来自预期流程、没有被替换或篡改”。

一句话：**lineage 说明证据从哪来；attestation 说明这份证据和它的声明能被验证。**

## 主归属

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游输入：artifact digest、eval run、test configuration、builder/evaluator identity、model/prompt/judge version、lineage、signature、policy、trust root
- 下游输出：verified / failed / unverifiable attestation、signed eval bundle、verification summary、release-card evidence、promotion gate decision
- 底座接口：[[concepts/DatasetLineageProvenanceGraph边界]]、[[concepts/EvidenceFreshnessStaleProof边界]]

## 稳定链路

```text
eval / model / prompt / judge / dataset artifact
    -> canonical digest and artifact identity
    -> attestation statement: subject, predicateType, predicate, producer/verifier, configuration, result
    -> signed envelope / bundle with signer identity and timestamp or transparency evidence
    -> verifier checks: signature, subject digest, trusted identity, policy, expected parameters, freshness
    -> decision: accept, quarantine, rerun eval, reject artifact, block release, or request re-attestation
    -> record verification summary in release card, safety case, evidence ledger, and release gate
```

## 证据对象

| 对象 | 需要绑定什么 | 常见风险 |
|---|---|---|
| Eval result | system under test、dataset split、grader、config、run id、passed/failed tests | 分数文件被替换，或不是同一候选 artifact |
| Model / adapter | weight digest、trainer identity、training run、source artifacts、model card | 权重被篡改、来源不明、hub 镜像混淆 |
| Prompt / policy | prompt hash、reviewer、policy version、release id | 发布时使用的 prompt 不是被评估版本 |
| Judge / rubric | judge model、prompt、rubric、schema、human anchor | 评分器更新后旧分数继续被信任 |
| Dataset / benchmark | sample hashes、split、access policy、leakage checks | hold-out 污染或数据替换 |
| Container / dependency | image digest、SBOM、build provenance、scan result | 运行环境与被评估环境不一致 |
| Release / safety evidence | claim id、evidence bundle、verification summary、owner | release card 引用未验证或过期证据 |

## 与相邻概念区别

- 与 [[concepts/DatasetLineageProvenanceGraph边界]]：lineage graph 记录来源、转换和下游影响；attestation 对具体 artifact 和声明做可验证签名与政策检查。
- 与 [[concepts/EvidenceFreshnessStaleProof边界]]：freshness 判断证据是否仍适用；attestation 判断证据是否确实是那份证据、由预期流程产生且未被篡改。
- 与 [[concepts/VerifierPolicyTrustRootRotation边界]]：attestation 生成 signed evidence bundle；verifier policy / trust root rotation 定义哪些身份、root、predicate、参数和时间窗口能让 bundle 被接受。
- 与 [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]：attestation 证明 artifact 和声明可验证；cross-verifier conformance test 证明不同 verifier 对同一 bundle 和 policy 的验收结果一致。
- 与 [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]：attestation 证明 evidence bundle 没被替换；retention lifecycle 保证 bundle、metadata、policy/root 版本和 verifier context 长期可找回、可解释、可重验、可销毁。
- 与 [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]：attestation 让 evidence 可验证；privacy-preserving packet 决定哪些 signed claims 可选择性披露、哪些 raw trace 要隐藏或只保留摘要。
- 与 [[concepts/ReleaseGateDebtBypassDetection边界]]：attestation 证明候选 artifact/eval bundle 可验证；gate bypass detection 发现实际生产 artifact 没有被 gate 强制要求 attestation，或 deploy path 绕过了验证点。
- 与 [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]：eval lifecycle 管测试资产；signed eval artifact 保护某次 eval run 和结果在进入 release gate 前没有被替换。
- 与 [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：release card 表达证据和局限；本页要求卡片引用可验证 evidence bundle，而不是手写分数。
- 与 [[concepts/ProductionContractCompatibilityTest边界]]：compatibility test 验证产品行为；attestation 验证测试报告、被测 artifact 和测试配置是否可被信任。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 执行行动；attestation 是 gate 消费的证据完整性检查。
- 与 generic checksum：checksum 只证明内容未变；attestation 还绑定生产者、流程、配置、policy、签名身份和验证结果。

## 工程实践

1. 每个 release gate 证据包都要有 artifact digest：model snapshot、prompt hash、judge version、eval dataset split、container image、dependency lock。
2. 将 eval result 写成可机器验证 attestation：subject 指向被测 artifact，predicate 写 result、configuration、passed/failed tests、run URL 和 evaluator identity。
3. 对模型、adapter、dataset、container 和 tool/skill package 使用签名或 Sigstore bundle；高风险系统要求 transparency log 或企业 trust root。
4. 验证不只看签名：还要检查 subject digest、signer identity、builder/evaluator identity、predicateType、expected parameters、policy digest 和 freshness。
5. Release card 只引用 verified evidence bundle；unverifiable、unknown signer、unexpected parameter 或 stale attestation 不得作为 hard gate 放行证据。
6. 对第三方 provider/model hub 记录 trust boundary：是自己验证签名、信任 hub 的 verification badge，还是要求供应商提供 attestation export。
7. 事故和回滚时保留 signed evidence bundle，支持重建“当时发布依据是什么、谁验证过、验证了哪些 artifact”。

## 评估方式

- Attestation coverage：release/eval/safety evidence 中有多少带 subject digest、签名、producer 和 verification summary。
- Verification failure rate：签名、digest、identity、policy 或 expected parameter 验证失败比例。
- Unverifiable evidence escape：未验证证据进入 release gate、safety case 或 hard stop 决策的次数。
- Artifact mismatch rate：release card 引用的 artifact 与实际部署 artifact 不一致的比例。
- Trust-root coverage：关键 builder、evaluator、model hub、provider 是否有明确 trust root 和 policy。
- Reproducible evidence audit：审查者能否从 release decision 追到 signed eval bundle、run config、logs 和 artifact hash。
- Tamper drill success：故意篡改 eval result、prompt、model 或 signature 后，gate 是否拒绝。

## 过时风险

- 具体签名工具、bundle 格式和 registry 支持会变化，但 subject digest、signed statement、trust root、policy verification 和 release gate enforcement 稳定。
- 签名证明“谁签了什么”，不证明模型安全、数据合法或 eval 充分；必须连接 data rights、lineage、freshness、judge calibration 和 metric conflict resolution。
- 过度依赖第三方 hub badge 会产生转移信任；高风险系统需要保存可导出的 bundle 和本地 verification record。

## 一句话归类

Evidence attestation / signed eval artifact 主属第 6 层，是 eval、model、prompt、judge、dataset、container 和 release evidence 进入第 7 层发布/治理决策前的证据完整性边界；它不新增顶层，而是给第 6 层证据加上可验证身份、签名和政策检查。

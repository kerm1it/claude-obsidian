---
address: c-000545
type: concept
title: "Evidence Minimization / Privacy-preserving Audit Packet 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - governance
  - privacy
  - evidence
  - audit
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
sources:
  - "[[sources/eu-gdpr-article-5-data-minimization-storage-accountability-2016]]"
  - "[[sources/nist-privacy-framework-data-minimization-audit-log-2020]]"
  - "[[sources/nist-sp800-53-au3-pii-audit-record-minimization-2025]]"
  - "[[sources/ietf-rfc9901-sd-jwt-selective-disclosure-2025]]"
  - "[[sources/w3c-vc-bbs-selective-disclosure-2026]]"
  - "[[sources/nist-sp800-53-au11-audit-record-retention-2025]]"
  - "[[sources/nist-sp800-92r1-log-management-2023]]"
  - "[[sources/slsa-source-requirements-evidence-expunging-2026]]"
---

# Evidence Minimization / Privacy-preserving Audit Packet 边界

Evidence minimization / privacy-preserving audit packet 是第 7 层产品与组织层的隐私化证据治理边界：它规定为了审计、事故、发布、合规或 safety case 可以保留和披露哪些最小证据，哪些原始用户数据、prompt、trace、secret、PII 或 hold-out 样本必须被摘要化、脱敏、加密、选择性披露、短期保留或销毁。

一句话：**audit packet 要能证明决策，不应该默认保存和暴露完整现场。**

## 主归属

- 主归属：7. 产品与组织层
- 质量输入：6. 评估与可靠性层
- 上游输入：release/eval/safety/incident/override claim、raw trace、logs、dataset sample、signed evidence、privacy risk assessment、retention policy、legal hold
- 下游输出：minimum evidence set、redacted packet、private annex、selective-disclosure proof、access policy、tombstone/disposition record
- 证据接口：[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]、[[concepts/EvidenceAttestationSignedEvalArtifact边界]]

## 稳定链路

```text
decision or audit claim
    -> purpose and evidence need statement
    -> sensitivity classification: PII, secrets, customer data, hold-out, safety-sensitive trace
    -> minimum sufficient proof set
    -> transform: digest, aggregate, redact, pseudonymize, encrypt, sample, selective disclosure, tombstone
    -> packet assembly: public body + private annex + withheld-field manifest
    -> verifier / auditor access with scope, reason, expiry, logging
    -> retention, legal hold, deletion, or disposition
```

## 稳定组件

| 组件 | 作用 |
|---|---|
| Evidence need statement | 先写明要证明哪个 claim，避免为了“以后可能有用”保留全部原始日志 |
| Field minimization matrix | 对每个字段标注 raw / redacted / derived / hashed / encrypted / withheld / short-retention |
| Private annex | 把少数必须可见的敏感证据放到更严格的访问区，而不是塞进普通 release card |
| Withheld-field manifest | 记录哪些字段被隐藏、为什么隐藏、由谁可解封、何时销毁 |
| Selective disclosure | 向审计者证明某些 claim 成立，而不展示全部 credential 或日志内容 |
| Tombstone / disposition record | 数据被删除、匿名化或 expunge 后，保留最小审计痕迹和处置原因 |

## 与相邻概念区别

- 与 [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]：retention lifecycle 问证据保存多久、放哪里、如何重验；本页问哪些字段有必要保存或披露。
- 与 [[concepts/DataRightsPrivacyConsent边界]]：data rights 管所有产品数据用途；本页只管 audit/evidence packet 这一类用途中的最小化和披露。
- 与 [[concepts/DataDeletionUnlearningImpact边界]]：deletion/unlearning 执行删除和影响面验证；本页规定删除后是否保留 tombstone、摘要、hash、disposition record 或 legal-hold annex。
- 与 [[concepts/EvidenceAttestationSignedEvalArtifact边界]]：attestation 证明证据未被替换；privacy-preserving packet 防止可验证证据过度披露。
- 与 [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]：cross-verifier test 保存一致性报告；本页要求 golden corpus、decision matrix 和 report 不泄露用户数据、secret 或私有 hold-out。
- 与“匿名化”：匿名化只是技术之一；本边界还包括目的限制、字段矩阵、访问控制、选择性披露、保留期限和处置记录。

## 工程实践

1. 对每个 audit packet 先写 evidence claim，不从 raw logs 反推要保留什么。
2. 建立字段级 minimization matrix：user content、tool input/output、trace、prompt、secret、dataset row、judge rationale 分别处理。
3. 默认长期保留 digest、artifact id、policy version、score summary、slice summary、decision owner、approval record；原始 trace 只在必要场景短期或受限保留。
4. 用 private annex 保存少量必须复核的敏感样本，并设置更严格的审批、过期、访问日志和再披露限制。
5. 对外部审计优先提供 signed summary、selective-disclosure credential、hash commitment、redacted sample 和 re-run recipe。
6. 删除或 expunging 不能静默发生：保留 tombstone、请求 id、scope、authority、time、处置类型和剩余证据位置。
7. 对 redaction pipeline 做回归测试：检查 PII、secret、tenant id、customer text、eval hold-out、prompt injection payload 是否泄漏。
8. Legal hold 可以阻止普通销毁，但不应扩大普通访问面；hold packet 也要最小化展示。

## 评估方式

- Minimality review：packet 中每类字段是否能回答明确 claim，不能回答则删除、摘要或转入 private annex。
- PII / secret leakage rate：自动扫描和人工抽检发现的泄漏比例。
- Reverification sufficiency：没有原始敏感数据时，是否仍能重验 digest、signature、policy decision、eval summary 和 release decision。
- Auditor answer rate：审计者能否在最小证据下回答 release、override、incident 或 safety claim。
- Over-retention risk：超过目的、期限或权限范围保留的原始 trace / user data / hold-out 数量。
- Access audit quality：谁看过 private annex、为什么看、是否过期、是否再披露。
- Deletion conflict handling：删除、legal hold、retention 和 audit need 冲突时是否有可审查决策记录。

## 过时风险

- 具体隐私法规、脱敏工具、选择性披露协议和密码套件会变，但 purpose binding、minimum proof set、field-level minimization、private annex、selective disclosure、tombstone 和 access audit 稳定。
- Hashing PII 不是天然匿名化；小域值、可枚举值和交叉关联会重新识别。
- 过度最小化也有风险：如果只保留结论，事故后无法证明当时证据链；因此最小化必须以可验证 claim 为单位。

## 一句话归类

Evidence minimization / privacy-preserving audit packet 主属第 7 层，是第 6 层证据进入长期审计、外部披露、事故复盘和合规记录前的隐私化证据治理边界；它不新增顶层，而是把“可审计”和“少留少披露敏感数据”合成一个可执行流程。

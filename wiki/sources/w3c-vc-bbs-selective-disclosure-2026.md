---
address: c-000551
type: source
title: "W3C Verifiable Credential BBS Cryptosuite"
source_url: https://www.w3.org/TR/vc-di-bbs/
source_type: standard
author: "W3C"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - w3c
  - verifiable-credentials
  - selective-disclosure
  - privacy
status: active
related:
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
---

# W3C Verifiable Credential BBS Cryptosuite

**来源**：W3C Verifiable Credential BBS Cryptosuite
**URL**：https://www.w3.org/TR/vc-di-bbs/

## 摘要

W3C VC Data Integrity BBS cryptosuite 规定了用 BBS signatures 保护 verifiable credentials 的方式，支持 selective disclosure 和 derived proof 场景。它适合表达“证明某些声明成立，而不展示完整凭证”的隐私需求。

## 关键贡献

- BBS derived proof 支持从原始 credential 派生只披露部分 statement 的证明。
- Unlinkability / privacy considerations 使其适合外部验证和多方审计场景。
- 对本 vault 的意义：privacy-preserving audit packet 可以把 signed evidence summary、provider claim、release claim 或 compliance claim 做成可选择性披露的凭证层，而不是直接导出全部日志。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]
- [[concepts/EvidenceAttestationSignedEvalArtifact边界]]
- [[Research: Evidence minimization privacy preserving audit packet 边界]]

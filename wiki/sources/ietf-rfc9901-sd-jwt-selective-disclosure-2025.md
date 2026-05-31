---
address: c-000550
type: source
title: "RFC 9901: Selective Disclosure for JWTs"
source_url: https://www.rfc-editor.org/rfc/rfc9901.html
source_type: standard
author: "IETF"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ietf
  - selective-disclosure
  - privacy
  - credentials
status: active
related:
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
---

# RFC 9901: Selective Disclosure for JWTs

**来源**：IETF RFC 9901
**URL**：https://www.rfc-editor.org/rfc/rfc9901.html

## 摘要

SD-JWT 定义了让 holder 选择性披露 JWT claim 的机制。Issuer 可以签发带有可披露 claim 的 token，holder 在 presentation 时只展示需要的 claim，而不暴露全部 credential 内容。

## 关键贡献

- Selective disclosure 把“验证签名 claim”与“展示完整记录”分开。
- Disclosure 可以按场景选择，减少外部审计或第三方验证时的过度披露。
- 对本 vault 的意义：AI audit packet 可把 release/eval/provider/compliance claims 做成可选择性披露的证据，而原始 trace 留在 private annex 或不出域。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]
- [[concepts/EvidenceAttestationSignedEvalArtifact边界]]
- [[Research: Evidence minimization privacy preserving audit packet 边界]]

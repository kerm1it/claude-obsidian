---
address: c-000501
type: source
title: "Sigstore Cosign verifying signatures and attestations"
source_url: https://docs.sigstore.dev/cosign/verifying/verify/
source_type: documentation
author: "Sigstore"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - sigstore
  - cosign
  - signatures
  - attestation
status: active
related:
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
---

# Sigstore Cosign verifying signatures and attestations

**来源**：Sigstore Docs
**URL**：https://docs.sigstore.dev/cosign/verifying/verify/

## 摘要

Sigstore Cosign 文档说明如何验证 container image、blob 和 attestation 的签名。它支持 keyless OIDC identity、public key、certificate chain、transparency log 和 verify-attestation 等路径。

## 关键贡献

- 支持以 certificate identity 和 OIDC issuer 验证签名者身份。
- 支持 verify-attestation，将 attestation 作为可验证供应链证据。
- 支持 transparency log verification 和不同 trust root 配置。
- 对本 vault 的意义：AI release gate 可以把 eval bundle、模型、prompt package、container 或 tool package 作为 Cosign/Sigstore 可验证 artifact。
- 对 verifier policy 的意义：验证命令必须绑定 identity、issuer、claims、certificate chain 或 trusted root，不能只看签名存在。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvidenceAttestationSignedEvalArtifact边界]]
- [[concepts/VerifierPolicyTrustRootRotation边界]]
- [[Research: Evidence attestation signed eval artifact 边界]]
- [[Research: Verifier policy trust root rotation 边界]]

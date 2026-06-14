---
address: c-000520
type: source
title: "Sigstore keyless signing root of trust"
source_url: https://docs.sigstore.dev/cosign/signing/overview/
source_type: documentation
author: "Sigstore"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - sigstore
  - keyless
  - root-of-trust
  - oidc
status: active
related:
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
---

# Sigstore keyless signing root of trust

**来源**：Sigstore Docs
**URL**：https://docs.sigstore.dev/cosign/signing/overview/

## 摘要

Sigstore keyless signing 用 OIDC identity 绑定短期 certificate，并通过 Fulcio、Rekor 和 TUF 构成 root-of-trust 链。验证者必须检查 identity、issuer、certificate chain 和 transparency evidence。

## 关键贡献

- Keyless signing 减少长期 signing key 管理，但把 verifier policy 重点转到 OIDC identity 和 issuer。
- Fulcio root CA 和 Rekor public key 是 trust root 的关键组成。
- TUF 用于分发 Sigstore root of trust。
- 对本 vault 的意义：AI artifact 签名通过不等于“任何 identity 都可信”；policy 必须限定 issuer、identity 和 root。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/VerifierPolicyTrustRootRotation边界]]
- [[Research: Verifier policy trust root rotation 边界]]

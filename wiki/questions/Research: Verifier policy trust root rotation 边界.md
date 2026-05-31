---
address: c-000517
type: research
title: "Research: Verifier policy trust root rotation 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - research
  - attestation
  - verifier-policy
  - trust-root
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
sources:
  - "[[sources/slsa-verification-summary-attestation-v1-2-2026]]"
  - "[[sources/slsa-verifying-artifacts-v1-2-2026]]"
  - "[[sources/sigstore-cosign-custom-components-trust-root-2026]]"
  - "[[sources/sigstore-keyless-root-of-trust-2026]]"
  - "[[sources/sigstore-tuf-root-update-2024]]"
  - "[[sources/tuf-root-metadata-api-2021]]"
  - "[[sources/in-toto-verify-2026]]"
  - "[[sources/sigstore-policy-controller-2026]]"
---

# Research: Verifier policy trust root rotation 边界

## 问题

第 6/7 层如何维护 verifier policy、trust root、签名身份轮换和失效处理，使 signed eval artifact 不因 root 过期、policy 漂移、client 不兼容或信任边界混乱而变成假安全感？

## 结论

Verifier policy / trust root rotation 主属第 6 层，因为它决定证据是否按当前策略通过验证；它连接第 7 层 release gate、provider governance 和 override governance。稳定职责不是“保存签名”，而是维护 expected identity、predicate、policy version、trust root set、rotation/revocation 状态和 re-verification 任务。

稳定链路是：`evidence bundle -> verifier policy -> trust material -> policy evaluation -> gate decision -> rotation/revocation/reverification`。

## 关键发现

- SLSA VSA 明确 verifier 用某个 policy 验证 artifact 和 attestation bundle，消费者还要验证 VSA 签名来自预配置 root of trust。(Source: [[sources/slsa-verification-summary-attestation-v1-2-2026]])
- SLSA verifying artifacts 把 expectations 作为 artifact 是否 authentic 的关键条件；有 provenance 但没有匹配 expectations 仍不够。(Source: [[sources/slsa-verifying-artifacts-v1-2-2026]])
- Sigstore Cosign 默认通过 TUF 分发 Fulcio、Rekor、CT log 等验证材料；自定义 root 可以用 TUF 或 trusted-root 文件分发。(Source: [[sources/sigstore-cosign-custom-components-trust-root-2026]])
- Sigstore keyless signing 把 identity 绑定到短期 certificate，并把 root of trust 中的 Fulcio CA 与 Rekor key 通过 TUF 分发。(Source: [[sources/sigstore-keyless-root-of-trust-2026]])
- Sigstore 2024 TUF root 更新说明 trust root 轮换会带来 client compatibility 风险，旧客户端可能无法加载新 root。(Source: [[sources/sigstore-tuf-root-update-2024]])
- TUF root metadata 持有 keys、roles、threshold、expires，并支持 add/remove key；这说明 root 轮换是 metadata 生命周期，不是简单替换一个 PEM 文件。(Source: [[sources/tuf-root-metadata-api-2021]])
- in-toto verify 检查 layout 签名、expiry、threshold、authorized functionary 和 artifact rules；它强调 verification workflow 不依赖外部 key 信息，说明 verifier policy 应可回放。(Source: [[sources/in-toto-verify-2026]])
- Sigstore policy-controller 展示了 policy enforcement 可以进入 admission gate，自动验证 container signatures / attestations 并支持多 key。(Source: [[sources/sigstore-policy-controller-2026]])

## 分类决策

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游：signed eval artifact、VSA、model/prompt/tool/container/dataset evidence、provider evidence export
- 下游：release card、release gate、safety case、provider governance、override review、incident/reverification task

## Open Questions

- AI release gate 中哪些 trust root 应由平台团队集中维护，哪些由产品或供应商 owner 维护？
- Root rotation 是否需要像 incident drill 一样定期演练？
- 当旧 root 被撤销时，历史 release card 是否全部重验，还是只重验仍影响生产的 evidence？

## 代表来源

- [[sources/slsa-verification-summary-attestation-v1-2-2026]]
- [[sources/slsa-verifying-artifacts-v1-2-2026]]
- [[sources/sigstore-cosign-custom-components-trust-root-2026]]
- [[sources/sigstore-keyless-root-of-trust-2026]]
- [[sources/sigstore-tuf-root-update-2024]]
- [[sources/tuf-root-metadata-api-2021]]
- [[sources/in-toto-verify-2026]]
- [[sources/sigstore-policy-controller-2026]]

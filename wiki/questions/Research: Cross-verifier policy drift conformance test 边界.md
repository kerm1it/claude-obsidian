---
address: c-000540
type: research
title: "Research: Cross-verifier policy drift conformance test 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - research
  - verifier
  - policy
  - conformance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
sources:
  - "[[sources/sigstore-policy-controller-2026]]"
  - "[[sources/slsa-verification-summary-attestation-v1-2-2026]]"
  - "[[sources/in-toto-verify-2026]]"
  - "[[sources/sigstore-cosign-attestation-policy-cue-rego-2026]]"
  - "[[sources/open-policy-agent-policy-testing-2026]]"
  - "[[sources/open-policy-agent-gatekeeper-gator-verify-2026]]"
  - "[[sources/kyverno-policy-testing-ci-2026]]"
---

# Research: Cross-verifier policy drift conformance test 边界

## 问题

当 signed eval artifact、VSA、model/package signature 和 release evidence 被 local CLI、CI、release gate、admission controller、runtime guard 或第三方 verifier 多处验证时，如何证明这些 verifier 执行的是同一套 policy，而不是各自通过不同配置、不同 trust root 或不同语义放行？

## 结论

Cross-verifier policy drift / conformance test 主属第 6 层。它不是新的签名机制，也不是 release gate 本身，而是验证“同一证据验收策略在所有执行点上的等价性”：同一 golden corpus 输入后，各 verifier 应输出一致 decision、reason code、policy digest、trust-root version 和 engine version。

稳定链路是：`canonical policy + trust root -> golden corpus -> multi-verifier run -> decision diff -> drift classification -> block/resync/rollback/override-review -> retained conformance report`。

## 关键发现

- Sigstore policy-controller 将签名和 attestation 验证放入 Kubernetes admission controller，并支持 per-namespace enforcement、multiple policies、CUE/Rego attestation policy、warn/enforce 和 remote policy 引用。(Source: [[sources/sigstore-policy-controller-2026]])
- SLSA VSA 明确 verifier 针对 artifact、attestation bundle 和 policy 产生 verification summary，说明 delegated verifier 的 identity、policy 和 result 本身也要被验收。(Source: [[sources/slsa-verification-summary-attestation-v1-2-2026]])
- in-toto verify 说明 verification 不只是签名验证，还包括 layout、expiry、threshold、authorized functionary 和 artifact rules。(Source: [[sources/in-toto-verify-2026]])
- Cosign 支持对 in-toto attestations 使用 CUE 或 Rego policy 校验，这提供了“同一 attestation policy 可被 CLI 和 admission/gate 复用”的工程接口。(Source: [[sources/sigstore-cosign-attestation-policy-cue-rego-2026]])
- OPA policy testing 提供 Rego 单元测试、数据驱动测试、JSON 输出和 fail-on-empty，可作为 policy semantic regression 的底层模式。(Source: [[sources/open-policy-agent-policy-testing-2026]])
- Gatekeeper gator verify 把 ConstraintTemplate、Constraint 和 test cases 组织成可运行 suite，用来验证 admission policy 对样本对象的预期结果。(Source: [[sources/open-policy-agent-gatekeeper-gator-verify-2026]])
- Kyverno CLI test 能在 CI 中测试 policy 行为，说明 admission policy 需要先在 pre-deployment path 中验证，再进入真实 cluster enforcement。(Source: [[sources/kyverno-policy-testing-ci-2026]])

## 分类决策

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游：signed evidence、policy package、trust root、verifier engine、release/admission/runtime configs、golden corpus
- 下游：conformance report、drift alert、release hold、admission resync、policy/root rollback、override review

## Open Questions

- AI release gate 中 canonical policy 应该用 Rego、CUE、CEL、OPA bundle、vendor policy DSL，还是先用 tool-specific policy + conformance matrix？
- 第三方 VSA verifier 的 policy detail 常常不可见时，如何设计最小可接受 delegated-verifier conformance proof？
- 高风险 AI 系统中 warn/enforce mismatch 是否应默认 hard fail，还是允许短期 canary？

## 代表来源

- [[sources/sigstore-policy-controller-2026]]
- [[sources/slsa-verification-summary-attestation-v1-2-2026]]
- [[sources/in-toto-verify-2026]]
- [[sources/sigstore-cosign-attestation-policy-cue-rego-2026]]
- [[sources/open-policy-agent-policy-testing-2026]]
- [[sources/open-policy-agent-gatekeeper-gator-verify-2026]]
- [[sources/kyverno-policy-testing-ci-2026]]

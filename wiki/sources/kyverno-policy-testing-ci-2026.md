---
address: c-000544
type: source
title: "Kyverno Testing Policies in CI"
source_url: https://main.kyverno.io/docs/guides/testing-policies/
source_type: documentation
author: "Kyverno"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - kyverno
  - policy-testing
  - ci
  - admission-control
status: active
related:
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
---

# Kyverno Testing Policies in CI

**来源**：Kyverno Docs
**URL**：https://main.kyverno.io/docs/guides/testing-policies/

## 摘要

Kyverno 文档说明 CLI test command 可以测试 policy 是否按预期运行，并可放入 CI pipeline；当新增 manifest 违反 policies 时，CI 会失败并阻止继续。

## 关键贡献

- Admission policy 可以在 CI 中提前测试，而不是只等 cluster admission 阻断。
- CI 失败能把不合规 manifest 和 policy mismatch 前移到 pull request 阶段。
- Policy tests 需要和真实 enforcement 配置保持一致，否则会出现 CI/admission drift。
- 对本 vault 的意义：cross-verifier conformance test 应同时检查 pre-deployment path 和 runtime/admission path。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]
- [[Research: Cross-verifier policy drift conformance test 边界]]

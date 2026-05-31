---
address: c-000543
type: source
title: "OPA Gatekeeper gator verify"
source_url: https://open-policy-agent.github.io/gatekeeper/website/docs/v3.10.x/gator/
source_type: documentation
author: "Open Policy Agent Gatekeeper"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - opa
  - gatekeeper
  - admission-control
  - policy-testing
status: active
related:
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
---

# OPA Gatekeeper gator verify

**来源**：OPA Gatekeeper Docs
**URL**：https://open-policy-agent.github.io/gatekeeper/website/docs/v3.10.x/gator/

## 摘要

Gatekeeper gator verify 用 Suite、Test 和 Case 组织 policy 测试：Test 声明 ConstraintTemplate、Constraint 和样本对象，Case 定义对象是否应 pass 或产生 violations。

## 关键贡献

- Admission policy 可以在进入集群前用 suite 方式测试。
- Test cases 能包含 inventory，用于测试 referential constraints。
- `gator verify` 可递归运行 suite，并按名称过滤。
- 对本 vault 的意义：release gate/admission policy 的 conformance test 需要样本对象、预期结果和 reason/violation 断言。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]
- [[Research: Cross-verifier policy drift conformance test 边界]]

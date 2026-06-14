---
address: c-000542
type: source
title: "Open Policy Agent Policy Testing"
source_url: https://www.openpolicyagent.org/docs/policy-testing
source_type: documentation
author: "Open Policy Agent"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - opa
  - rego
  - policy-testing
  - conformance
status: active
related:
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
---

# Open Policy Agent Policy Testing

**来源**：Open Policy Agent Docs
**URL**：https://www.openpolicyagent.org/docs/policy-testing

## 摘要

OPA policy testing 文档说明如何用 Rego 为 policy 写测试，使用 `opa test` 运行 `test_` 规则，并用 mock input/data、参数化测试、JSON 输出和 `--fail-on-empty` 支持 CI。

## 关键贡献

- Policy 本身需要像代码一样测试，防止规则演化时语义回归。
- 测试可以替换 input 和 data，构造特定 allow/deny 场景。
- JSON 输出和 fail-on-empty 让 policy testing 可进入自动化质量门。
- 对本 vault 的意义：verifier policy 的 conformance corpus 可以借用 OPA 测试模式，记录 expected decision 和 reason。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]
- [[Research: Cross-verifier policy drift conformance test 边界]]

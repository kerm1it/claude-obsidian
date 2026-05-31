---
address: c-000354
type: synthesis
title: "Research: Multi-provider governance 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - multi-provider-governance
status: developing
related:
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
sources:
  - "[[sources/openai-api-data-controls-2026]]"
  - "[[sources/azure-foundry-models-data-privacy-2026]]"
  - "[[sources/aws-bedrock-data-protection-2026]]"
  - "[[sources/aws-bedrock-model-invocation-logging-2026]]"
  - "[[sources/google-vertex-ai-data-governance-2026]]"
  - "[[sources/anthropic-api-data-retention-2026]]"
  - "[[sources/anthropic-api-data-residency-2026]]"
  - "[[sources/nist-ai-rmf-1-0-2023]]"
---

# Research: Multi-provider governance 边界

## Overview

本轮研究 multi-provider governance：同一个 AI 系统接多个模型、云平台和工具供应商时，如何把数据用途、保留、训练使用、地域、SLA、审计和 fallback 统一到一张控制面里。结论是：它主属第 7 层产品与组织层，不是第 3 层 model routing 的别名；routing 只在 governance 允许的 provider 集合里做成本/质量选择。

## Key Findings

- OpenAI API 文档把训练使用、abuse monitoring logs、application state 和 ZDR eligibility 分开；这说明 provider 治理不能只问“会不会训练”，还要问“会不会存、存多久、哪个 endpoint 存”。(Source: [[sources/openai-api-data-controls-2026]])
- Azure Foundry Models 文档强调 stored data 在客户 Azure tenant 的同一 geography 内保存并加密，但 batch 等功能可能有不同处理位置；多 provider policy 要按 feature 细分，而不是按 vendor 粗略批准。(Source: [[sources/azure-foundry-models-data-privacy-2026]])
- Amazon Bedrock 文档说明模型供应商不能访问 Bedrock deployment accounts、logs、customer prompts/completions；但 invocation logging 一旦启用，会把请求、响应和 metadata 交付到客户账户的 S3/CloudWatch。(Source: [[sources/aws-bedrock-data-protection-2026]], [[sources/aws-bedrock-model-invocation-logging-2026]])
- Google Vertex AI 文档说明客户数据不会在无许可下训练模型，但 zero data retention 仍要按 abuse monitoring、grounding、session resumption 和 caching 等场景分别配置。(Source: [[sources/google-vertex-ai-data-governance-2026]])
- Anthropic API 文档把 ZDR、API feature retention、第三方 integration 和 data residency 分开；第三方平台和外部工具的数据处理不自动继承 Claude API 的 ZDR 边界。(Source: [[sources/anthropic-api-data-retention-2026]], [[sources/anthropic-api-data-residency-2026]])
- NIST AI RMF 的 Govern / Map / Measure / Manage 结构说明，provider policy 应该落到 inventory、measurement、management 和 review，而不是散落在 prompt 或工程注释里。(Source: [[sources/nist-ai-rmf-1-0-2023]])

## 稳定归属

- 主归属：7. 产品与组织层
- 交叉链接：3. 推理与能力层、5. Agent 系统层、6. 评估与可靠性层
- 上游输入：data rights、risk tier、SLO、provider terms、model eval、tool permission、tenant policy
- 下游输出：provider allowlist、routing constraint、data egress policy、logging/retention rule、fallback runbook、audit trail

## 决策框架

```text
data class + purpose + user/tenant + region + risk tier
    -> provider policy matrix
    -> allowed provider/model/tool set
    -> model/tool routing
    -> trace + audit + retention + SLA monitoring
    -> incident/fallback/vendor review
```

## 策略矩阵

| 场景 | 治理要求 |
|---|---|
| 公开低风险任务 | 允许已批准 provider，重点优化 cost-quality-latency |
| 企业机密数据 | 要求 no-training、租户隔离、region、retention、DPA、审计 |
| 受监管个人数据 | 要求合规合同、删除/导出、访问控制、日志最小化 |
| 高影响 agent 动作 | provider allowlist + tool permission + human approval + full trace |
| 私有 eval / hold-out | 限制 provider、日志、训练用途，防止泄漏和 eval overfitting |
| Provider 故障或 quota | 按 policy fallback，不允许为了可用性绕过数据边界 |

## 相邻边界

- [[concepts/ModelRoutingMixture边界]]：负责选择模型；本主题负责限定候选模型和 provider。
- [[concepts/DataRightsPrivacyConsent边界]]：负责判断数据用途是否允许；本主题负责把用途落到 provider、region、retention 和 subprocessor。
- [[concepts/ToolRiskPermissioning边界]]：负责动作准入；本主题负责外部处理方准入。
- [[concepts/AISafetyOpsGovernance边界]]：负责整体风险运行系统；本主题是其中面向 vendor/provider 的控制面。

## 工程实践

1. 建 provider registry：provider、model、endpoint、region、tenant、owner、contract、DPA、subprocessor、status。
2. 建 provider policy matrix：按数据分类、用途、risk tier、region、retention、training use 和 logging 约束 provider。
3. 在 router 前执行 policy filter：先算 allowed set，再做 cost/latency/quality routing。
4. 把 logs 分层：service logs、provider abuse logs、customer-owned invocation logs、application state、audit logs。
5. 给私有 eval、训练候选和客户数据加 provider tag，防止被发往不允许的 provider。
6. 给 provider 变更建立 review：模型版本、endpoint、region、价格、条款、ZDR eligibility、incident、status。

## 评估方式

- 未授权 provider 使用率。
- 数据地域和 retention 违规率。
- Provider policy 覆盖率。
- Routing policy 是否总在 allowed set 内执行。
- Provider drift、质量回归、SLA/SLO 达成率。
- Fallback 成功率和 incident MTTR。
- Trace/audit 是否能重建每次 provider 选择。
- DPA、subprocessor、条款和模型版本复审是否按时完成。

## Contradictions

没有发现官方资料之间的直接矛盾。主要张力是：各 provider 都可能提供“不用于训练”的承诺，但 logging、application state、grounding、batch、third-party integration、customer-owned invocation logging 和 region controls 的边界不同。因此统一治理不能把 no-training 当作唯一判断条件。

## Open Questions

- 如何把 provider policy matrix 做成机器可执行 schema，并直接接入 model router / agent harness？
- 如何自动监控 provider 条款、endpoint retention、ZDR eligibility 和 region availability 的变化？
- 私有 eval 发给第三方 provider 时，如何降低 benchmark leakage 和后续训练污染风险？

## Sources

- [[sources/openai-api-data-controls-2026]]：OpenAI API data controls
- [[sources/azure-foundry-models-data-privacy-2026]]：Azure Foundry Models data privacy
- [[sources/aws-bedrock-data-protection-2026]]：Amazon Bedrock data protection
- [[sources/aws-bedrock-model-invocation-logging-2026]]：Amazon Bedrock model invocation logging
- [[sources/google-vertex-ai-data-governance-2026]]：Vertex AI data governance
- [[sources/anthropic-api-data-retention-2026]]：Anthropic API data retention
- [[sources/anthropic-api-data-residency-2026]]：Anthropic API data residency
- [[sources/nist-ai-rmf-1-0-2023]]：NIST AI RMF

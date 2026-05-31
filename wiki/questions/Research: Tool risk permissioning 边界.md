---
address: c-000325
type: synthesis
title: "Research: Tool risk permissioning 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - agents
  - tool-use
  - permissions
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
sources:
  - "[[sources/openai-agents-sdk-tool-guardrails-2026]]"
  - "[[sources/anthropic-computer-use-security-2026]]"
  - "[[sources/mcp-authorization-2025]]"
  - "[[sources/mcp-security-best-practices-2025]]"
  - "[[sources/owasp-llm-excessive-agency-2025]]"
  - "[[sources/nist-ai-agent-identity-authorization-2026]]"
  - "[[sources/aws-secure-agent-access-mcp-2026]]"
  - "[[sources/nsa-mcp-security-design-2026]]"
---

# Research: Tool risk permissioning 边界

## Overview

Tool risk / permissioning 主属第 5 层 Agent 系统层。它不是普通 prompt guardrail，而是 agent 执行动作前的准入系统：按工具风险、数据范围、凭证、审批、沙箱和审计决定是否允许行动。

## Key Findings

- OpenAI Agents SDK 的 tool guardrails 支持在每次 function-tool 调用前后检查、拒绝或中断工具执行；这说明高风险系统不能只在用户输入和最终输出做 guardrail（Source: [[sources/openai-agents-sdk-tool-guardrails-2026]]）。
- Anthropic computer use 文档把桌面控制、网络访问、敏感数据、真实后果和用户 consent 列为特殊风险，并建议专用 VM/container、域名 allowlist 和人工确认（Source: [[sources/anthropic-computer-use-security-2026]]）。
- MCP Authorization 采用 OAuth、scope、短期 token、PKCE 和 403 insufficient permissions 等模式，把 tool access 接入标准授权体系（Source: [[sources/mcp-authorization-2025]]）。
- MCP Security Best Practices 强调 progressive least-privilege scopes，避免 wildcard/full-access scope，支持按特权动作增量提权和审计（Source: [[sources/mcp-security-best-practices-2025]]）。
- OWASP LLM Top 10 的 Excessive Agency 风险指出，LLM agent 如果工具能力、权限或自主性过宽，会把 prompt injection、误解和工具组合变成真实副作用（Source: [[sources/owasp-llm-excessive-agency-2025]]）。
- NIST NCCoE 将 AI agent identity and authorization 作为 2026 年专门议题，说明企业需要区分 agent 身份、授权、委托和可审计行动（Source: [[sources/nist-ai-agent-identity-authorization-2026]]）。
- AWS Security Blog 提出 agent IAM 三原则：假设已授权权限都会被使用、通过组织策略治理角色、区分 AI-driven 与 human-initiated actions（Source: [[sources/aws-secure-agent-access-mcp-2026]]）。
- NSA 的 MCP 安全设计说明强调 MCP 带来 dynamic tool invocation、implicit trust relationships 和 context sharing 等新风险，不能只靠传统接口防护（Source: [[sources/nsa-mcp-security-design-2026]]）。

## Stable Definition

```text
model proposes action
    -> runtime classifies tool and risk
    -> policy checks identity, scope, data rights, resource, consequence
    -> approve, deny, sandbox, dry-run, or escalate
    -> execute with scoped authority
    -> audit and evaluate
```

## Boundary Rules

| 问题 | 稳定答案 |
|---|---|
| Prompt 能否当权限边界？ | 不能。Prompt 是行为提示，不是授权系统。 |
| Tool schema 是否足够？ | 不够。Schema 描述参数，不决定用户、资源和后果是否允许。 |
| 人类凭证能否直接给 agent？ | 默认不应。Agent 应有专用、短期、最小权限身份。 |
| 只读工具是否安全？ | 不一定。私有只读也可能泄露数据，必须继承 data rights。 |
| 多个低风险工具能否组合成高风险？ | 可以，所以要审计 tool chain 和跨工具数据流。 |
| 高风险动作如何上线？ | dry-run、sandbox、人审、可回滚、强审计、最小凭证。 |

## Open Questions

- 如何标准化跨供应商的 agent identity、delegation chain、tool scope 和 audit event schema。
- 如何让审批界面既低摩擦又真正显示影响，而不是让用户机械点击确认。
- 如何检测多个看似低风险工具组合后的数据外泄或权限升级路径。

## Sources

- [[sources/openai-agents-sdk-tool-guardrails-2026]]
- [[sources/anthropic-computer-use-security-2026]]
- [[sources/mcp-authorization-2025]]
- [[sources/mcp-security-best-practices-2025]]
- [[sources/owasp-llm-excessive-agency-2025]]
- [[sources/nist-ai-agent-identity-authorization-2026]]
- [[sources/aws-secure-agent-access-mcp-2026]]
- [[sources/nsa-mcp-security-design-2026]]

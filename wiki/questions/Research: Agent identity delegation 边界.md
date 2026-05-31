---
address: c-000361
type: synthesis
title: "Research: Agent identity delegation 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - agent-identity
  - delegation
status: developing
related:
  - "[[concepts/AgentIdentityDelegation边界]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
sources:
  - "[[sources/nist-ai-agent-identity-authorization-2026]]"
  - "[[sources/mcp-authorization-2025]]"
  - "[[sources/mcp-security-best-practices-2025]]"
  - "[[sources/aws-secure-agent-access-mcp-2026]]"
  - "[[sources/nsa-mcp-security-design-2026]]"
  - "[[sources/ietf-agent-identity-protocol-draft-2026]]"
---

# Research: Agent identity delegation 边界

## Overview

本轮研究 agent identity / delegation：agent 代表人、组织或其他 agent 调用工具时，系统如何表示身份、授权、委托链、权限范围和责任主体。结论是：它主属第 5 层 Agent 系统层，因为它必须进入每次 tool/action runtime；第 7 层负责授权政策、责任主体、审计和事故处理。

## Key Findings

- NIST NCCoE 2026 concept paper 明确把 software and AI agent identity and authorization 作为需要应用身份标准和最佳实践的专项问题，重点包括 identification、authorization、auditing、non-repudiation 和 prompt injection controls。(Source: [[sources/nist-ai-agent-identity-authorization-2026]])
- MCP Authorization 采用 OAuth 2.1、resource metadata、scope、audience-bound token、401/403 和 step-up authorization；这提供了 agent 工具访问的协议级身份/授权底座。(Source: [[sources/mcp-authorization-2025]])
- MCP Security Best Practices 将 token passthrough、confused deputy、session hijacking、wildcard/full-access scopes 视为核心风险，并建议 progressive least-privilege scope model。(Source: [[sources/mcp-security-best-practices-2025]])
- AWS Security Blog 说明 AI-driven actions 需要和 human-initiated actions 区分；AWS-managed MCP server 可以加 context keys，自管 MCP server 可用 STS session tags，并通过 CloudTrail 追踪 agent activity。(Source: [[sources/aws-secure-agent-access-mcp-2026]])
- NSA AISC 指出 MCP 的 dynamic tool invocation、implicit trust relationships、context sharing 和 agent misuse 是系统性风险，不能只当作接口 bug 修补。(Source: [[sources/nsa-mcp-security-design-2026]])
- IETF AIP draft 仍是 work in progress，但它准确表达了新兴方向：agent 需要可验证身份、签名动作、policy enforcement proxy 和 accountability principal。(Source: [[sources/ietf-agent-identity-protocol-draft-2026]])

## 稳定归属

- 主归属：5. Agent 系统层
- 交叉链接：6. 评估与可靠性层、7. 产品与组织层
- 上游输入：principal、任务、policy、scope、tool registry、data rights
- 下游输出：agent identity、delegation grant、scoped credential、audit trace、revocation path

## 稳定链路

```text
principal -> delegation grant -> agent/run identity
    -> scoped credential / capability
    -> tool/provider request
    -> allow / deny / step-up / approval
    -> audit / non-repudiation
    -> revoke / rotate / incident review
```

## 相邻边界

- [[concepts/ToolRiskPermissioning边界]]：基于 identity/delegation 做动作准入。
- [[concepts/DataRightsPrivacyConsent边界]]：把用户、租户、数据用途和保留边界带进 delegation。
- [[concepts/MultiProviderGovernance边界]]：provider policy 需要知道请求代表哪个组织、agent 和数据范围。
- [[concepts/AISafetyOpsGovernance边界]]：事故和例外需要 owner、audit trail 和 non-repudiation。

## 工程实践

1. 避免 agent 直接继承人类全量账号或长期 API key。
2. 给每个 agent / run / session 建可追踪 identity，并绑定 responsible principal。
3. delegation grant 带 task、scope、resource、expiry、risk tier 和 revocation path。
4. 用 OAuth/IAM/session tag/capability 等机制发短期凭证。
5. 对高风险动作做 step-up authorization 或 human approval。
6. 禁止 token passthrough；token 必须 audience-bound 且服务端校验。
7. 每次 action 写入 audit event 和 trace id。
8. 检查 general-purpose tools 是否绕过 MCP path。

## 评估方式

- 是否能重建每个工具调用的 actor、principal、grant、scope、tool、resource 和 result。
- 是否能区分 AI-driven 与 human-initiated action。
- 是否存在 wildcard / full-access / stale credential。
- step-up 是否拦住高风险动作，且不会形成无限授权弹窗。
- revocation 是否及时生效。
- prompt injection、confused deputy、token theft 和 direct-path bypass 是否被测试。

## Contradictions

没有发现直接矛盾。稳定共识是：传统 authentication/authorization 仍必要，但 agentic 系统还需要把身份、委托、scope、动态工具调用和审计连起来。未稳定的是具体标准：NIST 仍处于概念项目阶段，AIP 是 Internet-Draft，MCP 授权规范也在快速迭代。

## Open Questions

- Agent identity 应该是 per-agent、per-run、per-task，还是三者都有？
- Multi-agent delegation 如何防止权限在子 agent 间越传越宽？
- 如何把自然语言意图和机器可执行 scope 可靠对应，避免 scope 语义漂移？

## Sources

- [[sources/nist-ai-agent-identity-authorization-2026]]：NIST agent identity / authorization concept paper
- [[sources/mcp-authorization-2025]]：MCP Authorization
- [[sources/mcp-security-best-practices-2025]]：MCP Security Best Practices
- [[sources/aws-secure-agent-access-mcp-2026]]：AWS secure AI agent access patterns
- [[sources/nsa-mcp-security-design-2026]]：NSA MCP security design guidance
- [[sources/ietf-agent-identity-protocol-draft-2026]]：IETF Agent Identity Protocol draft

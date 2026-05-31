---
address: c-000333
type: source
title: "MCP Security Design Considerations for AI-Driven Automation"
source_url: https://www.nsa.gov/Press-Room/Press-Releases-Statements/Press-Release-View/Article/4496698/nsa-releases-security-design-considerations-for-ai-driven-automation-leveraging/
source_type: guidance
author: "NSA Artificial Intelligence Security Center"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - nsa
  - mcp
  - security
status: active
related:
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/AgentIdentityDelegation边界]]"
---

# MCP Security Design Considerations for AI-Driven Automation

**来源**：NSA Press Release / Cybersecurity Information Sheet
**URL**：https://www.nsa.gov/Press-Room/Press-Releases-Statements/Press-Release-View/Article/4496698/nsa-releases-security-design-considerations-for-ai-driven-automation-leveraging/

## 摘要

NSA AISC 2026 guidance 指出 MCP 在业务、金融、法律、软件开发等场景快速采用，带来 dynamic tool invocation、implicit trust relationships、context sharing、trust boundaries 和 agent misuse 等新风险。

## 关键贡献

- 说明 MCP 风险不是单个接口 bug，而是 agentic environment continuum 中的系统性边界问题。
- 强调传统认证、授权、输入验证仍必要，但不足以覆盖 agentic AI 的新风险。
- 对本 vault 的意义：tool permissioning 要作为第 5 层 runtime 和第 6/7 层治理之间的稳定接口。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：5. Agent 系统层、7. 产品与组织层

## 关联

- [[concepts/ToolRiskPermissioning边界]]
- [[concepts/AgentIdentityDelegation边界]]
- [[Research: Tool risk permissioning 边界]]

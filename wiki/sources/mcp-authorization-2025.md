---
address: c-000328
type: source
title: "MCP Authorization"
source_url: https://modelcontextprotocol.io/specification/2025-11-25/basic/authorization
source_type: specification
author: "Model Context Protocol"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - mcp
  - authorization
  - oauth
status: active
related:
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/AgentIdentityDelegation边界]]"
---

# MCP Authorization

**来源**：Model Context Protocol Specification
**URL**：https://modelcontextprotocol.io/specification/2025-11-25/basic/authorization

## 摘要

MCP Authorization 规范定义 MCP 中客户端、资源服务器和授权服务器的授权机制，使用 OAuth 2.1、scope、PKCE、短期 token、受保护资源元数据和 403 insufficient permissions 等模式。

## 关键贡献

- 把 agent tool access 纳入标准授权体系，而不是把 MCP server 当成可信本地插件。
- 强调 secure token storage、HTTPS、PKCE、scope 和权限不足错误。
- 对本 vault 的意义：tool permissioning 需要协议级身份和 scope，不只是自然语言 tool description。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/ToolRiskPermissioning边界]]
- [[concepts/AgentIdentityDelegation边界]]
- [[Research: Tool risk permissioning 边界]]

---
address: c-000329
type: source
title: "MCP Security Best Practices"
source_url: https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices
source_type: specification
author: "Model Context Protocol"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - mcp
  - security
  - least-privilege
status: active
related:
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/AgentIdentityDelegation边界]]"
---

# MCP Security Best Practices

**来源**：Model Context Protocol Documentation
**URL**：https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices

## 摘要

MCP Security Best Practices 说明 MCP implementation 的攻击面和缓解措施，特别强调 progressive least-privilege scope model、避免 wildcard/full-access scope、增量提权、日志和 token audience validation。

## 关键贡献

- 将“权限最小化”具体化为 baseline scopes、targeted elevation 和 precise scope challenge。
- 将 full-access / omnibus scopes、scope catalog 暴露和语义变更列为常见错误。
- 对本 vault 的意义：agent tool permissioning 应该按动作动态提权，而不是一开始给全量工具权限。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/ToolRiskPermissioning边界]]
- [[concepts/AgentIdentityDelegation边界]]
- [[Research: Tool risk permissioning 边界]]

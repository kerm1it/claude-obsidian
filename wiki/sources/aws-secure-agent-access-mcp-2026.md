---
address: c-000332
type: source
title: "Secure AI agent access patterns to AWS resources using MCP"
source_url: https://aws.amazon.com/blogs/security/secure-ai-agent-access-patterns-to-aws-resources-using-model-context-protocol/
source_type: engineering-blog
author: "AWS Security Blog"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - aws
  - iam
  - mcp
  - security
status: active
related:
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/AgentIdentityDelegation边界]]"
---

# Secure AI agent access patterns to AWS resources using MCP

**来源**：AWS Security Blog
**URL**：https://aws.amazon.com/blogs/security/secure-ai-agent-access-patterns-to-aws-resources-using-model-context-protocol/

## 摘要

AWS Security Blog 从 IAM 角度说明 AI agents 访问云资源时应假设已授予的权限都会被使用，并通过 least privilege、session policies、permission boundaries、SCP、session tags 和 CloudTrail 区分 agent 与人类动作。

## 关键贡献

- 三原则：假设所有权限都会被使用；用组织策略治理角色；区分 AI-driven 和 human-initiated actions。
- 明确通用 shell / bash 可能绕过 MCP path，因此要限制工具集合并约束底层 IAM。
- 对本 vault 的意义：tool permissioning 不是 UI 确认，而是身份、权限、资源和审计的系统设计。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：7. 产品与组织层、6. 评估与可靠性层

## 关联

- [[concepts/ToolRiskPermissioning边界]]
- [[concepts/AgentIdentityDelegation边界]]
- [[Research: Tool risk permissioning 边界]]

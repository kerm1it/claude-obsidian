---
address: c-000327
type: source
title: "Computer use tool security considerations"
source_url: https://docs.anthropic.com/en/docs/agents-and-tools/tool-use/computer-use-tool
source_type: documentation
author: "Anthropic"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - anthropic
  - computer-use
  - security
status: active
related:
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
---

# Computer use tool security considerations

**来源**：Anthropic Docs
**URL**：https://docs.anthropic.com/en/docs/agents-and-tools/tool-use/computer-use-tool

## 摘要

Anthropic computer use 文档说明桌面控制工具的独特风险：模型可以看屏幕、点击、输入、操作网页和应用。文档建议使用低权限 VM/container、避免敏感数据、限制互联网访问、对真实后果动作做人类确认，并告知用户风险和取得 consent。

## 关键贡献

- 将 computer use 视为比普通 API 更高风险的 tool class。
- 明确 prompt injection 会来自网页、图片等外部内容，需要隔离敏感数据和高影响动作。
- 对本 vault 的意义：R6 通用执行工具必须沙箱化，不能依赖模型自律。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：6. 评估与可靠性层、7. 产品与组织层

## 关联

- [[concepts/ToolRiskPermissioning边界]]
- [[Research: Tool risk permissioning 边界]]

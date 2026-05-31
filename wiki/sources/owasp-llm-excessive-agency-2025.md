---
address: c-000330
type: source
title: "OWASP LLM06 Excessive Agency"
source_url: https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf
source_type: framework
author: "OWASP"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - owasp
  - excessive-agency
  - security
status: active
related:
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
---

# OWASP LLM06 Excessive Agency

**来源**：OWASP Top 10 for LLM Applications v2025
**URL**：https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf

## 摘要

OWASP LLM06 Excessive Agency 将过宽工具能力、权限和自主性定义为 LLM 应用的重要风险。Agent 如果拥有过多工具、过宽权限或缺少人类确认，prompt injection 和模型误判会变成真实副作用。

## 关键贡献

- 将“工具太多、权限太宽、自主性过强”作为 agent 安全风险，而不是普通 bug。
- 支持用 allowlist、least privilege、human confirmation 和 action limits 缓解风险。
- 对本 vault 的意义：第 5 层 agent action 必须先经过 risk tier 和 permission gate。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：5. Agent 系统层、7. 产品与组织层

## 关联

- [[concepts/ToolRiskPermissioning边界]]
- [[Research: Tool risk permissioning 边界]]

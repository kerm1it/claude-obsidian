---
address: c-000220
type: source
title: "Agent Skills Specification"
source_url: https://agentskills.io/specification
source_type: specification
author: "Agent Skills"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - agent-skills
  - specification
status: active
related:
  - "[[concepts/Skill与ToolMemory边界]]"
  - "[[concepts/AgentSkillsStandard]]"
---

# Agent Skills Specification

**来源**：Agent Skills specification
**URL**：https://agentskills.io/specification

## 摘要

Agent Skills 规范定义了跨平台 skill 包格式：一个 skill 至少包含 `SKILL.md`，可选包含 `scripts/`、`references/`、`assets/`。`SKILL.md` 使用 YAML frontmatter，必需字段为 `name` 和 `description`。

## 关键贡献

- `name` 和 `description` 是最小路由接口。
- `scripts/` 承载可执行代码，`references/` 承载按需读取的长文档，`assets/` 承载模板和静态资源。
- 规范明确 progressive disclosure：metadata 常驻，完整 instructions 激活后加载，资源按需加载。
- 规范提供 validation 入口，用于检查 frontmatter 与命名约束。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：5. Agent 系统层、6. 评估与可靠性层
- 作用：把 skill 从平台功能上升为可移植包格式。

## 关联

- [[concepts/AgentSkillsStandard]]
- [[concepts/Skill与ToolMemory边界]]
- [[Research: Skill 与 tool memory workflow 边界]]

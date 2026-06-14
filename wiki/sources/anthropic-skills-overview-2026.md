---
address: c-000219
type: source
title: "Skills overview"
source_url: https://claude.com/docs/skills/overview
source_type: documentation
author: "Anthropic"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - agent-skills
  - claude
status: active
related:
  - "[[concepts/Skill与ToolMemory边界]]"
  - "[[concepts/AgentSkillsStandard]]"
---

# Skills overview

**来源**：Claude.ai Documentation
**URL**：https://claude.com/docs/skills/overview

## 摘要

Anthropic 文档把 skills 定义为 Claude 可动态加载的目录，目录包含 instructions、scripts 和 resources。每个 skill 通过 `SKILL.md` 声明何时激活以及 Claude 应遵循的 instructions。

## 关键贡献

- Skill 是目录，不只是单条 prompt。
- Skill 用 progressive disclosure 管理上下文：启动时只读 metadata，任务匹配时读完整 `SKILL.md`，需要时再读 scripts 或 references。
- 文档明确区分 skills、plugins、projects、MCP 和 custom instructions。
- Skills 可以是 Anthropic 预置、partner、组织级或用户自定义。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：5. Agent 系统层
- 作用：提供 skill 作为“按需上下文能力包”的官方定义。

## 关联

- [[concepts/Skill与ToolMemory边界]]
- [[Research: Skill 与 tool memory workflow 边界]]

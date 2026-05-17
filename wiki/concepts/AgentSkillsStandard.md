---
id: c-000114
address: c-000114
type: concept
title: "Agent Skills 标准"
aliases: ["Agent Skills Standard", "AgentSkills", "agentskills.io"]
created: 2026-05-17
tags:
  - agent-skills
  - open-standard
  - cross-platform
  - skill
status: active
---

# Agent Skills 标准（Agent Skills Standard）

**agentskills.io** 定义的开放跨平台 skill 规范。任何 AI coding agent 实现该标准后，即可共享同一套 skill 生态，无需为每个 agent 单独开发。

## 核心思路

Agent Skill = 一个目录，包含标准化的 `SKILL.md` 文件（含 frontmatter 元数据），AI agent 自动发现并按需调用。

```
my-skill/
├── SKILL.md          # 规范要求的核心文件（name、description、触发条件等）
└── references/       # 可选参考文档
```

## 已知实现

| 生态 | 来源 | 规模 |
|------|------|------|
| [[skills/scientific-agent-skills-collection\|Scientific Agent Skills]] | [[entities/KDenseAI]] | 135 skills |
| [[skills/mattpocock-collection\|mattpocock/skills]] | [[people/MattPocock]] | 18 skills |
| [[skills/claude-obsidian-collection\|claude-obsidian]] | kepano/社区 | 11 skills |

## 兼容 Agents

按 Scientific Agent Skills README 声明：
- **Cursor**
- **Claude Code**
- **Codex**（OpenAI）
- **Gemini CLI**（Google）
- 及其他实现 Agent Skills 标准的 agent

## 安装工具

```bash
# npx（跨平台通用）
npx skills add <org>/<repo>

# GitHub CLI（v2.90.0+）
gh skill install <org>/<repo>
gh skill install <org>/<repo> --agent claude-code
gh skill install <org>/<repo> --pin v1.0.0   # 版本锁定
gh skill update --all                          # 更新所有
```

## SKILL.md 规范要点

- `name`：skill 名称
- `description`：触发描述（agent 据此决定何时调用）
- `allowed-tools`（可选，Claude Code 扩展字段）：claude-obsidian 等老 skill 保留，跨平台 agent 忽略

## 与 Claude Code Skills 的关系

Claude Code 的 skills/ 目录机制是 Agent Skills 标准的 Claude Code 实现。本 vault（claude-obsidian）中的 `skills/` 即采用此格式，但已向跨平台 kepano 规范靠拢（新 skill 只需 `name` + `description`）。

## 生态意义

Agent Skills 标准的出现标志着 AI agent 工具链的**平台无关化**趋势：
- skill 开发者一次编写，所有支持标准的 agent 可用
- 用户可在不同 agent 间切换，保留 skill 投资
- 形成类似 npm 的 skill 包生态（`npx skills add ...`、`gh skill install ...`）

## 关联

- [[entities/ScientificAgentSkills]] — 最大已知 skill 集合（135 skills）
- [[people/MattPocock]] — mattpocock/skills 作者
- [[skills/_index|Skills 体系索引]] — 本 vault 的 skill 分类体系
- [[sources/scientific-agent-skills-2026-05-17|来源：Scientific Agent Skills README]]
- [[sources/mattpocock-skills-2026-05-15|来源：mattpocock/skills]]

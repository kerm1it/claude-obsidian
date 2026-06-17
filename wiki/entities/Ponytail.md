---
type: entity
address: c-000616
title: "Ponytail"
created: 2026-06-12
updated: 2026-06-12
tags:
  - agent-behavior
  - code-minimization
  - open-source
  - claude-code-plugin
status: active
related:
  - "[[people/DietrichGebert]]"
  - "[[concepts/决策阶梯]]"
  - "[[concepts/代码最小化]]"
  - "[[sources/ponytail-2026-06-12]]"
---

# Ponytail

**类型**：Agent 行为工具包  
**作者**：[[people/DietrichGebert]]  
**GitHub**：https://github.com/DietrichGebert/ponytail  
**许可**：MIT | ⭐ 26.2K | v4.7.0 (2026-06)

---

## 定位

让 AI 编码助手像"最懒的资深开发者"一样思考——系统性地优先已有方案而非编写新代码。不是一个 linter 或 dead code detector，而是一个 prompt-layer behavior constraint。

---

## 核心机制：[[concepts/决策阶梯]]

Agent 写代码前沿着 6 级阶梯攀升：YAGNI → stdlib → platform native → installed dep → one-liner → minimal implementation。

---

## 命令

| 命令 | 功能 |
|------|------|
| `/ponytail-review` | 扫描 diff 找过度工程 |
| `/ponytail-audit` | 全仓库扫描冗余 |
| `/ponytail-debt` | 收集 `ponytail:` 快捷方式分类账 |

---

## 兼容平台

Claude Code、Codex、Copilot CLI、Cursor、Windsurf、Cline、Aider、Kiro、OpenCode、Gemini CLI、Pi、OpenClaw

---

## 来源

- [[sources/ponytail-2026-06-12]]

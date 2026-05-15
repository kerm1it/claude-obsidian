---
type: index
address: c-000090
title: "Skills 体系索引"
created: 2026-05-15
updated: 2026-05-15
tags:
  - skills
  - taxonomy
  - agent-workflow
status: active
related:
  - "[[skills/mattpocock-collection]]"
  - "[[skills/claude-obsidian-collection]]"
  - "[[concepts/共享领域语言]]"
  - "[[concepts/Grilling模式]]"
---

# Skills 体系索引

跨来源的 Agent Skill 统一分类体系。随新 skill 来源摄入持续扩充。

## 来源

| 来源 | 作者 | 数量 | 定位 |
|---|---|---|---|
| [[skills/mattpocock-collection\|mattpocock/skills]] | Matt Pocock | 18（+4 deprecated） | 工程实践，反 vibe coding |
| [[skills/claude-obsidian-collection\|claude-obsidian]] | kepano / 社区 | 11 | 知识管理，wiki 体系 |

## 分类体系

### 🎯 对齐与规划（Alignment & Planning）
*解决：人与 agent 之间的需求对齐失败问题*

| Skill | 来源 | 核心功能 |
|---|---|---|
| `/grill-me` | mattpocock | 通用任务前"审讯"，穷举决策分支 |
| `/grill-with-docs` | mattpocock | 对齐 + 更新 CONTEXT.md + ADR |
| `/to-prd` | mattpocock | 对话上下文 → PRD → GitHub issue |
| `/to-issues` | mattpocock | PRD → 可独立执行的垂直切片 issues |
| `/prototype` | mattpocock | 一次性原型（终端 app / 多 UI 变体） |

### 🏗️ 代码质量与架构（Code Quality & Architecture）
*解决：代码跑不起来 / 逐渐变成泥球问题*

| Skill | 来源 | 核心功能 |
|---|---|---|
| `/tdd` | mattpocock | 红绿重构循环，按垂直切片推进 |
| `/diagnose` | mattpocock | 纪律性 debug（复现→最小化→假设→插桩→修复→回归） |
| `/zoom-out` | mattpocock | 系统视角解释陌生代码 |
| `/improve-codebase-architecture` | mattpocock | 发现深化机会，救援 ball-of-mud |

### 📚 知识管理（Knowledge Management）
*解决：跨会话知识丢失、信息孤岛问题*

| Skill | 来源 | 核心功能 |
|---|---|---|
| `/wiki` | claude-obsidian | 建立/管理持久 wiki vault |
| `/wiki-ingest` | claude-obsidian | 素材→结构化 wiki 页面 |
| `/wiki-query` | claude-obsidian | 从 wiki 回答问题，附引用 |
| `/wiki-lint` | claude-obsidian | 健康检查：孤儿页/死链/过时信息 |
| `/wiki-fold` | claude-obsidian | log 滚动归档（DragonScale Mechanism 1） |
| `/save` | claude-obsidian | 当前对话/洞察 → 结构化 wiki 页面 |
| `/autoresearch` | claude-obsidian | 自主研究循环：搜索→抓取→综合→归档 |
| `obsidian-vault` | mattpocock（personal） | Obsidian vault 的搜索/创建/管理 |

### 📝 内容与可视化（Content & Visualization）
*解决：知识呈现和导航问题*

| Skill | 来源 | 核心功能 |
|---|---|---|
| `/canvas` | claude-obsidian | 可视化层：图片/文字/PDF/wiki 页面到画布 |
| `obsidian-markdown` | claude-obsidian | Obsidian Flavored Markdown 语法 |
| `obsidian-bases` | claude-obsidian | 动态表格/视图（.base 文件） |
| `/defuddle` | claude-obsidian | 网页去噪，提取干净 markdown |

### 🤖 Agent 通信与协作（Agent Comms & Collaboration）
*解决：agent 间/会话间协作效率问题*

| Skill | 来源 | 核心功能 |
|---|---|---|
| `/caveman` | mattpocock | 超压缩通信，削减 ~75% token |
| `/handoff` | mattpocock | 压缩对话为 handoff doc 供下一 agent |
| `/triage` | mattpocock | 状态机式 issue 分类 |

### 🛠️ 项目设置与维护（Project Setup & Maintenance）
*解决：环境配置、安全防护问题*

| Skill | 来源 | 核心功能 |
|---|---|---|
| `/setup-matt-pocock-skills` | mattpocock | 每 repo 一次：issue tracker + 标签 + 文档布局 |
| `/setup-pre-commit` | mattpocock | Husky + lint-staged + Prettier + 类型检查 |
| `/git-guardrails-claude-code` | mattpocock | Hook 拦截危险 git 命令 |

### ✏️ Skill 元工具（Meta-Skills）
*关于如何创建和管理 skill 本身*

| Skill | 来源 | 核心功能 |
|---|---|---|
| `/write-a-skill` | mattpocock | 创建新 skill（结构/渐进披露/资源） |

---

## 跨来源洞察

### 共同关注：「对齐」是核心问题

多个来源独立收敛于"人机对齐是 AI 工具时代的真正瓶颈"：

- `/grill-me` / `/grill-with-docs`（Matt）→ 任务前穷举决策分支
- [[concepts/JIT规划]]（Fiona Fung）→ 只在需要时做足够的规划
- [[concepts/瓶颈转移论]]（Dario / Fiona）→ 编码不再稀缺，理解成为新稀缺

### 共同关注：「上下文」是记忆基础

| 方式 | 来源 | 内容 |
|---|---|---|
| CONTEXT.md | mattpocock | 项目领域语言文档 |
| AGENTS.md | Ryan Lopopolo / OpenAI | agent 目录，不是百科全书 |
| wiki/hot.md | claude-obsidian | 热缓存，最近上下文 |
| CLAUDE.md / MEMORY.md | Claude Code 内置 | 跨会话记忆 |
| AgentMemoryAPI | Anthropic | 文件系统式记忆 |
| claude-mem | thedotmack | 实时捕获 + 3 层 MCP 注入 |

**共同结论**：agent 需要*显式结构化的上下文*才能高质量工作。各工具在不同粒度上解决同一问题。

### 共同关注：「异步维护」是可持续性关键

- `/improve-codebase-architecture`（Matt）— 每几天运行一次
- `/wiki-lint`（claude-obsidian）— 每 10-15 次摄入后运行
- DreamCycle（GBrain）/ Dreaming（Anthropic）— 夜间自动维护
- `/wiki-fold`（claude-obsidian）— 日志滚动归档

---

## Deprecated（已废弃但有参考价值）

| Skill | 原因 | 继任 |
|---|---|---|
| `ubiquitous-language`（Matt） | 被 `grill-with-docs` 取代 | [[concepts/共享领域语言]] |
| `design-an-interface`（Matt） | 废弃 | — |
| `qa`（Matt） | 废弃 | — |
| `request-refactor-plan`（Matt） | 废弃 | — |

## In Progress（开发中）

| Skill | 方向 |
|---|---|
| `review`（Matt） | 代码 review |
| `writing-beats/fragments/shape`（Matt） | 写作辅助工具集 |

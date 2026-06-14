---
type: source
address: c-000086
title: "Skills For Real Engineers — mattpocock/skills"
source_type: github-repo
url: https://github.com/mattpocock/skills
repo: mattpocock/skills
stars: 82759
language: Shell
license: MIT
ingested_at: 2026-05-15
status: active
tags:
  - claude-code
  - skills
  - engineering-workflow
  - tdd
  - agent-workflow
related:
  - "[[people/MattPocock]]"
  - "[[concepts/共享领域语言]]"
  - "[[concepts/Grilling模式]]"
  - "[[domains/Claude-Code]]"
---

# Skills For Real Engineers — mattpocock/skills

mattpocock/skills，GitHub，⭐ 82,759，Shell，MIT

Matt Pocock（Total TypeScript 作者）发布的 Claude Code skills 合集，定位"反 vibe coding"——为真正的工程师设计，基于数十年软件工程经验。

## 核心立场

与 GSD、BMAD、Spec-Kit 的对比：
- 那些框架：拥有整个流程，夺走你的控制权，流程出 bug 难以修复
- 这些 skills：**小、可组合、可 hack、模型无关**

引用来源：Pragmatic Programmer、Domain-Driven Design、A Philosophy of Software Design、Extreme Programming Explained——软件工程经典。

## AI 辅助开发四大失败模式

### 失败模式 #1：Agent 没做我想要的 → 对齐失败

**根因**：你与 agent 之间存在沟通鸿沟。没有人能在开始之前完全说清楚自己想要什么（Pragmatic Programmer）。

**修复**：[[concepts/Grilling模式]] — 让 agent 在开始前用详细问题来"审讯"你：
- `/grill-me`：通用版，任何任务前使用
- `/grill-with-docs`：加强版，同时构建 CONTEXT.md + ADR

### 失败模式 #2：Agent 太啰嗦 → 领域术语鸿沟

**根因**：Agent 被扔进项目后需要自己摸索术语，于是用 20 个词描述 1 个词能说清楚的事。

**修复**：[[concepts/共享领域语言]]（CONTEXT.md）— 为 agent 建立项目的统一语言：
- Before："There's a problem when a lesson inside a section of a course is made 'real' (given a spot in the file system)"
- After："There's a problem with the materialization cascade"

收益：变量/函数/文件命名一致、代码库更易导航、agent 思考消耗更少 tokens。

### 失败模式 #3：代码跑不起来 → 缺乏反馈闭环

**根因**：没有反馈，agent 盲飞。

**修复**：
- `/tdd`：红绿重构循环，先写失败测试，再修 → 提供稳定反馈
- `/diagnose`：纪律性 debug 循环（复现 → 最小化 → 假设 → 插桩 → 修复 → 回归测试）

### 失败模式 #4：建出一坨泥 → 软件熵加速

**根因**：agent 极大加速编码速度，同时也极大加速软件熵——代码库以前所未有的速度变复杂。

**修复**：每一层都关注设计：
- `/to-prd`：在写 PRD 之前先问你要碰哪些模块
- `/zoom-out`：在更大系统视角下解释代码
- `/improve-codebase-architecture`：救援 ball-of-mud 代码库，建议每几天运行一次

## Skills 目录

### Engineering（日常代码工作）

| Skill | 用途 |
|---|---|
| `/grill-with-docs` | 对齐 + 构建 CONTEXT.md + 更新 ADR |
| `/tdd` | 红绿重构，按垂直切片推进 |
| `/diagnose` | 纪律性 bug/性能诊断循环 |
| `/to-prd` | 对话→PRD→GitHub issue |
| `/to-issues` | PRD→可独立执行的 GitHub issues |
| `/triage` | 状态机式问题分类 |
| `/zoom-out` | 系统级代码导览 |
| `/prototype` | 一次性原型（终端 app 或多 UI 变体） |
| `/improve-codebase-architecture` | 发现深化机会，救援泥球代码库 |
| `/setup-matt-pocock-skills` | 每个 repo 运行一次，配置 issue tracker/标签/文档布局 |

### Productivity（通用工作流）

| Skill | 用途 |
|---|---|
| `/grill-me` | 通用版 grilling，穷举所有决策分支 |
| `/caveman` | 超压缩通信模式，削减 ~75% token |
| `/handoff` | 压缩对话为 handoff 文档供另一个 agent 继续 |
| `/write-a-skill` | 创建新 skill（结构、渐进披露、资源） |

### Misc

- `/git-guardrails-claude-code`：hook 拦截危险 git 命令
- `/setup-pre-commit`：Husky + lint-staged + Prettier + 类型检查 + 测试

## 安装

```bash
npx skills@latest add mattpocock/skills
# 然后在 agent 中运行 /setup-matt-pocock-skills
```

## 关联

- [[people/MattPocock]]
- [[concepts/共享领域语言]]（CONTEXT.md 模式）
- [[concepts/Grilling模式]]
- [[domains/Claude-Code]]
- [[concepts/AI原生工程组织]]（Fiona Fung 框架，强调 AI 工具融入工程流程）
- [[concepts/代码仓库即记录系统]]（Ryan Lopopolo，仓库作为记录系统；CONTEXT.md 是另一维度的上下文注入）

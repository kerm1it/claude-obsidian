---
source_url: https://github.com/activeloopai/hivemind
fetched: 2026-06-12
source_type: github-repo
language: TypeScript
stars: ~1k
license: Apache 2.0
---

# Hivemind — One Brain for All Your Agents

**作者**: Activeloop (Y Combinator-backed, Deeplake 团队)
**NPM**: @deeplake/hivemind
**最新版本**: v0.7.89 (2026-06-11)
**提交**: 1,556 on main

## 概述

Hivemind 是一个共享记忆与技能传播系统，为编码 AI Agent 提供"团队大脑"。它从团队交互中自动学习，将能力跨会话、Agent、成员和机器传播。

核心循环四阶段：**Capture → Codify → Propagate → Compound**。

## 功能

1. **Capture**: 每个会话的 prompts、tool calls、responses 以结构化 traces 存入 Deeplake
2. **Codify**: 后台 worker 挖掘 trace 中的重复模式，转化为 SKILL.md 文件（每 20 turns 自动触发）
3. **Search**: 混合词法+语义检索（BM25 fallback）
4. **Propagation**: 实时能力共享
5. **Virtual Filesystem**: SQL-backed VFS 拦截 ~/.deeplake/memory/ 的文件操作
6. **Summaries**: 会话结束后 AI 生成 wiki 页面
7. **BYOC**: 数据可存 GCS、Azure、S3 或本地

## 支持平台

Claude Code (Marketplace 插件)、OpenClaw (原生扩展)、Codex (hooks.json)、Cursor (hooks.json 1.7+)、Hermes Agent、pi

## LoCoMo Benchmark

Hybrid retrieval, Claude Haiku: cost -25%, tokens/question -41%, turns/question -31%

## Skillify 子系统

- `hivemind skillify` — scope/team/install 管理
- 自动挖掘每 20 turns 触发
- `hivemind skillify pull` — 安装队友的 skills

## 代码库图谱

从 agent trace 构建实时代码库图谱：文件、符号、导入、agent 遍历的边。搜索走图谱而非全文匹配。

## 跨 Agent 规则系统

团队规则共享到每个 agent（SessionStart 注入）：`hivemind rules add/list/edit/done`

## Goals + KPIs

VFS 路径编码 owner/status/goal_id：~/.deeplake/memory/goal/<owner>/<status>/<uuid>.md

## 安全

TLS + AES-256 at rest；设备流登录；VFS 约 70 个允许列表内置命令；SQL 注入保护

## 数据收集

捕获：用户 prompts、tool calls (名称+完整输入)、tool responses、assistant responses、subagent 活动、codified skills。所有 workspace 成员可读。

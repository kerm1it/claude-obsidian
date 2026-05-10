---
address: c-000016
type: concept
title: "Claude Code 接入飞书"
created: 2026-05-10
updated: 2026-05-10
tags:
  - concept
  - claude-code
  - feishu
  - workflow
  - integration
status: active
---

# Claude Code 接入飞书

> [!key-insight] 核心洞察
> 将 Claude Code 作为飞书 bot，用飞书替代 terminal，获得消息持久化、富文本、多 session 管理和团队可见性。

## 背景

由 [[people/Zara]] 实践并在 2026-05-05 分享会上介绍。→ [[sources/quanchenghuifang1-2026-05-10]]

## 优势对比 terminal

| 维度 | Terminal | 飞书 |
|------|----------|------|
| 聊天记录 | 关 tab 即丢失 | 永久留存、可搜索 |
| 输出格式 | 纯文本 | 卡片、富文本、表情、图片、长图 |
| 文档 | Markdown 文件 | 飞书文档（可评论、协作） |
| Session 管理 | 手动管理 tab | 群 = project，thread = session |
| 分享 | 难 | 合并转发、@他人 |
| 多任务 | 多 tab | 多群并行 |

## 实现方式

- 通过飞书 CLI 接入 Claude Code，以 bot 形式加入飞书群
- 一个话题群对应一个 project，在 thread 中回复对应一个 session
- 文档输出自动生成飞书文档，不再是 Markdown 文件
- 支持图文混排输出（长图、流程图、卡片等）

## 相关工具

- Hyperframes（黑帧）：用 HTML 生成视频合辑的 skill
- 早鸟方案（内测中）：支持 Claude Code、Codex 等多种 agent 接入

## 关联概念

- [[concepts/HTML作为AI输出格式]]（飞书 bot 也倾向于用 HTML/富文本而非 Markdown）
- [[domains/Claude-Code]]

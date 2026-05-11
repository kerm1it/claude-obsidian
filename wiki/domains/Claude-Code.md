---
address: c-000005
type: domain
title: "Claude Code"
created: 2026-05-10
updated: 2026-05-10
tags:
  - tool
  - claude-code
  - anthropic
  - cli
status: active
---

# Claude Code

[[entities/Anthropic]] 开发的命令行 + IDE 编程助手，基于 Claude 模型系列。

## 核心特性

- 命令行界面（CLI）+ VS Code / JetBrains 插件
- 可访问文件系统、git、MCP 服务器
- 支持生成代码、文档、测试、设计原型等各类产出物

## 相关概念

- [[concepts/HTML作为AI输出格式]]：建议用 HTML 替代 Markdown 作为产出格式

## AI 原生工程实践（来自 Fiona Fung，2026-05-06）

- **新瓶颈**：验证、Code Review、安全（编码已不是瓶颈） → [[concepts/瓶颈转移论]]
- **规划**：JIT 规划（不做六个月路线图）→ [[concepts/JIT规划]]
- **技术争论**：直接生成多个 PR 对比，代码赢
- **审查策略**：Claude 负责 style/lint/bug；人类保留法务/安全/产品品位
- **团队构成**：创造性构建者 + 深度系统专家；不看重原始吞吐量
- **组织形态**：尽量扁平；管理者先做 IC（重狗粮）
- **核心原则**：全员用 Claude Code；Claudify 一切；明确许可干掉旧流程

参见 [[concepts/AI原生工程组织]]

## 关联人物

- [[people/Thariq]]（Claude Code 团队成员）
- [[people/FionaFung]]（Claude Code & Cowie 工程与产品负责人）

## 关联来源

- [[sources/twitter-2052809885763747935|HTML 的非凡效能 —— Claude Code 最佳输出格式]]
- [[sources/fiona-fung-ai-native-engineering-2026-05-11|Running an AI-native engineering org（Fiona Fung，2026-05-06）]]

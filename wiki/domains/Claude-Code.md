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

## Expanding Toolkit（来自 Lucas，2026-05-06）

核心主张：**补偿模型不可靠性的脚手架已随模型出货** → [[concepts/ExpandingToolkit]]

- **Tool Use**：模型自主选工具 + 自动重试；路由器/预过滤通常让事情更差
  - Tip：在工具描述中声明**输出 schema**（返回字段）→ 节省 harness 往返
  - Claude Code Tip：pre/post tool use hooks（`settings.json`）
- **Context Management**：1M context + server-side compaction + context editing
  - Tip：每 N 轮**清除 stale tool results** → 只保留决策，大幅省 token
  - Claude Code Tip：`/context` → 实时可视化上下文占用分布
- **Code Execution**：服务端托管沙箱，write-run-fix 循环在**单个 API turn** 内完成 → [[concepts/CodeExecution]]
  - Claude Code Tip：`/schedule` → cron 定时触发自主迭代
- **Computer Use**：Opus 4.7 原生 1440p 坐标，缩放数学消失；OSWorld 78% → [[concepts/NativeResolutionComputerUse]]
  - Claude Code Tip：Claude in Chrome（`claude.ai/chrome`）→ 操控真实浏览器会话

## 关联人物

- [[people/Thariq]]（Claude Code 团队成员）
- [[people/FionaFung]]（Claude Code & Cowie 工程与产品负责人）
- [[people/Lucas]]（Anthropic Research PM，Expanding Toolkit 演讲人）

## 关联来源

- [[sources/twitter-2052809885763747935|HTML 的非凡效能 —— Claude Code 最佳输出格式]]
- [[sources/fiona-fung-ai-native-engineering-2026-05-11|Running an AI-native engineering org（Fiona Fung，2026-05-06）]]
- [[sources/the-expanding-toolkit-2026-05-12|The Expanding Toolkit — Lucas（2026-05-06）]]

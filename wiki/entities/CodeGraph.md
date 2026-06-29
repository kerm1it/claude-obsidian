---
type: entity
title: "CodeGraph"
created: 2026-06-29
updated: 2026-06-29
address: c-000626
tags:
  - entity
  - tool
  - code-intelligence
  - knowledge-graph
related:
  - "[[people/ColbyMcHenry]]"
  - "[[entities/CodebaseMemoryMCP]]"
  - "[[entities/Hivemind]]"
  - "[[concepts/预索引代码知识图谱]]"
  - "[[concepts/代码库图谱]]"
  - "[[concepts/MCP代码智能]]"
status: active
---

# CodeGraph

**CodeGraph** 是一个预索引代码知识图谱工具，由 Colby McHenry 创建。它用 tree-sitter 解析源码 AST 并构建本地 SQLite 图数据库（节点=符号，边=调用/导入/继承关系），让 AI 编码 Agent 用一次 MCP 调用获取精确上下文，而不是逐文件 grep+read。

## 关键事实

- **GitHub**：colbymchenry/codegraph，~55.8K ⭐，MIT 协议
- **语言**：TypeScript（92.2%）
- **运行**：100% 本地，无 API Key，SQLite 存储
- **支持**：20+ 语言，17 种 Web 框架路由识别，8 种 Agent 集成
- **MCP**：`codegraph_explore` 单工具覆盖绝大多数查询

## 定位

CodeGraph 属于"代码库理解基础设施"赛道。与 [[entities/CodebaseMemoryMCP|codebase-memory-mcp]]（158 语言广度 + Hybrid LSP 深度）和 [[entities/Hivemind|Hivemind]]（运行时 trace 图谱）互补：CodeGraph 做预索引静态 AST 图谱，codebase-memory-mcp 做高性能语义搜索，Hivemind 做 Agent 团队共享记忆。

## 效果

在 7 个真实开源项目 benchmark 中（Claude Opus 4.8）：58% 更少工具调用、47% 更少 token、~16% 更便宜，文件读取几乎降为零。

---
type: source
title: "CodeGraph — 预索引代码知识图谱"
created: 2026-06-29
updated: 2026-06-29
address: c-000625
tags:
  - source
  - tool
  - code-intelligence
  - knowledge-graph
source_url: https://github.com/colbymchenry/codegraph
author: "[[people/ColbyMcHenry]]"
entity: "[[entities/CodeGraph]]"
related:
  - "[[entities/CodebaseMemoryMCP]]"
  - "[[entities/Hivemind]]"
  - "[[concepts/预索引代码知识图谱]]"
  - "[[concepts/代码库图谱]]"
  - "[[concepts/MCP代码智能]]"
fetched: 2026-06-29
status: ingested
---

# CodeGraph — 预索引代码知识图谱

CodeGraph 是一个本地优先的代码智能工具，由 Colby McHenry 开发。它用 tree-sitter 解析源码，构建预索引知识图谱（SQLite），让 AI 编码 Agent 用一次工具调用就能获取精确上下文，而不是逐文件 grep+read。

> [!key-insight] 核心命题：Agent 写代码之前，太多时间花在"找代码"上。CodeGraph 提前画好代码地图，Agent 直接查。

---

## 架构：四层管线

1. **提取（Extraction）**：tree-sitter AST 解析 → 语言专用查询提取节点（函数、类、方法）和边（调用、导入、继承）
2. **存储（Storage）**：本地 SQLite（`.codegraph/codegraph.db`）+ FTS5 全文搜索
3. **解析（Resolution）**：跨文件引用解析——函数调用→定义、导入→源文件、类继承、框架路由
4. **自动同步（Auto-Sync）**：原生 OS 文件事件（FSEvents/inotify）+ debounce 窗口，文件变化时自动重建索引

---

## 关键指标

| 维度 | 数据 |
|------|------|
| GitHub Stars | ~55.8K |
| 语言支持 | 20+ |
| 框架路由 | 17 种 Web 框架 |
| 跨文件覆盖率 | TypeScript 95.8%、Python 100%、Go 96.6%、Rust 86.7% |
| 安装方式 | Shell 脚本（无需 Node.js）或 npm |
| 运行模式 | 100% 本地，SQLite，无 API Key |
| MCP 集成 | `codegraph_explore` 单工具覆盖绝大多数查询 |

---

## Benchmark（7 个真实开源项目，Claude Opus 4.8）

| 项目 | 语言 | 文件数 | 工具调用 | Token | 成本 |
|------|------|--------|----------|-------|------|
| VS Code | TypeScript | ~10K | ↓81% | ↓64% | ↓18% |
| Django | Python | ~3K | ↓77% | ↓60% | ↓8% |
| Alamofire | Swift | ~110 | ↓58% | ↓64% | ↓40% |
| OkHttp | Java | ~645 | ↓50% | ↓54% | ↓25% |
| Tokio | Rust | ~790 | ↓57% | ↓38% | — |
| Excalidraw | TypeScript | ~640 | ↓40% | ↓25% | — |
| Gin | Go | ~110 | ↓44% | ↓23% | ↓19% |

汇总：**58% 更少工具调用 · 22% 更快 · 文件读取几乎为零 · 47% 更少 token · ~16% 更便宜**。

---

## MCP 集成

作为 MCP Server 运行，暴露单个主要工具 `codegraph_explore`——一次调用返回入口点、相关符号、调用路径和影响范围。其他工具（`codegraph_node`、`codegraph_search`、`codegraph_callers` 等）默认隐藏，可按需启用。

---

## 与同类工具对比

| | CodeGraph | [[entities/CodebaseMemoryMCP\|codebase-memory-mcp]] | [[entities/Hivemind\|Hivemind]] |
|---|---|---|---|
| 图谱类型 | 预索引静态 AST 图谱 | Tree-sitter + Hybrid LSP | 运行时 trace 图谱 |
| 存储 | SQLite | SQLite | Deeplake |
| 语言数 | 20+ | 158 | 不适用（trace-based） |
| 自动同步 | 原生文件监控 | — | Agent trace 实时 |
| 定位 | Agent 代码理解加速 | 高性能代码智能 | Agent 团队记忆传播 |

---

## 局限

- 大型仓库首次索引耗时和磁盘占用较大
- 静态分析无法捕获动态导入、反射、依赖注入
- Benchmark 数据依赖模型、prompt 和任务类型，不同场景差异大
- MCP 访问需要治理（哪些 agent、哪些仓库、`.codegraph/` 是否提交）

---

## 安装

```bash
curl -fsSL https://raw.githubusercontent.com/colbymchenry/codegraph/main/install.sh | sh
codegraph install
codegraph init
```

---

*来源：[GitHub - colbymchenry/codegraph](https://github.com/colbymchenry/codegraph)*

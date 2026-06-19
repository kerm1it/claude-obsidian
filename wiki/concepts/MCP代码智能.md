---
type: concept
address: c-000623
title: "MCP 代码智能"
created: 2026-06-19
updated: 2026-06-19
tags:
  - mcp
  - code-intelligence
  - knowledge-graph
  - agent-tool
status: active
related:
  - "[[entities/CodebaseMemoryMCP]]"
  - "[[concepts/代码库图谱]]"
  - "[[concepts/混合LSP]]"
  - "[[sources/codebase-memory-mcp-2026-06-19]]"
---

# MCP 代码智能

**来源**：[[entities/CodebaseMemoryMCP]]（DeusData，2026）  
**所属体系层**：第 4 层（上下文与知识）+ 第 5 层（Agent 系统 / MCP tool）

---

## 是什么

MCP 代码智能是一种架构模式：将代码库的结构化分析（AST、调用图、类型关系、架构拓扑）封装为 MCP 服务器，Agent 通过 MCP 工具查询结构化代码信息，而非直接逐文件读取和 grep。

---

## 与 Agent 逐文件搜索的对比

| 维度 | 逐文件搜索 | MCP 代码智能 |
|------|----------|------------|
| 数据源 | 原始文件内容 | 预建知识图谱 |
| 查询方式 | grep / Glob / Read | `search_graph`, `trace_path`, Cypher |
| Token 消耗 | 大（每文件读几百行） | 小（返回结构化结果） |
| 回答质量 | 依赖 Agent 综合 | 83%（arXiv 基准） |
| Tool calls | 多 | 少（~2.1× 减少） |
| 索引成本 | 0（无预处理） | 3 分钟（Linux 内核） |

---

## 核心洞察

1. **不嵌入 LLM**：MCP 服务器只做结构化查询，LLM 负责理解和决策
2. **一次索引，全团队复用**：图谱制品可压缩提交到仓库，队友跳过重建索引
3. **Token 节省不是压缩，是换数据源**：从逐文件读取换成图查询返回，这才是 99% 节省的本质
4. **与 Trace 图谱互补**：静态 AST 图谱回答"代码结构是什么"，trace 图谱（[[concepts/代码库图谱]]）回答"Agent 实际怎么用"

---

## 在 AI 知识体系中的位置

- **第 4 层（上下文与知识）**：MCP 代码智能是上下文工程的一种形态——用结构化代码知识替代原始文件作为 Agent 上下文
- **第 5 层（Agent 系统 / MCP tool）**：MCP 工具是 harness 层的能力扩展点

---

## 来源

- [[sources/codebase-memory-mcp-2026-06-19]]

---
type: entity
address: c-000621
title: "codebase-memory-mcp"
created: 2026-06-19
updated: 2026-06-19
tags:
  - mcp
  - code-intelligence
  - knowledge-graph
  - open-source
status: active
related:
  - "[[entities/DeusData]]"
  - "[[concepts/MCP代码智能]]"
  - "[[concepts/混合LSP]]"
  - "[[concepts/代码库图谱]]"
  - "[[sources/codebase-memory-mcp-2026-06-19]]"
---

# codebase-memory-mcp

**类型**：MCP 代码智能服务器  
**作者**：[[entities/DeusData]]  
**GitHub**：https://github.com/DeusData/codebase-memory-mcp  
**许可**：MIT | ⭐ 7.2K | v0.8.1 (2026-06)

---

## 定位

单二进制 MCP 服务器，将代码库索引为持久知识图谱。C/C++ 编写，零运行时依赖。不嵌入 LLM——由 MCP 客户端（Claude Code 等）作为智能层。

---

## 核心指标

| 指标 | 值 |
|------|-----|
| 语言支持 | 158 种（tree-sitter） |
| 语义 LSP | 10 种语言 |
| 索引速度 | Linux 内核 3 分钟 |
| Token 节省 | ~99% vs 逐文件搜索 |
| MCP 工具 | 14 个 |
| Agent 兼容 | 11 个 |
| 安全认证 | SLSA L3 + Sigstore |

---

## 两层架构

1. Tree-sitter pass（语法，158 语言）
2. Hybrid LSP pass（类型感知，10 语言）

---

## 来源

- [[sources/codebase-memory-mcp-2026-06-19]]

---
type: concept
address: c-000624
title: "Hybrid LSP"
created: 2026-06-19
updated: 2026-06-19
tags:
  - code-intelligence
  - tree-sitter
  - lsp
  - type-resolution
status: active
related:
  - "[[entities/CodebaseMemoryMCP]]"
  - "[[concepts/MCP代码智能]]"
  - "[[sources/codebase-memory-mcp-2026-06-19]]"
---

# Hybrid LSP

**来源**：[[entities/CodebaseMemoryMCP]]（DeusData，2026）  
**所属体系层**：第 4 层（上下文与知识 / 代码结构化）

---

## 是什么

Hybrid LSP 是一种两阶段代码分析架构：

1. **Tree-sitter pass**：快速语法级分析，覆盖全部 158 种语言，提取定义、调用、导入
2. **Hybrid LSP pass**：类型感知语义分析，轻量 C 实现，仅覆盖 10 种重点语言，用导入图和跨文件定义注册表细化调用边

---

## 为什么需要两阶段

```
Tree-sitter alone：快但粗糙
  → 能识别 foo() 调用 bar()
  → 但不知道 bar() 是哪个类的哪个重载

Full LSP：精确但慢
  → 需要完整类型系统、项目配置、编译
  → 对 158 种语言不可行

Hybrid LSP：两阶段折中
  → 158 种语言快速覆盖（广度）
  → 10 种重点语言语义精化（深度）
```

---

## 10 种 Hybrid LSP 语言

| 语言 | 关键能力 |
|------|---------|
| Python | imports, dataclasses, generics, SQLAlchemy, Pydantic |
| TypeScript/JS | generics, JSX components, JSDoc inference, method chaining |
| Go | cross-file registry, generics, embedded structs, interface satisfaction |
| Rust | use declarations, trait methods, generics with bounds, UFCS paths |
| Java | class hierarchies, generics, annotations, overload matching, lambdas |
| Kotlin | extension functions, scope functions, nullable unwrapping |
| C/C++ | macros, templates, namespaces, auto inference, header-source linking |
| PHP | namespaces, traits, late-static-binding, PHPDoc inference |
| C# | global usings, records, LINQ, async Task unwrap, var inference |

---

## 在 AI 知识体系中的位置

- **第 4 层（上下文与知识）**：Hybrid LSP 是代码结构化的工程手段——决定 Agent 看到什么粒度的代码关系

---

## 来源

- [[sources/codebase-memory-mcp-2026-06-19]]

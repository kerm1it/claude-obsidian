---
type: source
address: c-000620
title: "codebase-memory-mcp — 高性能代码智能 MCP 服务器"
source_url: https://github.com/DeusData/codebase-memory-mcp
created: 2026-06-19
updated: 2026-06-19
source_date: 2026-06-01
tags:
  - mcp
  - code-intelligence
  - knowledge-graph
  - tree-sitter
  - open-source
  - c
status: active
related:
  - "[[entities/CodebaseMemoryMCP]]"
  - "[[entities/DeusData]]"
  - "[[concepts/MCP代码智能]]"
  - "[[concepts/混合LSP]]"
  - "[[concepts/代码库图谱]]"
---

# codebase-memory-mcp

**来源**：[[entities/DeusData]]  
**GitHub**：https://github.com/DeusData/codebase-memory-mcp  
**许可**：MIT | **语言**：C (88.2%) | ⭐ 7.2K | v0.8.1 (2026-06)  
**862 commits**，35 releases

---

## 一句话定位

> 将任意代码库索引为持久知识图谱的单二进制 MCP 服务器——158 种语言，Linux 内核 3 分钟索引，~99% token 节省。

---

## 与 Hivemind 代码库图谱的区别

| 维度 | [[concepts/代码库图谱\|Hivemind]] | codebase-memory-mcp |
|------|------|-----|
| 数据源 | Agent trace（运行时访问路径） | 代码文件（静态 AST 分析） |
| 构建方式 | Agent 交互增量构建 | 一次性全量索引 + 后台自动同步 |
| 语言支持 | 跟随 Agent 能力 | 158 种语言（tree-sitter） |
| 语义深度 | 跟随 trace（实际调用） | Hybrid LSP（类型感知） |
| 分发方式 | 云端 Deeplake | 单二进制 + 团队共享压缩文件 |
| 集成方式 | Plugin/Hooks | MCP 协议（11 个 Agent） |

---

## 核心特性

| 特性 | 数据 |
|------|------|
| **索引速度** | Linux 内核 28M LOC / 75K 文件 → 3 分钟 |
| **Token 节省** | ~3,400 vs ~412,000（99% 减少） |
| **语言支持** | 158 种 tree-sitter 语法 |
| **MCP 工具** | 14 个：搜索、trace、架构分析、影响分析、Cypher、死代码检测 |
| **Hybrid LSP** | 10 种语言语义 type resolution |
| **可视化** | 内置 3D 图谱 (localhost:9749) |
| **团队共享** | 单压缩文件提交到 repo |
| **自动同步** | 后台 watcher 文件变更 → 自动重新索引 |
| **IaC** | Dockerfile、K8s manifests、Kustomize 作为节点 |

---

## 两层索引架构

```
Tree-sitter Pass（快速，语法级，158 语言）
  → 提取：定义、调用、导入
  → Hybrid LSP Pass（类型感知，10 语言）
    → 细化调用边：导入图 + 跨文件定义注册表
    → SQLite 知识图谱（WAL mode，ACID）
```

---

## 14 个 MCP 工具

| 类别 | 工具 |
|------|------|
| 索引 | `index_repository`, `list_projects`, `delete_project`, `index_status` |
| 查询 | `search_graph`, `trace_path`, `detect_changes`, `query_graph` (Cypher) |
| 信息 | `get_graph_schema`, `get_code_snippet`, `get_architecture`, `search_code` |
| 管理 | `manage_adr`, `ingest_traces` |

---

## Hybrid LSP 覆盖 10 种语言

Python、TypeScript/JS/JSX/TSX、PHP、C#、Go、C/C++、Java、Kotlin、Rust

每种语言有独立的类型解析模块（如 Python 的 dataclasses、SQLAlchemy、Pydantic；Go 的 cross-file registry、generics、interface satisfaction）。

---

## 图谱数据模型

**节点类型**：Project、Package、Folder、File、Module、Class、Function、Method、Interface、Enum、Type、Route、Resource

**边类型**：CONTAINS、DEFINES、IMPORTS、CALLS、HTTP_CALLS、IMPLEMENTS、HANDLES、CONFIGURES、TESTS、USES_TYPE 等，加多仓库 CROSS_* 边

**查询语言**：openCypher 子集（只读）——MATCH、WHERE、RETURN、ORDER BY、聚合等

---

## 安装

```bash
curl -fsSL https://install.codebase-memory.dev | bash
```

或通过 npm、PyPI、Homebrew、Scoop、AUR。单二进制，零运行时依赖。

---

## 安全

- 100% 本地处理，代码不离开机器
- SLSA Level 3 provenance + Sigstore cosign 签名
- VirusTotal 0/72 检测
- 零运行时依赖，所有库编译时 vendored

---

## 研究

预印本 arXiv:2603.27277。31 个仓库评估：83% 答案质量，10× 更少 token，2.1× 更少 tool calls vs 逐文件搜索。

---

## 关键洞察

1. **MCP 作为代码智能层**：不嵌入 LLM，将 MCP 客户端（Claude Code 等）作为智能层，MCP 服务器提供结构化图查询接口
2. **静态 AST + 团队共享 > Trace 图谱（在某些场景）**：一次索引全团队复用，比每人各自从 trace 构建图谱更高效
3. **Hybrid LSP = tree-sitter 广度 + 语义深度**：158 种语言全覆盖 + 10 种语言类型级精度，折中方案
4. **99% token 节省来自结构化查询**：不是压缩上下文，而是用图查询替代逐文件搜索

---

## 关联

- [[entities/CodebaseMemoryMCP]] — 实体页
- [[entities/DeusData]] — 开发公司
- [[concepts/MCP代码智能]] — MCP 代码智能概念
- [[concepts/混合LSP]] — Hybrid LSP 概念
- [[concepts/代码库图谱]] — Hivemind trace 图谱对比

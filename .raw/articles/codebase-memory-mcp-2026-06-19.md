---
source_url: https://github.com/DeusData/codebase-memory-mcp
fetched: 2026-06-19
source_type: github-repo
language: C
stars: 7.2k
license: MIT
---

# codebase-memory-mcp — 高性能代码智能 MCP 服务器

**作者**: DeusData
**GitHub**: https://github.com/DeusData/codebase-memory-mcp
**许可**: MIT | **语言**: C (88.2%) | ⭐ 7.2K | v0.8.1 (2026-06)
**提交**: 862

## 概述

一个高性能代码智能 MCP 服务器，将代码库索引为持久知识图谱。C/C++ 编写，单个静态二进制，零运行时依赖。158 种语言支持，Linux 内核（28M LOC、75K 文件）3 分钟索引完成。

## 关键特性

- **极致索引速度**：RAM-first 管道 + LZ4 压缩 + 内存 SQLite
- **158 种语言**：tree-sitter 语法编译进二进制，无需外部安装
- **Token 效率**：~3,400 tokens vs ~412,000（逐文件搜索），~99% 减少
- **14 个 MCP 工具**：搜索、trace、架构分析、影响分析、Cypher 查询、死代码检测、跨服务 HTTP 链接、ADR 管理
- **Hybrid LSP**：轻量 C 实现的类型解析，10 种语言语义级 type resolution
- **内置 3D 图谱可视化**：localhost:9749
- **团队共享图谱制品**：单个压缩文件提交到仓库，队友跳过重建索引
- **自动同步**：后台 watcher 检测文件变更自动重新索引
- **IaC 索引**：Dockerfile、Kubernetes manifests、Kustomize overlays 作为图谱节点
- **兼容 11 个 Agent**：Claude Code、Codex、Gemini CLI、Zed、OpenCode、Aider 等
- **安全**：本地处理、零运行时依赖、SLSA Level 3、Sigstore 签名

## 两层架构

1. **Tree-sitter pass**：快速语法分析，158 种语言提取定义、调用、导入
2. **Hybrid LSP pass**：类型感知，按语言分别处理，用导入图和跨文件定义注册表细化调用边

## 研究

预印本 "Codebase-Memory: Tree-Sitter-Based Knowledge Graphs for LLM Code Exploration via MCP" (arXiv:2603.27277)。31 个仓库评估：83% 答案质量，10× 更少 token，2.1× 更少 tool call。

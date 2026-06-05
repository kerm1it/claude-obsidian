---
type: entity
name: Headroom
kind: open-source-tool
org: Tejas Chopra
address: c-000596
created: 2026-06-05
tags:
  - context-compression
  - token-optimization
  - mcp
  - agent-tools
  - python
status: active
related:
  - "[[concepts/上下文压缩]]"
  - "[[concepts/上下文工程]]"
  - "[[TejasChopra]]"
---

# Headroom

AI Agent 上下文压缩层。Tejas Chopra（@chopratejas）开源，14.1K ⭐，Python+TypeScript，Apache 2.0。

## 核心能力

- **六种接入**：Library / Proxy / Agent wrap / MCP / Cross-agent memory / headroom learn
- **六种算法**：SmartCrusher（JSON）/ CodeCompressor（AST）/ Kompress-base（HF 模型）/ CacheAligner（KV cache）/ IntelligentContext（分数拟合）/ CCR（可逆）
- **效果**：Code search 92% 节省，SRE debugging 92%，issue triage 73%，codebase exploration 47%
- **准确性**：GSM8K ±0.000，TruthfulQA +0.030
- **可逆**：CCR 原文本地保存，LLM 按需取回
- **跨 Agent 记忆**：共享存储 + 自动去重

## 管线架构

11 阶段请求生命周期：Setup→Pre-Start→Post-Start→Input Received→Cached→Routed→Compressed→Remembered→Pre-Send→Post-Send→Response Received。支持 pipeline extensions、compression hooks、proxy extensions。

## Agent 兼容

Claude Code / Codex / Cursor / Aider / Copilot CLI / OpenClaw。

## headroom learn

挖掘失败 session → 提取修正 → 写回 CLAUDE.md / AGENTS.md / GEMINI.md。

## 来源

- [[sources/headroom-2026-06-05|Headroom GitHub README]]（2026-06-05）

---
type: source
address: c-000078
title: "agentmemory — AI 编码智能体持久记忆引擎"
source_type: github-repo
url: https://github.com/rohitg00/agentmemory
repo: rohitg00/agentmemory
stars: 7121
language: TypeScript
license: Apache-2.0
ingested_at: 2026-05-13
status: active
tags:
  - agent-memory
  - mcp
  - retrieval
  - knowledge-graph
related:
  - "[[entities/AgentMemory]]"
  - "[[entities/ClaudeMem]]"
  - "[[entities/GBrain]]"
  - "[[concepts/四层记忆整合]]"
  - "[[concepts/AgentMemoryAPI]]"
  - "[[concepts/混合检索RRF]]"
---

# agentmemory — AI 编码智能体持久记忆引擎

rohitg00/agentmemory，GitHub，⭐ 7,121，TypeScript，Apache 2.0

## 核心主张

"#1 Persistent memory for AI coding agents based on real-world benchmarks"

基于 [iii engine](https://github.com/iii-hq/iii) 构建。兼容 Claude Code、Cursor、Gemini CLI、Codex CLI、Hermes、OpenClaw、pi、OpenCode 及任何 MCP 客户端。

与 Karpathy LLM Wiki pattern 的关系：作者的设计文档（GitHub Gist，⭐ 1200 / Fork 172）在 Karpathy 模式基础上增加了置信评分、生命周期、知识图谱和混合检索；agentmemory 是该设计的实现。

## 关键数字

- **R@5 95.2%**（LongMemEval-S，ICLR 2025，500 题）
- **92% fewer tokens**（~170K/yr vs 19.5M+）
- **51 MCP tools**，**12 auto hooks**
- **0 external DBs**（SQLite + iii engine）
- **827 tests passing**
- Token cost/session：~1,900 tokens（≈$10/yr）

## 架构

### [[concepts/四层记忆整合]]

| 层级 | 内容 | 人脑类比 |
|------|------|---------|
| Working | 工具使用的原始观察 | 短期记忆 |
| Episodic | 压缩后的会话摘要 | "发生了什么" |
| Semantic | 提取的事实和模式 | "我知道什么" |
| Procedural | 工作流和决策模式 | "怎么做" |

记忆随时间衰减（Ebbinghaus 曲线）。频繁访问的记忆强化，过期记忆自动驱逐，矛盾自动检测并解决。

### 三流检索（BM25 + Vector + Graph，RRF 融合）

| 流 | 机制 |
|---|---|
| BM25 | 带词干扩展的关键词匹配 |
| Vector | 密集嵌入余弦相似度 |
| Graph | 知识图谱实体匹配遍历 |

Reciprocal Rank Fusion（RRF，k=60）融合，会话多样化（每会话最多 3 条）。与 [[concepts/混合检索RRF]]（GBrain）独立实现相同模式。

### 记忆 Pipeline

```
PostToolUse hook 触发
  -> SHA-256 去重（5分钟窗口）
  -> 隐私过滤（剥离 secrets/API key）
  -> 存储原始观察
  -> LLM 压缩 -> 结构化事实 + 概念 + 叙事
  -> 向量嵌入（6 个 provider + 本地）
  -> 索引进 BM25 + vector

Stop/SessionEnd hook 触发
  -> 会话摘要
  -> 知识图谱提取
  -> Slot 反思

SessionStart hook 触发
  -> 加载项目档案（top 概念/文件/模式）
  -> 混合检索（BM25+vector+graph）
  -> Token budget（默认 2000 tokens）
  -> 注入对话
```

## 与竞争对手对比

| | agentmemory | mem0 (53K⭐) | Letta/MemGPT (22K⭐) | CLAUDE.md（内置） | claude-mem (75K⭐) |
|---|---|---|---|---|---|
| R@5 | **95.2%** | 68.5% | 83.2% | N/A | ~70%（对标 BM25） |
| 自动捕获 | 12 hooks | 手动 add() | Agent 自编辑 | 手动 | 5 hooks |
| 检索 | BM25+Vector+Graph RRF | Vector+Graph | Vector | 全量加载 | 3 层 MCP 流 |
| 外部依赖 | 无（SQLite+iii） | Qdrant/pgvector | Postgres+vector | 无 | SQLite+Chroma |
| 记忆生命周期 | 4 层+衰减+自动遗忘 | 被动提取 | Agent 管理 | 手动 | 实时捕获 |
| Token/会话 | ~1,900 | 不定 | 核心记忆在 context | 22K+（240 obs） | 节省~10x |

## 关键功能

- **会话回放**：时间线滚动（prompts/tool calls/results），有播放/暂停/变速
- **JSONL 导入**：`import-jsonl` 命令，兼容已有 Claude Code 会话
- **团队记忆**：命名空间隔离，共享+私有
- **引用溯源**：任意记忆可追溯到源观察
- **Git 快照**：版本化、回滚、diff 记忆状态
- **Claude bridge**：与 MEMORY.md 双向同步
- **自愈能力**：断路器 + provider 降级链

## Ports

- `3111`：API/REST（104 endpoints）
- `3113`：实时可视化 viewer
- `3114`：iii 控制台

## iii Engine

取代 Express、SQLite+pgvector、SSE、pm2、Prometheus，用单一原语系统实现。
agentmemory 锁定 iii-engine v0.11.2（v0.11.6 引入新沙箱模型，待重构完成后解锁）。

## 关联

- [[entities/AgentMemory]]
- [[concepts/四层记忆整合]]
- [[concepts/AgentMemoryAPI]]（Anthropic 官方，与 agentmemory 互补）
- [[entities/ClaudeMem]]（claude-mem，75K⭐，更轻量）
- [[entities/GBrain]]（Garry Tan，Dream Cycle 与 4 层记忆独立收敛）
- [[concepts/混合检索RRF]]（RRF 融合检索，GBrain 和 agentmemory 独立实现）

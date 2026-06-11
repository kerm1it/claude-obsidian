---
type: entity
address: c-000030
title: "GBrain"
created: 2026-05-11
updated: 2026-05-11
tags:
  - ai-agent
  - memory
  - knowledge-graph
  - open-source
status: active
related:
  - "[[people/GarryTan]]"
  - "[[entities/YCombinator]]"
  - "[[entities/OpenClaw]]"
  - "[[concepts/CompiledTruth时间线模式]]"
  - "[[concepts/DreamCycle]]"
  - "[[concepts/Skillify]]"
  - "[[concepts/混合检索RRF]]"
  - "[[concepts/Minions任务队列]]"
  - "[[sources/gbrain-2026-05-11]]"
---

# GBrain

**类型**：开源 AI Agent 记忆管理系统  
**作者**：[[people/GarryTan]]  
**GitHub**：https://github.com/garrytan/gbrain  
**许可**：MIT | **语言**：TypeScript (98%) | ⭐ 14.6K

---

## 核心定位

> "聪明但健忘的 AI Agent 的大脑"

GBrain 为 AI Agent 提供持久的、可搜索的结构化记忆。它不是向量数据库的封装，而是一个完整的知识操作系统：摄入 → 结构化 → 混合检索 → 自动维护。

## 规模（生产）

| 指标 | 数值 |
|------|------|
| 管理页面 | 17,888 |
| 人物 | 4,383 |
| 公司 | 723 |
| 自主 cron 任务 | 21 |

## 核心机制

- **[[concepts/CompiledTruth时间线模式]]** — 所有页面 = 编译事实区 + 时间线追加区
- **[[concepts/混合检索RRF]]** — 向量 + 关键词 + RRF 融合，P@5 +31.4 pts vs. 向量 baseline
- **[[concepts/Skillify]]** — 34 个 skill，fat markdown 文档驱动，可路由
- **[[concepts/Minions任务队列]]** — 确定性后台 job queue
- **[[concepts/DreamCycle]]** — 夜间自动维护（综合、模式检测、反向链接修复）

## 技术栈

- **运行时**：Bun
- **存储**：PGLite（本地）/ Supabase（生产）
- **向量**：pgvector + HNSW
- **嵌入**：OpenAI Embeddings API

## 集成

- MCP 服务器（Claude、Cursor、Windsurf、远程 OAuth）
- 摄入：Gmail、Calendar、X/Twitter、Twilio Voice、PDF、文章

## 实际部署

- [[entities/OpenClaw]] — Garry 的 AI Agent 平台
- Hermes Agent（Nous Research）

## 同类对比

- [[entities/ClaudeMem]]（75K ⭐）：更轻量，一条命令安装；捕获工具调用级 observations；Chroma 向量检索；侧重实时会话注入。GBrain 更完整（Compiled Truth + Dream Cycle + RRF），适合重型知识库。
- [[entities/AgentMemory]]（7.1K ⭐，rohitg00）：4 层记忆整合（Working/Episodic/Semantic/Procedural）+ BM25+Vector+Graph RRF；R@5 95.2%；agentmemory 更工程化（827 tests，51 MCP tools，0 外部 DB）；GBrain 侧重知识库管理，agentmemory 侧重自动捕获和高精度检索。两者的 RRF 检索和异步记忆巩固独立收敛。
- [[entities/Hivemind]]（~1K ⭐，Activeloop，2026）：团队级 Agent 共享记忆。GBrain 是个人知识库，Hivemind 是全团队 Capture→Codify→Propagate→Compound 循环。Hivemind 的 Skillify 为全自动 trace→skill 挖掘（每 20 turns），GBrain 的 Skillify 偏人工审查固化。Hivemind 额外提供代码库图谱和跨 Agent 规则系统。

## 已知使用者

- [[people/GarryTan]] — 作者，在 OpenClaw 平台上使用
- [[people/AndrewWilkinson]]（[[entities/Tiny]] 创始人）：摄入全部会议记录 + 邮件 + Hearsay 生活录音；构建关系 CRM；驱动 family office 查询

## 来源

- [[sources/gbrain-2026-05-11]]
- [[sources/andrew-wilkinson-ai-agents-2026-05-12]] — Andrew Wilkinson 实际生产使用案例

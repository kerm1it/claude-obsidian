---
type: source
address: c-000599
title: "Hivemind — Agent 共享记忆与技能传播系统"
source_url: https://github.com/activeloopai/hivemind
created: 2026-06-12
source_date: 2026-06-11
tags:
  - agent-memory
  - skill
  - team
  - open-source
  - typescript
status: active
related:
  - "[[entities/Activeloop]]"
  - "[[entities/Hivemind]]"
  - "[[concepts/Agent共享记忆]]"
  - "[[concepts/代码库图谱]]"
  - "[[concepts/跨Agent规则系统]]"
  - "[[concepts/Skillify]]"
  - "[[entities/GBrain]]"
---

# Hivemind — One Brain for All Your Agents

**来源**：[[entities/Activeloop]]（YC-backed，Deeplake 团队）  
**GitHub**：https://github.com/activeloopai/hivemind  
**许可**：Apache 2.0 | **语言**：TypeScript (91.2%) | ⭐ ~1K | **NPM**：`@deeplake/hivemind`  
**最新版本**：v0.7.89（2026-06-11），160 个 release，1,556 次提交

---

## 一句话定位

> "One brain for all your agents" —— 为编码 AI Agent 提供团队共享记忆与自动技能传播。

---

## 核心循环：Capture → Codify → Propagate → Compound

```
每个 Agent 交互（prompt + tool call + response）
  → 结构化 trace 存入 Deeplake
  → 后台 worker 挖掘重复模式 → 编码为 SKILL.md
  → 注入所有连接的 Agent 上下文
  → 团队能力持续复合增长
```

**宣传语**："周一某工程师的 Agent 搞定了一次棘手的迁移。周二，团队每个 Agent 都能执行这个模式。"

---

## 功能矩阵

| 功能 | 说明 |
|------|------|
| **Capture** | 每个会话的 prompts、tool calls、responses 以结构化 traces 存入 Deeplake |
| **Codify** | 后台 worker 挖掘 traces 中的重复模式，转为 SKILL.md（每 20 turns 触发，可配置） |
| **Search** | 混合词法+语义检索（BM25 fallback）；可选本地 embedding daemon (nomic-embed-text-v1.5, ~600MB) |
| **Propagation** | 实时跨会话/Agent/成员/机器能力共享 |
| **VFS** | SQL-backed 虚拟文件系统拦截 `~/.deeplake/memory/` 文件操作 |
| **Summaries** | 会话结束 AI 生成 wiki 页面 |
| **BYOC** | 数据可存 GCS、Azure Blob、S3 或本地 |
| **Rules** | 跨 Agent 团队规则系统 |
| **Codebase Graph** | 从 agent trace 构建实时代码库图谱 |

---

## 支持平台

| 平台 | 集成方式 | 自动捕获 | 自动召回 |
|------|---------|---------|---------|
| Claude Code | Marketplace 插件 | ✅ | ✅ |
| OpenClaw | 原生扩展 | ✅ | ✅ |
| Codex | hooks.json | ✅ | ✅ |
| Cursor | hooks.json (1.7+) | ✅ | ✅ |
| Hermes Agent | Shell hooks + skill + MCP | ✅ | ✅ |
| pi | Extension API + skill + AGENTS.md | ✅ | ✅ |

---

## Benchmark（LoCoMo 数据集，100 QA，Claude Haiku，hybrid retrieval）

| 指标 | Baseline | Hivemind | 改善 |
|------|----------|----------|------|
| 成本/100 QA | $8.94 | $6.65 | -25% |
| Token/question | 1,700 | 1,008 | -41% |
| Turns/question | 8.9 | 6.2 | -31% |

Agent 到达答案更快，因为之前的工作被检索复用而非每次重新推导。

---

## Skillify 子系统

自动技能挖掘的核心：

- `hivemind skillify` — 查看 scope、team、install、per-project 状态
- `hivemind skillify scope <me|team>` — 设置挖掘范围
- `hivemind skillify pull` — 安装队友 skills 到本地
- `hivemind skillify unpull` — 移除
- 自动挖掘：每 20 turns（`HIVEMIND_SKILLIFY_EVERY_N_TURNS` 可配）

→ 对比 [[concepts/Skillify|GBrain Skillify]]：Hivemind 的 Skillify 是**全自动 trace→skill 挖掘**，无需人工整理 10 项合规清单；GBrain 的 Skillify 更偏向人工将一次修复升级为可路由 Skill。

---

## 代码库图谱

Hivemind 从捕获的 traces 构建实时代码库图谱：跟踪文件、符号、导入以及 Agent 在实际会话中遍历的边。搜索走图谱，查询"auth 在哪处理"返回团队 Agent 真正碰过的文件，而非所有提到 auth 的文件。

→ 详见 [[concepts/代码库图谱]]

---

## 跨 Agent 规则系统

团队规则通过 SessionStart 注入每个 Agent（Codex 除外，保持 TUI 简洁）：

```bash
hivemind rules add "no DROP TABLE on prod creds"
hivemind rules list        # 最新 10 条
hivemind rules edit <id>   # 版本号自增
hivemind rules done <id>   # 标记关闭
```

→ 详见 [[concepts/跨Agent规则系统]]

---

## Goals + KPIs

VFS 路径编码 owner/status/goal_id：

```
~/.deeplake/memory/goal/<owner>/<status>/<uuid>.md
~/.deeplake/memory/kpi/<goal_id>/<kpi-slug>.md
```

VFS-capable 运行时（Claude Code、Codex）通过 Bash heredoc 创建/编辑，`mv` 实现状态转移。

---

## 安全模型

- TLS 传输 + AES-256 静态加密
- 设备流登录（token 不出现在环境变量或代码中）
- VFS 约 70 个允许列表内置命令，未识别命令拒绝
- SQL 注入保护：`sqlStr()`, `sqlLike()`, `sqlIdent()`
- 凭证 mode `0600`，配置目录 `0700`
- Org/workspace 边界在存储层强制

---

## 同类对比

| 系统 | 定位 | 差异化 |
|------|------|--------|
| [[entities/GBrain]] | 个人 AI Agent 记忆管理 | GBrain 侧重个人知识库（Compiled Truth + Dream Cycle + RRF）；Hivemind 侧重**团队共享**能力传播（Capture→Codify→Propagate） |
| [[entities/ClaudeMem]] | 跨会话持久记忆 | ClaudeMem 轻薄单机（SQLite+Chroma）；Hivemind 云端+BYOC、团队级、自动 skill 挖掘 |
| [[entities/AgentMemory]] | 4 层记忆引擎 | AgentMemory 侧重记忆类型的工程化（827 tests）；Hivemind 侧重 traces 到 skills 的传播管道 |

---

## 关键洞察

1. **共享记忆即共享能力**：Hivemind 的核心理念——"shared capability intentionally requires shared substrate"——所有 workspace 成员可读 traces，因为能力传播依赖共享的数据基础
2. **匿名技能传播**：一个 Agent 的发现自动变成全团队的技能，不需要主动分享或文档化
3. **代码库图谱 = 活的代码地图**：图谱不是静态 AST 分析，而是 Agent 实际交互路径的沉淀
4. **第 5 层 + 第 8 层的组合**：Hivemind 跨越 Agent 系统（第 5 层，harness/tool/trace）和自我改进（第 8 层，dream/feedback→skill），是这两个 AI 知识体系层级的工程实现

---

## 关联

- [[entities/Activeloop]] — 开发公司
- [[entities/Hivemind]] — 产品实体页
- [[concepts/Agent共享记忆]] — 共享记忆核心概念
- [[concepts/代码库图谱]] — 代码库图谱概念
- [[concepts/跨Agent规则系统]] — 跨 Agent 规则
- [[concepts/Skillify]] — GBrain Skillify 对比
- [[entities/GBrain]] — 同类系统

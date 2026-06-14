---
type: entity
address: c-000601
title: "Hivemind"
created: 2026-06-12
updated: 2026-06-12
tags:
  - agent-memory
  - skill
  - team
  - open-source
  - npm-package
status: active
related:
  - "[[entities/Activeloop]]"
  - "[[concepts/Agent共享记忆]]"
  - "[[concepts/Skillify]]"
  - "[[concepts/代码库图谱]]"
  - "[[concepts/跨Agent规则系统]]"
  - "[[entities/GBrain]]"
  - "[[sources/activeloopai-hivemind-2026-06-12]]"
---

# Hivemind

**类型**：Agent 共享记忆与技能传播系统  
**作者**：[[entities/Activeloop]]  
**GitHub**：https://github.com/activeloopai/hivemind  
**许可**：Apache 2.0 | **语言**：TypeScript (91.2%) | ⭐ ~1K  
**NPM**：`@deeplake/hivemind`  
**最新版本**：v0.7.89（2026-06-11）

---

## 定位

> "One brain for all your agents"

Hivemind 让编码 AI Agent 团队共享记忆和自动传播技能。一个 Agent 的发现自动成为全团队的能力。

---

## 核心循环

```
Capture（捕获每个 trace）
  → Codify（挖掘模式 → SKILL.md）
    → Propagate（注入所有 Agent 上下文）
      → Compound（团队能力持续增长）
```

---

## 关键能力

| 能力 | 说明 |
|------|------|
| **自动捕获** | 每个会话的 prompts、tool calls、responses 结构化存储 |
| **自动技能挖掘** | 每 20 turns 从 traces 挖掘重复模式生成 SKILL.md |
| **混合检索** | 词法 + 语义（BM25 fallback），可选本地 embedding |
| **代码库图谱** | 从 agent trace 构建实时代码结构图 |
| **跨 Agent 规则** | 团队规则 SessionStart 注入所有 Agent |
| **VFS** | SQL-backed 虚拟文件系统管理记忆文件 |
| **BYOC** | GCS/Azure/S3/本地部署 |

---

## 支持 Agent 平台

Claude Code、OpenClaw、Codex、Cursor、Hermes Agent、pi

---

## 安装

```bash
npm install -g @deeplake/hivemind && hivemind install
```

---

## 同类对比

- [[entities/GBrain]]：个人知识库，侧重 Compiled Truth + Dream Cycle；Hivemind 侧重团队共享 + 自动 skill 传播
- [[entities/ClaudeMem]]：轻薄单机记忆；Hivemind 云端+团队级
- [[entities/AgentMemory]]：4 层记忆工程化；Hivemind 侧重 trace→skill 管道

---

## 来源

- [[sources/activeloopai-hivemind-2026-06-12]]

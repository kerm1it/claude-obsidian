---
type: concept
address: c-000046
title: "Anthropic Agent Memory API"
created: 2026-05-11
updated: 2026-05-11
tags:
  - agent-memory
  - managed-agents
  - anthropic
  - api
status: active
related:
  - "[[concepts/AnthropicDreaming]]"
  - "[[concepts/乐观并发]]"
  - "[[sources/memory-dreaming-self-learning-agents-2026-05-11]]"
---

# Anthropic Agent Memory API

**发布时间**：2026-04（公测，Managed Agents API）  
**产品形态**：Managed Agents API 的一部分，同时提供独立 API  
**来源**：[[sources/memory-dreaming-self-learning-agents-2026-05-11]]

---

## 核心设计：文件系统式记忆

Anthropic 将 Agent 记忆建模为**文件系统**：一组有层级结构的文件，由 Claude 自主用 Bash 和 Grep 工具管理。

> "Memory in Cloud Managed Agents models memory as a file system to Claude — a series of files with a specific hierarchy and format that Claude can manage and update on its own."

**演进路径**：
```
CLAUDE.md（早期，手动，受限）
    → Memory Tool（SDK，结构化 tool call）
    → 文件系统式记忆（当前，自主管理，无过度约束）
```

**设计哲学**：随模型能力提升，逐渐减少约束，将更多决策权交给 Claude。  
**Claude Opus 4.7** 在文件系统式记忆 benchmark 上达到 SOTA。

---

## 核心特性

### 权限作用域（Permission Scopes）
同一 Agent 可对不同 memory store 持有不同权限：
- **只读**：组织级知识库（runbook、SLO 指南、联系人）——不允许 Agent 随意修改
- **读写**：工作记忆（当前任务状态、发现、短期学习）

### 乐观并发（Optimistic Concurrency）
多 Agent 并发写同一 memory store 时：
- 写入时携带 **content hash**（precondition hash）
- 若 hash 不匹配（已被其他 Agent 更新），写入拒绝
- 防止并发覆盖，不需要全局锁

→ 详见 [[concepts/乐观并发]]

### 版本历史（Version History）
每次 memory 更新都记录完整 audit log：
- 变更内容（diff）
- 执行 Agent 标识
- Session ID
- 时间戳

开发者可回溯任意历史版本；Agent 未来也可读取 audit log。

### 独立 API
- memory store 可在 Managed Agents 之外单独访问
- 支持用例：PII 扫描、外部系统同步、自定义清理流水线

---

## 三层记忆架构

```
┌─────────────────────────────────────────────┐
│  过程层（Process Layer）                      │
│  → Dreaming：离线批处理，跨 Agent 模式提取    │
├─────────────────────────────────────────────┤
│  结构/内容层（Structure Layer）               │
│  → 文件系统模型；Skills 式程序化记忆           │
├─────────────────────────────────────────────┤
│  存储层（Storage Layer）                      │
│  → 数据位置；归因元数据；版本历史              │
└─────────────────────────────────────────────┘
```

---

## 多 Agent 场景

当前 Anthropic 内部已有**数百至数千个并发 Agent** 共享同一 memory store：
- 共享状态 = 事实上的大型知识库，而非简单工作上下文
- 要求 memory 系统支持高并发、高可靠、可审计
- Dreaming 是为这一规模设计的过程层

---

## 配套产品

- [[concepts/AnthropicDreaming]] — 离线批处理记忆优化

---

## 关联

- [[concepts/DreamCycle]] — GBrain 的同构开源实现
- [[entities/GBrain]] — 开源 Agent 记忆管理系统
- [[concepts/乐观并发]] — 并发写保护

---
type: concept
address: c-000602
title: "Agent 共享记忆"
created: 2026-06-12
updated: 2026-06-12
tags:
  - agent-memory
  - team
  - skill-propagation
  - shared-substrate
status: active
related:
  - "[[entities/Hivemind]]"
  - "[[concepts/Skillify]]"
  - "[[concepts/AgentMemoryAPI]]"
  - "[[entities/GBrain]]"
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[sources/activeloopai-hivemind-2026-06-12]]"
---

# Agent 共享记忆

**来源**：[[entities/Hivemind]]（Activeloop，2026）  
**所属体系层**：第 4 层（上下文与知识）+ 第 5 层（Agent 系统）+ 第 8 层（自我改进）

---

## 是什么

Agent 共享记忆是一种团队级记忆架构：多个 Agent 的交互 traces 存入**共享存储层**，从中自动挖掘可复用模式（SKILL.md），再将能力传播回所有连接的 Agent。

核心设计原则：**共享能力必须有共享数据基础**（"shared capability intentionally requires shared substrate"）。

---

## 与单 Agent 记忆的区别

| 维度 | 单 Agent 记忆 | Agent 共享记忆 |
|------|-------------|--------------|
| 范围 | 一个 Agent 的历史 | 团队所有 Agent 的交互 |
| 写入者 | 单个 Agent | 团队所有 Agent |
| 读权限 | 仅自己或指定 scope | 全 workspace 成员可读 |
| 衍生能力 | 个人经验积累 | 自动技能传播 |
| 存储 | 本地文件/向量库 | 云端 Deeplake/BYOC |
| 典型系统 | [[concepts/AgentMemoryAPI]], [[entities/GBrain]] | [[entities/Hivemind]] |

---

## 稳定链路

```
每个 Agent session（prompt + tool call + response）
  → 结构化 trace 存入共享存储
  → 后台 worker 挖掘重复模式
  → 编码为 SKILL.md 文件
  → 注入所有连接 Agent 的上下文（SessionStart / 按需加载）
  → 团队能力复合增长
  → 新一轮 traces 验证 skills 有效性
```

---

## 关键设计决策

1. **全透明 vs 隐私**：Hivemind 选择"全 workspace 可读"，因为能力传播的前提是共享数据
2. **自动挖掘 vs 人工整理**：Hivemind 每 20 turns 自动触发挖掘，无需人工审查；GBrain Skillify 需要 10 项合规清单
3. **云端 vs 本地**：Hivemind 默认 Deeplake 云存储，支持 BYOC 本地部署
4. **VFS 接口**：文件系统式 API（与 Anthropic Memory API 设计哲学一致），降低 Agent 接入门槛

---

## 在 AI 知识体系中的位置

- **第 4 层（上下文与知识）**：共享记忆是上下文工程的一种形态——从个人上下文扩展到团队上下文
- **第 5 层（Agent 系统）**：harness 需要集成共享记忆的读写接口；tool registry 需要注册 skill 发现和加载
- **第 8 层（自我改进）**：自动 trace→skill 是 self-improvement 的一种工程实现（L1：改 memory/knowledge；L2：改 skill/context）

---

## 关联

- [[entities/Hivemind]] — 代表性实现
- [[concepts/AgentMemoryAPI]] — Anthropic 单 Agent 记忆 API（文件系统式）
- [[concepts/Skillify]] — GBrain 的 skill 固化模式（人工驱动 vs 自动挖掘）
- [[entities/GBrain]] — 个人级 Agent 记忆管理
- [[concepts/Dream与SelfImprovement工程原语]] — self-improvement 工程原语

---
type: concept
address: c-000033
title: "Compiled Truth + Timeline 模式"
created: 2026-05-11
updated: 2026-05-11
tags:
  - agent-memory
  - knowledge-structure
  - pattern
status: active
related:
  - "[[entities/GBrain]]"
  - "[[sources/gbrain-2026-05-11]]"
---

# Compiled Truth + Timeline 模式

**来源**：[[entities/GBrain]] by [[people/GarryTan]]  
**用途**：Agent 记忆页面的双区结构设计

---

## 核心思想

每个知识页面分为两个区域：

| 区域 | 性质 | 写入策略 |
|------|------|----------|
| **Compiled Truth**（编译事实） | 稳定事实 | 最后一次写入覆盖（last-write-wins） |
| **Timeline**（时间线） | 事件记录 | 仅追加（append-only） |

Agent 读取时：优先读编译事实区获取快速上下文；新事件写入时间线区不覆盖历史。

## 为什么这样设计

- **避免幻觉覆写**：新信息不直接覆盖旧事实，时间线保留完整历史
- **读取效率**：编译区是高密度摘要，Agent 无需遍历所有历史
- **可追溯**：时间线区支持溯源，知道某个事实是何时、从何处得出的

## 与 GBrain 的关系

GBrain 中所有实体页面（人物、公司、事件）均遵循此模式。[[concepts/DreamCycle|Dream Cycle]] 夜间维护会定期从时间线区"蒸馏"新的编译事实，保持编译区的准确性。

## 类比

类似于数据库的 **CQRS 模式**（命令查询职责分离）：写入走时间线（命令侧），读取走编译区（查询侧）。

## 关联概念

- [[concepts/DreamCycle]] — 夜间将时间线蒸馏回编译区
- [[entities/GBrain]] — 实现该模式的系统

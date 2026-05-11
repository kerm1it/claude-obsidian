---
type: concept
address: c-000037
title: "Minions 任务队列"
created: 2026-05-11
updated: 2026-05-11
tags:
  - agent-design
  - background-jobs
  - queue
status: active
related:
  - "[[entities/GBrain]]"
  - "[[concepts/DreamCycle]]"
  - "[[sources/gbrain-2026-05-11]]"
---

# Minions 任务队列

**来源**：[[entities/GBrain]] by [[people/GarryTan]]  
**类型**：确定性后台任务队列

---

## 是什么

Minions 是 GBrain 的后台 Job Queue，负责运行**确定性**（非 LLM 驱动）的维护和富化任务，不阻塞 Agent 的主会话。

## 用途

- 批量实体富化（爬取公司信息、补全人物档案）
- 交叉引用生成（新页面入库后的反向链接构建）
- [[concepts/DreamCycle|Dream Cycle]] 夜间维护任务触发
- 大批量摄入的分步处理

## 设计原则

**确定性**：Minions 执行的任务是规则驱动的，不是 Agent 推理驱动的。这保证了可预测性和可重试性。

**不阻塞**：Agent 摄入一条新数据后，富化工作交给 Minions 队列异步完成，Agent 立即可用于下一个任务。

**崩溃恢复**：GBrain 支持 durable subagent 执行，Minions 任务在崩溃后可从断点恢复。

## 生产规模

GBrain 生产环境挂载 **21 个自主 cron 任务**，均通过 Minions 队列调度。

## 关联

- [[concepts/DreamCycle]] — 主要调度目标之一
- [[entities/GBrain]] — 实现系统
- [[entities/OpenClaw]] — 运行这些 Minions 的平台

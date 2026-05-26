---
address: c-000154
type: source
title: "Effective Context Engineering for AI Agents — Anthropic Engineering（2026-05-26）"
created: 2026-05-26
updated: 2026-05-26
tags:
  - ai-agent
  - context-engineering
  - llm
  - anthropic
status: active
related:
  - "[[entities/Anthropic]]"
  - "[[concepts/上下文工程]]"
  - "[[concepts/上下文腐化]]"
  - "[[concepts/渐进式上下文注入]]"
---

# Effective Context Engineering for AI Agents

**来源：** Anthropic Engineering Blog  
**URL：** https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents  
**日期：** 2026-05-26  
**原始文件：** `.raw/articles/anthropic-context-engineering-agents-2026-05-26.md`

---

## 摘要

Anthropic 工程博客详述了"上下文工程"（Context Engineering）这一概念——超越提示工程，管理 Agent 推理过程中全部 token 信息的技术体系。核心主张：LLM 的有效性取决于**在正确时刻向模型提供正确的信息**，而非单纯扩大上下文窗口。

---

## 核心概念

### 上下文工程 vs. 提示工程

| 维度 | 提示工程 | 上下文工程 |
|---|---|---|
| 范围 | 单次 prompt 写法与组织 | 多轮推理中全部 token 的管理 |
| 关注点 | 指令措辞 | 系统提示 + 工具 + 外部数据 + 消息历史 |
| 时间维度 | 静态 | 动态、随任务演进 |

### 上下文腐化（Context Rot）

Transformer 架构的固有限制：注意力关系随序列长度呈 **n² 增长**，导致上下文越长性能越低。不断扩大窗口并非解决方案——需要主动管理 token 质量。

→ 详见 [[concepts/上下文腐化]]

### 高信号 Token 原则

> "最小化高信号 token 集合，最大化期望结果的概率。"

---

## 实践原则

### 系统提示"恰当海拔"

- **太低**（过度硬编码）：脆弱，无法泛化
- **太高**（过度抽象）：Agent 在共享上下文中迷失
- **恰当**：具体足以引导，灵活足以应对变化

### 工具设计

工具应满足三个条件：
1. **自包含**（self-contained）：不依赖外部隐式状态
2. **容错**（robust to error）：输入异常时有合理降级
3. **意图明确**（extremely clear）：避免多个工具功能重叠

---

## 长任务上下文策略

### 1. Compaction（上下文压缩）

对话历史达到阈值时，将其**压缩摘要**并用新的上下文窗口重初始化。保留关键架构决策，丢弃冗余中间输出。

### 2. 结构化笔记

Agent 在上下文窗口**外部**维护持久记忆（scratchpad / notes），跨复杂任务追踪进度。

### 3. 子 Agent 架构

专化 Agent 以干净上下文窗口处理聚焦任务，返回压缩摘要给协调 Agent——"清晰的关注点分离"。

### 4. 即时检索（JIT Retrieval）

维护轻量标识符，通过工具**动态加载**数据，而非预先处理全部内容。镜像人类认知，实现渐进式披露。

→ 与 [[concepts/渐进式上下文注入]] 高度重合；Anthropic 的表述侧重 Agent 工具调用层面

---

## 混合方案

最优实践往往结合多种策略：部分数据提前检索（速度优先），复杂情况允许自主探索（灵活优先）。无通用最优解，取决于任务特性。

---

## 实践建议

1. **从最小 prompt 开始**，配合最强模型
2. **按失败模式迭代**添加指令，而非预先过度指定
3. 把上下文视为**有限稀缺资源**，无论窗口多大

---

## 关联概念

- [[concepts/上下文工程]] — 本文核心概念的完整定义
- [[concepts/上下文腐化]] — Context Rot 机制与影响
- [[concepts/渐进式上下文注入]] — JIT 检索的先前相关讨论
- [[concepts/Agent评估体系]] — 评估 Agent 上下文策略效果
- [[concepts/Eval驱动开发]] — 按失败模式迭代与 eval-first 开发相通

---

## 来源

- Anthropic Engineering Blog, 2026-05-26

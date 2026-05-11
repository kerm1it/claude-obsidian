---
type: concept
address: c-000045
title: "Anthropic Dreaming（异步记忆优化）"
created: 2026-05-11
updated: 2026-05-11
tags:
  - agent-memory
  - dreaming
  - managed-agents
  - anthropic
  - self-learning
status: active
related:
  - "[[concepts/AgentMemoryAPI]]"
  - "[[concepts/DreamCycle]]"
  - "[[entities/GBrain]]"
  - "[[sources/memory-dreaming-self-learning-agents-2026-05-11]]"
---

# Anthropic Dreaming（异步记忆优化）

**发布时间**：2026-05-11（研究预览，Managed Agents API）  
**来源**：[[sources/memory-dreaming-self-learning-agents-2026-05-11]]  
**产品归属**：[[concepts/AgentMemoryAPI]]（Anthropic Managed Agents）

---

## 是什么

Dreaming 是 Anthropic 在 Managed Agents API 中发布的**离线批处理记忆优化过程**。它在 Agent 工作会话之外独立运行，分析近期多个 Agent 的 transcript，提取跨 Agent 模式，自动生成和整理记忆内容。

> 类比：人类睡眠时的记忆巩固——短期工作记忆 → 长期知识库

---

## 工作流程

```
1. 触发（cron / API / Agent 任务完成后）
          ↓
2. 扫描近期 Agent session transcripts
          ↓
3. 多个子 Agent 并发分析 transcript
          ↓
4. 识别：共同错误 / 成功策略 / 重复条目 / 过时内容
          ↓
5. 生成 diff（更新/新增/删除/验证注释）
          ↓
6. 应用到 memory store（立即或经人工审查）
```

---

## 核心设计原则

### 1. 离线、带外（Out-of-Band）
- 完全独立于 Agent 正在执行的任务
- 零热路径延迟：不影响 Agent 响应速度
- 更适合多 Agent 系统：可同时观察多个 Agent

### 2. 目标分离
- Agent 本身：专注任务执行（task performance）
- Dreaming：专注记忆质量（memory quality）
- 不混合目标 → 两者都做得更好

### 3. 跨 Agent 视角
- 单 Agent 只有自己的上下文和历史
- Dreaming 可跨多个并发 Agent 发现共同模式
- 例：60 秒重试模式——每个单独 Agent 都看不到，Dreaming 一眼识别

### 4. 扩展律类比
- 类似 test-time compute：用更多计算换更好输出
- 类似搜索引擎索引：提前整理好，下游高效命中
- 成本均摊到所有从 memory store 读取的 Agent

---

## 输出内容（Diff 类型）

| 操作 | 说明 |
|------|------|
| **更新** | 补充新发现的模式或纠正旧描述 |
| **去重** | 多条相同条目合并为一 |
| **删除** | 标记为过时或不再有效的条目 |
| **验证注释** | "此记忆在 [日期] 经 transcript 验证，仍准确" |
| **新增** | 从 transcript 中提取首次出现的模式 |

---

## 触发方式

- **Console**：手动点击启动
- **API cron**：定期自动触发（如每日）
- **任务完成后**：Agent spin-down 时自动调用

---

## 效果数据

| 客户 | 场景 | 效果 |
|------|------|------|
| Harvey | 法律场景基准 | 任务完成率 **↑ 6×** |
| Rockutin | 知识 Agent | 首次犯错率 **↓ 90%** |

---

## 与 GBrain Dream Cycle 对比

> [!note] 同构概念，独立实现
> [[concepts/DreamCycle]] 和 Anthropic Dreaming 在功能上高度同构，但实现路径完全独立。

| 维度 | Anthropic Dreaming | GBrain Dream Cycle |
|------|--------------------|--------------------|
| 来源 | Anthropic 官方 API | Garry Tan 开源项目 |
| 触发 | cron / API / 任务后 | cron（21个自主 cron 之一）|
| 输入 | Agent session transcripts | 时间线事件（Timeline） |
| 输出 | Memory store diff | Compiled Truth 更新 |
| 范围 | 多 Agent 跨 session | 单 vault 跨页面 |
| 状态 | 研究预览（2026-05） | 开源可用 |

---

## 关联概念

- [[concepts/AgentMemoryAPI]] — 记忆存储层（Dreaming 的上层依赖）
- [[concepts/DreamCycle]] — GBrain 同构实现
- [[concepts/乐观并发]] — memory store 并发保护
- [[entities/GBrain]] — 开源参考实现

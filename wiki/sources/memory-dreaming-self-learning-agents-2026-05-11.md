---
type: source
address: c-000043
title: "Memory and Dreaming for Self-Learning Agents"
created: 2026-05-11
updated: 2026-05-11
source_url: "https://www.youtube.com/watch?v=RtywqDFBYnQ"
source_type: youtube
author: "[[people/Mahesh]]"
channel: "Claude (Anthropic)"
tags:
  - agent-memory
  - dreaming
  - managed-agents
  - anthropic
  - self-learning
status: active
related:
  - "[[concepts/AnthropicDreaming]]"
  - "[[concepts/AgentMemoryAPI]]"
  - "[[concepts/DreamCycle]]"
  - "[[entities/GBrain]]"
---

# Memory and Dreaming for Self-Learning Agents

**来源**：YouTube，[[people/Mahesh]]（Anthropic 平台团队 PM）  
**发布频道**：Claude @ Anthropic  
**链接**：https://www.youtube.com/watch?v=RtywqDFBYnQ

---

## 核心主张

Memory 是继 MCP、Skills 之后 Anthropic 平台的**下一个核心原语**，目标是实现 Agent 的持续自学习（continuous self-learning）。**Dreaming** 是今日同步发布的配套异步批处理过程，通过分析 Agent 历史 transcript 来自动更新和整理记忆。

---

## 主要内容

### Agent 记忆原语的演进

- **CLAUDE.md**（~1.5年前）：最早形态，Agent 给自己留笔记，受限
- **Memory Tool**（SDK 内）：结构化 tool call，参数/格式固定，仍有约束
- **文件系统式记忆**（当前）：把记忆建模为文件系统，Claude 自主用 Bash/Grep 管理，不过度约束

> 设计哲学：随模型能力提升，逐渐"让开"（get out of the model's way），把更多决策权交给 Claude

**Claude Opus 4.7** 在文件系统式记忆基准上达到 SOTA：
- 更准确判断什么值得记忆
- 更善于组织记忆层级/文件分割
- 完全使用 Bash + Grep 工具，与 agentic coding 能力共轭

### Anthropic Memory API 核心特性

| 特性 | 说明 |
|------|------|
| **文件系统模型** | Claude 将记忆视为有层级的文件集合，自主读写 |
| **权限作用域** | 同一 Agent 可对 A 存储只读、对 B 存储读写 |
| **乐观并发** | content hash 校验，防止并发写入互相覆盖 |
| **版本历史** | 每次更新完整 audit log，含 agent 归因、session ID、时间戳 |
| **独立 API** | 可在 managed agents 之外单独调用，支持 PII 扫描/外部同步 |

### Dreaming

**定义**：独立于 Agent 工作会话的离线批处理流程，分析近期多个 Agent 的 transcript，提取跨 Agent 模式，生成更新后的记忆 diff。

**工作方式**：
- 触发：Console 手动、API cron、Agent 任务完成后自动触发
- 处理：扫描历史 transcript → 识别共同错误/成功策略 → 去重整合 → 验证时效性 → 输出 diff
- 应用：立即应用或通过 API 先做人工审查

**核心优势**：
1. **跨 Agent 视角**：单个 Agent 只有自己的上下文；Dreaming 可同时看多个 Agent，发现任何单个 Agent 都看不到的模式
2. **目标分离**：把"记忆质量"目标从"任务完成"目标中分离，Agent 专注执行，Dreaming 专注维护
3. **零热路径延迟**：离线运行，不影响 Agent 正在执行的任务
4. **扩展律类比**：类似 test-time compute——用更多计算让记忆系统更优，成本均摊到所有下游 Agent

**类比**：
- 像搜索引擎的**索引构建**：提前建好高质量索引，检索时高效命中
- 像人类**睡眠时的记忆巩固**（与 [[concepts/DreamCycle]] 同构，但 Dreaming 是 Anthropic 官方实现）

### 客户案例

| 客户 | 场景 | 效果 |
|------|------|------|
| **Rockutin** | 内部知识 Agent | 首次重复犯错率 ↓ 90%，token 效率↑，延迟↓ |
| **Harvey** | 法律场景基准 | 任务完成率 ↑ 6×（Dreaming 部署后） |

### 三层记忆架构

```
存储层（Storage）     → 数据位置、归因元数据、版本历史
结构/内容层（Structure）→ 文件系统模型、Skills 式程序化记忆
过程层（Process）     → 写入频率、触发机制、来源 → 即 Dreaming
```

### Demo 场景（SRE Agent）

组织级只读知识存储（runbook、SLO）+ Agent 工作读写存储：
1. P1 alert 触发 SRE Agent A → 调查 CPU、流量、近期 PR → 写入记忆
2. 同一 alert 再次触发 Agent B → 直接读取 Agent A 的调查结论 → 跳过重复调查 → token 效率↑
3. Dreaming 发现多 Agent 均在 upstream CPU 峰值后 60 秒触发（retry 逻辑低效）→ 写入模式注释
4. Dreaming 去重五条相同条目、删除过时条目、添加验证注释

---

## 关键引用

> "Memory is the next primitive. It's the thing that I think will get us to self-learning agents that evolve and improve based on the tasks that they're working on."
> — Mahesh, Anthropic Platform PM

> "Dreaming really lets us separate out this new objective of memory quality… from the task completion and task performance objective that a lot of agents already have today."

---

## 关联页面

- [[concepts/AnthropicDreaming]] — Dreaming 概念页
- [[concepts/AgentMemoryAPI]] — Anthropic Memory API 详解
- [[concepts/DreamCycle]] — GBrain 的同构实现（对比）
- [[concepts/乐观并发]] — 并发写入保护机制
- [[entities/GBrain]] — 同期开源替代方案
- [[people/Mahesh]] — 演讲者

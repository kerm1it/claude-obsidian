---
type: concept
address: c-000052
title: "智能体GC（Agent Garbage Collection）"
created: 2026-05-11
updated: 2026-05-11
tags:
  - agent-engineering
  - technical-debt
  - codex
  - automation
status: active
related:
  - "[[concepts/智能体优先工程]]"
  - "[[concepts/DreamCycle]]"
  - "[[concepts/AnthropicDreaming]]"
  - "[[sources/harness-engineering-openai-2026-02-11]]"
---

# 智能体GC（Agent Garbage Collection）

**来源**：[[sources/harness-engineering-openai-2026-02-11]]，[[people/RyanLopopolo]]（OpenAI）  
**别称**：黄金原则 + 循环清理流程

---

## 问题背景

完全由智能体生成的代码库会产生熵：Codex 复现仓库中已有的模式，**包括不均衡或不理想的模式**，导致渐进式漂移。

初始解法（人工每周五清理，占 20% 工时）→ 不可扩展。

---

## 解决方案：黄金原则 + 后台 GC

### 黄金原则（Golden Principles）

将最佳实践编码为**可机械检查的规则**：

- 共享实用程序包优于手工编写的辅助工具（便于集中管理不变量）
- 不使用"YOLO 式"探测数据——验证边界或依赖类型化 SDK
- （其他团队品味一旦被捕捉，即成为规则）

### 后台循环清理

- 定期运行一组后台 Codex 任务
- 扫描代码偏差、更新质量等级
- 发起有针对性的重构 Pull Request
- 大多数 PR 可在一分钟内完成审查并自动合并

---

## 类比：垃圾回收

> "技术债务就像一笔高息贷款：不断以小额贷款的方式偿还债务，总比让债务不断累积、再痛苦地一次解决要好得多。"

人类的品味一旦被捕捉，就会持续应用于每一行代码。这也使团队能够每天发现并解决不良模式，而不是让它们在代码库中传播数天或数周。

---

## 与同类机制对比

| 机制 | 来源 | 输入 | 输出 |
|------|------|------|------|
| 智能体 GC | OpenAI / Ryan Lopopolo | 代码仓库偏差扫描 | 重构 PR |
| [[concepts/DreamCycle]] | GBrain / Garry Tan | 时间线事件 | Compiled Truth 更新 |
| [[concepts/AnthropicDreaming]] | Anthropic | Agent session transcripts | Memory store diff |

三者都是**异步离线批处理维护机制**，本质上解决同一问题：防止系统随时间积累熵。

---
type: concept
address: c-000055
title: "Test-Time Compute（推理时计算扩展）"
created: 2026-05-11
updated: 2026-05-11
tags:
  - test-time-compute
  - scaling
  - reasoning
  - anthropic
status: active
related:
  - "[[concepts/AdaptiveThinking]]"
  - "[[concepts/EffortDial]]"
  - "[[concepts/ScalingLaws]]"
  - "[[sources/the-thinking-lever-2026-05-11]]"
---

# Test-Time Compute（推理时计算扩展）

**来源**：[[sources/the-thinking-lever-2026-05-11]]，[[people/MattBleifer]]（Anthropic）

---

## 是什么

Test-time compute 是继**训练时扩展**（更大模型、更多数据、更长训练）之后的第二条智能扩展路径：**让模型在推理时花更多时间/token 来解决问题**。

两条路径都能提升性能，但切入角度不同：
- 训练时扩展 → 更聪明的模型
- 推理时扩展 → 同一模型在同一问题上做得更好

---

## 实验证据

同一 Opus 4.7 模型，在交通灯模拟任务上：

| Effort 级别 | 时间倍数 | Token 倍数 | 结果质量 |
|-------------|---------|-----------|---------|
| Low | 1× | 1×（~4600 tokens） | 基础，红绿灯放路中间 |
| High | 2× | 2× | 更好，多车型，智能驾驶模型 |
| Max | 10× | 10× | 最佳图形，最真实驾驶模式 |

适用范围：不只是软件工程，还包括 agentic search、computer use、PhD 级学术推理等所有知识工作领域。

---

## Claude 的三类推理时 Token

- **Thinking tokens**：内部推理、chain-of-thought、草稿本
- **Tool call tokens**：与外部环境交互（搜索、文件读写等）
- **Text tokens**：与用户沟通（进度更新、最终回答）

→ 详见 [[concepts/AdaptiveThinking]]

---

## 关联

- [[concepts/AdaptiveThinking]] — token 分配的自适应机制
- [[concepts/EffortDial]] — 用户控制推理时计算的接口
- [[concepts/ScalingLaws]] — 训练时扩展律（对比视角）

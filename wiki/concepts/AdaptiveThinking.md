---
type: concept
address: c-000056
title: "Adaptive Thinking（自适应思考）"
created: 2026-05-11
updated: 2026-05-11
tags:
  - adaptive-thinking
  - reasoning
  - anthropic
  - test-time-compute
status: active
related:
  - "[[concepts/TestTimeCompute]]"
  - "[[concepts/EffortDial]]"
  - "[[sources/the-thinking-lever-2026-05-11]]"
---

# Adaptive Thinking（自适应思考）

**发布时间**：Opus 4.6 起成为所有 benchmark 默认设置  
**来源**：[[sources/the-thinking-lever-2026-05-11]]，[[people/MattBleifer]]（Anthropic）

---

## 是什么

Adaptive Thinking 是 Claude token 分配机制的最新演进：**Claude 可以在任何时刻、以任何顺序、使用任意数量的 thinking token**，不受任何固定约束。

---

## 演进历史

```
早期推理模型
  固定顺序：Think → Tool → Text

Interleaved Thinking（交错思考）
  Think → Tool → Think → Tool → ... → Text
  （可在 tool call 之间插入 thinking）

Adaptive Thinking（当前）
  完全自由：任何顺序，按需思考
  可以：Text → Tool → Think → Text → Tool → Think → Text
  也可以：对简单问题完全不思考
```

---

## 关键澄清

**Adaptive Thinking 不是**：
- 模型路由（不是根据难度选择"思考模型"还是"非思考模型"）
- 思考开关（不是"至少思考一个 token"）

**Adaptive Thinking 是**：
- Claude 在每一步都拥有思考的**选项**
- 从"你必须在开始时思考"→"你可以在任何需要时思考"

---

## 与 Effort 的关系

Adaptive Thinking 是机制，Effort 是控制旋钮：
- 高 effort → Claude 通常思考更多、更长
- 低 effort → Claude 可能跳过 thinking
- 但具体行为完全 prompt-dependent（2+2 vs 复杂研究任务，差异巨大）

---

## 关联

- [[concepts/TestTimeCompute]] — 上层框架
- [[concepts/EffortDial]] — 用户控制接口

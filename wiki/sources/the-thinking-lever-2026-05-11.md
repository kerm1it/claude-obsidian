---
type: source
address: c-000053
title: "The Thinking Lever — Claude 推理时计算的设计哲学"
created: 2026-05-11
updated: 2026-05-11
source_url: "https://www.youtube.com/watch?v=OXJO4LldSnc"
source_type: youtube
author: "[[people/MattBleifer]]"
channel: "Claude (Anthropic)"
tags:
  - test-time-compute
  - effort
  - adaptive-thinking
  - anthropic
  - reasoning
status: active
related:
  - "[[concepts/TestTimeCompute]]"
  - "[[concepts/AdaptiveThinking]]"
  - "[[concepts/EffortDial]]"
  - "[[concepts/TaskBudgets]]"
---

# The Thinking Lever — Claude 推理时计算的设计哲学

**来源**：YouTube，[[people/MattBleifer]]（Anthropic 研究团队 PM）  
**频道**：Claude @ Anthropic  
**链接**：https://www.youtube.com/watch?v=OXJO4LldSnc

---

## 核心主张

Test-time compute（推理时计算）是继训练时扩展之后的第二条智能扩展路径。Claude 将 token 分为三类——Thinking、Tool Call、Text——并通过 **Effort 拨盘**和 **Task Budgets** 让用户控制 Claude 如何分配这些 token。

---

## Token 的三种类型

| 类型 | 作用 |
|------|------|
| **Thinking tokens** | Claude 的内部独白：逐步推理、探索选项、chain-of-thought、草稿本 |
| **Tool call tokens** | Claude 与外部世界交互：搜索、读写文件、执行代码 |
| **Text tokens** | Claude 与用户交互：进度更新、最终摘要、简单回答 |

三种 token 都有直接成本：**金钱 + 等待时间**。

---

## Thinking 机制的演进

```
早期推理模型
  → Think → Tool call → Text（固定顺序）

Interleaved Thinking（交错思考）
  → Think → Tool → Think → Tool → ... → Text

Adaptive Thinking（自适应思考，当前）
  → 任何顺序，按需思考，可完全不思考
```

**Adaptive Thinking** 自 Opus 4.6 起成为所有 benchmark 的默认设置：
- 不是模型路由（不是"难题用思考模型，简单题用非思考模型"）
- 不是思考开关（不是"至少思考一个 token"）
- 而是"**在每一步都拥有思考的选项**"

---

## Effort 拨盘

### 为什么 Effort 优于思考开关

思考开关是 Effort 的**劣质代理**：
- 开关控制的是 Claude **被允许如何工作**，而非**你希望它多努力**
- Effort 同时移动 thinking + tool use + text，而非单独切换某一项
- 类比：我们不会让同事"开/关内心独白"，而是告诉他"这件事要认真做"

### Effort 级别指南（Opus 4.7）

| 级别 | 适用场景 |
|------|----------|
| **max** | 最高难度任务；可能有边际递减，不一定最划算 |
| **extra high** | 大多数 coding & agentic 场景的最佳选择；Claude Code / claude.ai 默认值 |
| **high** | 平衡 token 用量与智能；intelligence-sensitive 任务的起点 |
| **medium** | 对成本敏感、可接受稍低智能 |
| **low** | 短任务、延迟敏感；注意：Claude 会走意外捷径，务必读 transcripts |

> **低 effort 的惊喜**：Claude Plays Pokémon 实验中，低 effort 下 Claude 自发采用"速通策略"——跳过训练师战斗、囤积物品、使用 Repel——说明低 effort ≠ 低智能，而是**最优化 token 效率**。

---

## Task Budgets（任务预算）

新功能：设置 Claude 在某任务上花费 token 的**上限**，到达上限前主动停下来与用户确认。预算可以是：
- Token 数量
- 时间
- 成本

随着 Claude 开始运行数天乃至数周的任务，Budget 会越来越重要。

---

## 模型选择 vs Effort 选择

| 场景 | 推荐 |
|------|------|
| 智能敏感 + 优化速度 | 大模型低 effort（如 Opus 低 effort ≈ Haiku 高 effort，但质量更好） |
| 成本敏感 + 任务不复杂 | 小模型（分类、信息提取、基础摘要） |
| 极低 time-to-first-token | 小模型 |
| 极低 time-to-last-token | 大模型低 effort |

> "小模型优化 time-to-first-token；大模型低 effort 优化 time-to-last-token。"

---

## 三条行动建议

1. **始终开启 thinking**：给 Claude 思考空间；用 Effort/Budget 调节幅度，而非用开关屏蔽
2. **用 evals 找最优 effort**：画出 token/时间/成本 vs 性能的 effort 曲线；读 transcripts
3. **没有 eval？用 extra high**：coding & agentic 任务的最佳默认值

---

## 北极星目标

> "Claude 在被要求时能极好地分配计算资源——你只需设定质量标准和预算，Claude 自己去找出最优做法。"

Adaptive Thinking、Effort、Budgets 是这个方向的第一步，但只是开始。

---

## 关联页面

- [[concepts/TestTimeCompute]] — 推理时扩展律
- [[concepts/AdaptiveThinking]] — 自适应思考机制详解
- [[concepts/EffortDial]] — Effort 拨盘设计哲学
- [[concepts/TaskBudgets]] — 任务预算
- [[people/MattBleifer]] — 演讲者

---
type: concept
address: c-000057
title: "Effort 拨盘"
created: 2026-05-11
updated: 2026-05-11
tags:
  - effort
  - test-time-compute
  - anthropic
  - ux
status: active
related:
  - "[[concepts/TestTimeCompute]]"
  - "[[concepts/AdaptiveThinking]]"
  - "[[concepts/TaskBudgets]]"
  - "[[sources/the-thinking-lever-2026-05-11]]"
---

# Effort 拨盘

**来源**：[[sources/the-thinking-lever-2026-05-11]]，[[people/MattBleifer]]（Anthropic）

---

## 是什么

Effort 是用户告诉 Claude **如何权衡时间、成本和质量**的接口。它同时调节 thinking、tool use 和 text token 的分配，而非单独切换某一项。

---

## 为什么优于思考开关

思考开关是 Effort 的**劣质代理**：

| 维度 | 思考开关 | Effort 拨盘 |
|------|---------|------------|
| 表达的是 | 允许 Claude 如何工作 | 希望 Claude 多努力 |
| 影响范围 | 仅 thinking tokens | thinking + tool use + text |
| 类比 | 让同事"开/关内心独白" | 告诉同事"认真对待这件事" |

---

## 级别指南（Opus 4.7）

| 级别 | 说明 | 适用场景 |
|------|------|---------|
| **max** | 最高计算投入，可能边际递减 | 最难任务，测试性能上限 |
| **extra high** | 智能与效率最佳平衡点 | **大多数 coding & agentic 任务；Claude Code 默认** |
| **high** | 平衡 token 与智能 | intelligence-sensitive 任务的起点 |
| **medium** | 成本优先，稍降智能 | 成本敏感场景 |
| **low** | 最快，最省 token | 短任务、延迟敏感；注意意外捷径 |

---

## 低 Effort 的反直觉行为

低 effort ≠ 低智能。Claude 在低 effort 下会**主动寻找最优化 token 效率的策略**：

> Claude Plays Pokémon 实验：低 effort 下 Claude 自发采用速通策略——跳过训练师战斗、囤积道具、使用 Repel 减少随机遇敌——用最少 token 通关。这需要相当的策略智能。

**实践建议**：低 effort 时务必读 transcripts，了解 Claude 实际走了哪些捷径。

---

## 如何选择 Effort

1. **有 evals**：画出 token/时间/成本 vs 性能的曲线，找边际收益拐点
2. **无 evals，coding/agentic 任务**：直接用 extra high
3. **有延迟要求**：low 或 medium，配合 transcript review

---

## 关联

- [[concepts/TaskBudgets]] — 配套的 token 上限控制
- [[concepts/AdaptiveThinking]] — Effort 调节的底层机制
- [[concepts/TestTimeCompute]] — 上层框架

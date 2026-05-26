---
type: concept
address: c-000153
title: "Eval 驱动开发（Eval-Driven Development）"
created: 2026-05-26
updated: 2026-05-26
tags:
  - evals
  - development-practice
  - anthropic
  - tdd
status: active
related:
  - "[[concepts/Agent评估体系]]"
  - "[[concepts/软件工厂]]"
  - "[[concepts/模型即产品]]"
  - "[[sources/anthropic-demystifying-evals-agents-2026-05-26]]"
---

# Eval 驱动开发（Eval-Driven Development）

**来源**：[[sources/anthropic-demystifying-evals-agents-2026-05-26]]  
**出处**：Anthropic Engineering Blog

---

## 核心思想

> "Build evals defining planned capabilities before agents can fulfill them, then iterate until performance improves."

先建 eval，再开发 agent。Eval 不只是事后检验，而是**开发前定义成功标准**的工具。

---

## 与 TDD 的对比

| TDD（测试驱动开发）| Eval 驱动开发 |
|------------------|-------------|
| 先写测试，再写代码 | 先建 eval，再迭代 agent |
| 测试是确定性的 | Eval 是概率性的（需要多次 trial）|
| 通过/失败 | 通过率 / pass@k / pass^k |
| 针对单个函数 | 针对多步 agent 行为 |

参见：[[concepts/软件工厂]]（TDD → 软件工厂 → Eval 驱动开发，同一演进方向）

---

## 实践流程

```
1. 定义目标能力（agent 应该能做什么？）
        ↓
2. 建立 eval 任务集（从真实失败案例出发）
        ↓
3. 确认基线分数（可能很低，甚至 0%）
        ↓
4. 迭代开发 agent（模型/prompt/工具改进）
        ↓
5. eval 通过率提升 → 能力实现
        ↓
6. 毕业进入回归套件 → 持续监控
```

---

## 关键实践

- **任务无歧义**：两位专家独立评分一致；包含参考解答
- **0% 通过率 ≠ agent 无能**：通常是任务设计有问题（如 Opus 4.5 初始在 CORE-Bench 42% 的案例）
- **阅读 transcript**：eval 结果低时，先读 transcript 确认是真实失败还是 grader 误判
- **监控饱和度**：接近 100% 时 eval 失去信号，需要更难任务

---

## 为什么 eval-first 有价值

1. **澄清规格歧义**：不同工程师对"成功"的理解不同，eval 强制对齐
2. **加速迭代**：把主观判断转为可测量的数字
3. **防止回归**：改进一个能力时，eval 套件立即捕获其他能力的下滑
4. **沟通工具**：产品和研究团队用同一套数字对话

---

## 与模型即产品的关系

[[concepts/模型即产品]]（Alex Albert）的 Research PM 工作流：
- PM 设计覆盖目标能力的 eval → hill climb 依据
- 每个模型版本的"规格文档"本质上是一套 eval 套件的定义

Eval 驱动开发是"模型即产品"在工程实践层的具体落地。

---

## 关联概念

- [[concepts/Agent评估体系]] — eval 驱动开发的基础设施
- [[concepts/软件工厂]] — 同方向：spec+test 驱动 AI 生成实现
- [[concepts/模型即产品]] — Research PM 用 eval 驱动模型改进

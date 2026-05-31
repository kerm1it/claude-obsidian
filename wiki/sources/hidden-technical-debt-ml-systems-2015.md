---
address: c-000310
type: source
title: "Hidden Technical Debt in Machine Learning Systems"
source_url: https://papers.nips.cc/paper_files/paper/2015/hash/86df7dcfd896fcaf2674f757a2463eba-Abstract.html
source_type: paper
author: "D. Sculley et al."
published: 2015
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - mlops
  - technical-debt
  - feedback-loops
status: active
related:
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
---

# Hidden Technical Debt in Machine Learning Systems

**来源**：NeurIPS 2015
**URL**：https://papers.nips.cc/paper_files/paper/2015/hash/86df7dcfd896fcaf2674f757a2463eba-Abstract.html

## 摘要

这篇经典论文指出 ML 系统会产生特殊技术债，包括 entanglement、hidden feedback loops、undeclared consumers 和 data dependencies。它是理解 data flywheel 风险的基础来源。

## 关键贡献

- Feedback loops 会让系统输出影响未来训练数据，形成难以观察的耦合。
- 数据依赖和 pipeline 债务常比模型代码更难管理。
- 系统应监控数据、模型、消费者和反馈路径，而不只监控模型指标。
- 对本 vault 的意义：数据飞轮不是纯正向复利，也会制造反馈污染和技术债。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层、8. 自我改进与前沿层

## 关联

- [[concepts/DataFlywheelFeedbackLoop边界]]
- [[Research: Data flywheel feedback loop 边界]]

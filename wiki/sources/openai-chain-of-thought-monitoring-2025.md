---
address: c-000303
type: source
title: "Detecting misbehavior in frontier reasoning models"
source_url: https://openai.com/index/chain-of-thought-monitoring/
source_type: research-blog
author: "OpenAI"
published: 2025-03-10
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - chain-of-thought
  - reward-hacking
  - monitoring
status: active
related:
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/TestTimeCompute]]"
---

# Detecting misbehavior in frontier reasoning models

**来源**：OpenAI Research
**URL**：https://openai.com/index/chain-of-thought-monitoring/
**发布时间**：2025-03-10

## 摘要

OpenAI 研究 chain-of-thought monitoring 是否能帮助检测 frontier reasoning models 的 misbehavior。文章将 reward hacking 作为代表性风险之一，并指出 CoT 可能比只看 actions 更早暴露意图，但直接优化 CoT 可能削弱这种可监控性。

## 关键贡献

- CoT monitoring 可作为第 6 层监控信号，辅助发现 reward hacking、欺骗或异常策略。
- 只看最终 action 可能太晚，reasoning trace 有时包含更早的风险信号。
- 如果训练直接惩罚 CoT 中的坏想法，模型可能学会隐藏意图，因此 CoT 不应被简单当成优化目标。
- 生产风险控制应结合 sandbox、trace、action monitoring、eval 和人工审查。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：3. 推理与能力层、5. Agent 系统层
- 作用：提供 reward hacking 的 trace / CoT detection 方向。

## 关联

- [[concepts/RewardHackingEvalOverfitting边界]]
- [[concepts/ReasoningEvalVerifier边界]]
- [[Research: Reward hacking eval overfitting 边界]]

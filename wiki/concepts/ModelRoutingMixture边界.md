---
address: c-000287
type: concept
title: "Model Routing / Mixture 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - model-routing
  - inference
  - mixture
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/Serving成本延迟边界]]"
  - "[[concepts/TestTimeCompute]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/ProductOrganizationLayer边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
sources:
  - "[[sources/openai-model-selection-2026]]"
  - "[[sources/routellm-2024]]"
  - "[[sources/routerbench-2024]]"
  - "[[sources/frugalgpt-2023]]"
  - "[[sources/optimizing-model-selection-compound-ai-systems-2025]]"
  - "[[sources/mixture-of-agents-2024]]"
  - "[[sources/switch-transformers-2021]]"
  - "[[sources/aws-secure-agent-access-mcp-2026]]"
  - "[[sources/test-before-you-deploy-llm-supply-chain-2026]]"
---

# Model Routing / Mixture 边界

Model routing 是推理时控制面：根据任务、风险、成本、延迟、上下文长度、用户等级和质量要求，选择哪个模型、哪种 effort、是否级联、是否并行组合。它主属第 3 层，因为它发生在 inference/runtime，而不是训练权重本身。

一句话：**routing 不是“多接几个模型”，而是用 eval 证明某个选择策略在 cost-quality frontier 上更好。**

## 主归属

- 主归属：3. 推理与能力层
- 上游输入：请求特征、任务类型、SLO、成本预算、风险等级、eval 结果、模型池
- 下游输出：模型选择、cascade/escalation、parallel ensemble、per-module model allocation、成本/质量 trace
- 交叉链接：2. 模型构建层、5. Agent 系统层、6. 评估与可靠性层、7. 产品与组织层

## 四种容易混淆的 mixture

| 类型 | 主归属 | 边界 |
|---|---|---|
| Internal MoE | 2. 模型构建层 | 模型内部 router 选择专家参数，是架构/训练问题 |
| Runtime model router | 3. 推理与能力层 | 请求进来后选择强/弱模型、provider、effort 或 cascade |
| Compound / multi-agent selection | 5. Agent 系统层 | 在多模块或多 agent 系统中为不同步骤分配模型 |
| Product policy routing | 7. 产品与组织层 | 按用户等级、SLO、风险和价格策略约束路由 |

## 稳定链路

```text
request / task features / risk / SLO
    -> routing policy or learned router
    -> cheap-fast default or strong model
    -> confidence / verifier / guardrail
    -> escalate, parallelize, or stop
    -> log quality + cost + latency
    -> update eval, router, model pool, or product policy
```

## 核心策略

| 策略 | 适用场景 | 风险 |
|---|---|---|
| 静态规则 | 早期、任务分类清楚、成本敏感 | 规则过时，长尾覆盖差 |
| Strong-first distill | 先用强模型达到质量，再蒸馏到小模型 | 数据集偏、目标变化 |
| Cheap-first cascade | 便宜模型先答，低置信或失败再升级 | confidence 不可靠会误杀难题 |
| Learned router | 流量足够、模型池稳定、eval 丰富 | router 自身漂移或过拟合 |
| Parallel ensemble / MoA | 高价值、开放式、需要多视角质量 | 成本和延迟高，聚合器可能偏 |
| Per-module selection | compound AI / agent workflow | 局部最优不等于端到端最优 |

## 与相邻概念区别

- 与 serving：serving 提供执行、排队、cache、batching 和指标；routing 选择哪个执行路径。
- 与 TTC：TTC 决定投入多少推理计算；routing 决定用哪个模型或策略承载这笔计算。
- 与 verifier：verifier 给 routing 提供质量/置信/失败信号，但 verifier 本身不是 router。
- 与 distillation：distillation 把稳定强模型行为压进小模型；routing 是运行时选择，二者经常组合。
- 与 tool permissioning：routing 决定调用哪个模型或 provider；permissioning 决定请求携带的数据和工具权限能否发往该 provider 或工具。
- 与 multi-provider governance：governance 先过滤 provider/model 是否合规可用；routing 只在 allowed set 内优化成本、质量和延迟。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：router policy、model pool、fallback path 和 escalation threshold 的改动都要经过 release gate、canary 和 rollback trigger。
- 与 agent planning：planning 选择行动步骤；model routing 选择每一步用什么模型。

## 评估方式

- Cost-quality frontier：同等质量下更低成本，或同等成本下更高质量。
- Regret vs oracle：与知道每个模型答案质量的理想 router 相比差多少。
- Calibration：router 预测的成功率和真实成功率是否一致。
- Safety false downgrade：高风险/高难任务被错路由到弱模型的概率。
- Latency overhead：routing、cascade、parallelism 额外增加多少 TTFT/E2E latency。
- Drift：模型版本、流量分布、价格和 provider 行为变化后是否退化。
- Trace attribution：失败是否能归因到 router、模型、prompt、context、tool 或 eval。
- Gaming resistance：router 是否被固定 eval、低质 confidence、KPI 或 adversarial prompt 诱导错路由。

## 实践顺序

1. 先用最强模型和真实 eval 建立质量上限。
2. 收集真实请求、成本、延迟、失败类型和输出标签。
3. 尝试小模型、prompt 压缩、cache、distillation，建立候选模型池。
4. 从透明静态规则或 cheap-first cascade 开始。
5. 只有在流量、标签和模型池足够稳定时，引入 learned router。
6. 给高风险任务设置强制强模型、人工审批或 verifier gate。
7. 用持续 eval 监控 cost/success，而不是只看 cost/request。

## 过时风险

- 平台模型能力和价格变化会迅速改变最优路由策略。
- Provider 可能在底层已做隐藏路由；应用层 router 需要证明额外收益。
- Router 依赖的 benchmark 会污染或过拟合，必须使用真实私有流量。
- 复杂 routing 增加可观测性和调试负担；没有 trace/eval 时得不偿失。
- Router 也会被 [[concepts/RewardHackingEvalOverfitting边界|eval overfitting]] 污染：公开任务上学会省钱，不代表真实高风险任务安全。

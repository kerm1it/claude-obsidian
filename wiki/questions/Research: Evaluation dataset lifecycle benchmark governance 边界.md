---
address: c-000394
type: synthesis
title: "Research: Evaluation dataset lifecycle benchmark governance 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - evals
  - benchmark-governance
status: developing
related:
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
sources:
  - "[[sources/openai-evaluation-best-practices-2026]]"
  - "[[sources/openai-evals-framework-2026]]"
  - "[[sources/helm-holistic-evaluation-2022]]"
  - "[[sources/dynabench-2021]]"
  - "[[sources/livebench-2024]]"
  - "[[sources/benchmarking-benchmark-leakage-2024]]"
---

# Research: Evaluation dataset lifecycle benchmark governance 边界

## Overview

Evaluation dataset lifecycle / benchmark governance 的稳定核心是“eval set 是质量门资产，不是一次性测试文件”。它主属第 6 层，因为它决定样本、split、rubric、grader、hold-out、公开 benchmark、泄漏防护、刷新和退役如何产生可靠证据；第 7 层把这些证据接入 release gate、risk owner 和产品决策。

## Key Findings

- OpenAI eval best practices 将 eval 流程拆成 objective、dataset、metrics、run/compare、continuous evaluation，并强调生产分布、日志挖掘、人类校准和持续增长 eval set。（Source: [[sources/openai-evaluation-best-practices-2026]]）
- OpenAI Evals 将 eval 实现为框架和 registry：用数据、YAML/config、templates、graders 和 run outputs 表达可重复评估；这说明 eval dataset 与 eval harness 是不同对象。（Source: [[sources/openai-evals-framework-2026]]）
- HELM 提出多场景、多指标的 holistic evaluation，并强调透明度和原始 prompts/completions 发布；这说明 benchmark governance 不应只看单一 accuracy 排名。（Source: [[sources/helm-holistic-evaluation-2022]]）
- Dynabench 反对静态 benchmark 饱和，主张人机在环动态收集挑战样本；这提供了 refresh / adversarial collection 的稳定模式。（Source: [[sources/dynabench-2021]]）
- LiveBench 通过月度更新、近期来源和自动客观评分来降低污染风险；这说明 renewable benchmark 是抗污染策略之一，但仍要治理来源、可复现性和更新节奏。（Source: [[sources/livebench-2024]]）
- Benchmark leakage 研究提出公开 benchmark 可能被训练、调参或模型选择污染，并建议用 transparency card 记录 benchmark 使用历史；这直接支持 lineage 和 anti-leakage controls。（Source: [[sources/benchmarking-benchmark-leakage-2024]]）

## Stable Classification

- 主归属：6. 评估与可靠性层
- 上游：产品目标、风险场景、失败 trace、human feedback、data rights、lineage、public benchmarks
- 下游：release gate、regression signal、model/provider comparison、risk register、training/context/tool/router fixes
- 关键连接：第 6 层决定证据可信度；第 7 层决定这些证据控制哪些发布、采购、SLO 和风险动作；第 8 层只能用通过 gate 的 eval failure 生成改进候选。

## Engineering Practice

1. 每个 eval set 先写 objective、owner、decision controlled、risk tier 和 freshness policy。
2. 按用途分 split：dev/tuning、regression、private hold-out、public benchmark、red-team、canary、production shadow。
3. 每条样本保存 lineage、rights、source date、rubric/grader version、model exposure、split 和下游使用。
4. 对公开 benchmark 查 contamination；对私有 hold-out 控制访问和结果泄露。
5. 持续监控 saturation、drift、flakiness、grader calibration、production correlation 和 actionability。
6. 定期 refresh / retire：泄漏、过时、重复、无区分度、不再相关或无法归因的样本退出质量门。

## Open Questions

- Live benchmark 牺牲部分可复现性换抗污染，静态 benchmark 牺牲抗污染换可复现；不同领域需要不同平衡。
- LLM-as-judge 可降低评分成本，但 evaluator 本身也会被优化和污染，必须与 human gold 与 production outcomes 校准。
- Public benchmark transparency card 依赖模型开发者披露训练/调参接触历史；闭源模型和第三方供应商仍有审计缺口。

## Sources

- [[sources/openai-evaluation-best-practices-2026]]：生产 eval 流程和 continuous evaluation。
- [[sources/openai-evals-framework-2026]]：eval framework / registry / data + grader 实现边界。
- [[sources/helm-holistic-evaluation-2022]]：多场景、多指标、透明度 benchmark。
- [[sources/dynabench-2021]]：动态 benchmark 和人机在环挑战样本。
- [[sources/livebench-2024]]：月度更新、近期来源、抗污染 benchmark。
- [[sources/benchmarking-benchmark-leakage-2024]]：benchmark leakage 和 transparency card。

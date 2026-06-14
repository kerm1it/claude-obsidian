---
address: c-000579
type: source
title: "ShadowMerge"
source_url: https://arxiv.org/abs/2605.09033
source_type: paper
author: "Yang Luo, Zifeng Kang, Tiantian Ji, Xinran Liu, Yong Liu, Shuyu Li, Lingyun Peng"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - memory
  - graph-memory
  - security
status: active
related:
  - "[[concepts/MemorySkillGovernanceDrift边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
---

# ShadowMerge

**来源**：arXiv:2605.09033
**URL**：https://arxiv.org/abs/2605.09033
**标题**：ShadowMerge: A Novel Poisoning Attack on Graph-Based Agent Memory via Relation-Channel Conflicts

## 摘要

ShadowMerge 研究 graph-based agent memory 的投毒风险。攻击利用 relation-channel conflicts，使恶意关系与 benign evidence 共享 query-activated anchor 和 canonicalized relation channel，但携带冲突值，随后被图记忆系统合并和检索。

## 对本体系的贡献

- 说明 graph memory 不自动更安全；结构化关系反而会出现 relation conflict 和 merge 漂移。
- 支撑 memory governance 必须对 memory graph 做 conflict resolution、source trust、relation provenance 和 retrieval audit。
- 连接第 4 层 memory 与第 6 层 lineage/provenance graph 的边界。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：4. 上下文与知识层

## 关联

- [[concepts/MemorySkillGovernanceDrift边界]]
- [[Research: Memory skill governance drift 边界]]

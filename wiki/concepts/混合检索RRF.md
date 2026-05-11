---
type: concept
address: c-000036
title: "混合检索 + RRF 融合"
created: 2026-05-11
updated: 2026-05-11
tags:
  - search
  - rag
  - vector-search
  - information-retrieval
status: active
related:
  - "[[entities/GBrain]]"
  - "[[sources/gbrain-2026-05-11]]"
---

# 混合检索 + RRF 融合

**来源**：[[entities/GBrain]] by [[people/GarryTan]]  
**类型**：检索增强生成（RAG）技术模式

---

## 是什么

GBrain 的搜索流水线将三种检索方法融合为一个结果集：

| 方法 | 工具 | 优势 |
|------|------|------|
| **向量搜索** | pgvector + HNSW | 语义相似，捕捉意图 |
| **关键词搜索** | PostgreSQL tsvector | 精确匹配，速度快 |
| **RRF 融合** | 互惠排名融合算法 | 整合两种结果，无需调参 |

## 完整流水线

```
用户查询
  ↓ 意图分类（entity / temporal / event / general）
  ↓ 多查询扩展（multi-query expansion）
  ↓ HNSW 向量搜索 + tsvector 关键词搜索（并行）
  ↓ RRF 融合去重
  ↓ Compiled Truth 加权 + 反向链接排名
  → 最终结果
```

## 性能（BrainBench）

| 指标 | GBrain 混合 | 向量 baseline |
|------|------------|--------------|
| Precision@5 | **49.1%** | ~17.7%（推算） |
| Recall@5 | **97.9%** | — |
| P@5 提升 | **+31.4 pts** | — |

> [!key-insight] 关键洞察
> RRF 无需人工调权重，在向量召回率高（97.9%）的基础上，通过精准性来大幅提升 P@5。意图分类是前置过滤器，避免跨类别噪声。

## RRF 算法简介

互惠排名融合（Reciprocal Rank Fusion）：

$$\text{RRF}(d) = \sum_{r \in R} \frac{1}{k + r(d)}$$

其中 $k$ 通常取 60，$r(d)$ 是文档 $d$ 在排名列表 $r$ 中的位置。优点：不需要归一化各检索方法的分数，直接基于排名融合。

## 关联

- [[entities/GBrain]] — 实现此流水线的系统
- [[concepts/CompiledTruth时间线模式]] — 编译区加权是排名后处理步骤

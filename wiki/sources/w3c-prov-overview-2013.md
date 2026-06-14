---
address: c-000378
type: source
title: "PROV-Overview"
source_url: https://www.w3.org/TR/prov-overview/
source_type: standard
author: "W3C Provenance Working Group"
date_published: 2013-04-30
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - provenance
  - w3c
  - standard
status: active
related:
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
---

# PROV-Overview

**来源**：W3C
**URL**：https://www.w3.org/TR/prov-overview/

## 摘要

W3C PROV 是跨系统表达 provenance 的标准族。它将 provenance 定义为关于实体、活动和参与者的信息，可用于评估数据或对象的质量、可靠性和可信度。

## 关键贡献

- 提供稳定三元抽象：entity、activity、agent。
- 提供 PROV-O、PROV-DM、PROV-N、PROV-AQ 等互操作规范。
- 对本 vault 的意义：AI lineage 不应只记录文件路径，而要记录“什么 artifact 被什么 activity、由哪个 actor 生成或使用”。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、4. 上下文与知识层、5. Agent 系统层、7. 产品与组织层

## 关联

- [[concepts/DatasetLineageProvenanceGraph边界]]
- [[Research: Dataset lineage provenance graph 边界]]

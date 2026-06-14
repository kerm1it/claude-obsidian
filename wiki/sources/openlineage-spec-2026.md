---
address: c-000380
type: source
title: "OpenLineage Spec"
source_url: https://github.com/OpenLineage/OpenLineage/blob/main/spec/OpenLineage.md
source_type: specification
author: "OpenLineage"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - data-lineage
  - open-standard
  - metadata
status: active
related:
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
---

# OpenLineage Spec

**来源**：OpenLineage GitHub
**URL**：https://github.com/OpenLineage/OpenLineage/blob/main/spec/OpenLineage.md

## 摘要

OpenLineage 是数据 lineage metadata 的开放标准，面向运行中的 job instrumentation。它定义 run event、job、dataset、run 和 facet，并用 OpenAPI / JSON Schema 表达可扩展的 lineage 事件。

## 关键贡献

- 将数据作业建模为 consuming / producing datasets 的 job。
- 用 run event 捕获 job run 生命周期，至少包括 START 和 COMPLETE/FAIL/ABORT。
- 用 facets 扩展 run、job、dataset、input、output 的 metadata，包括 schema、source code、data quality metrics、column lineage 等。
- 对本 vault 的意义：AI 系统需要把传统数据 pipeline lineage 扩展到 agent trace、RAG、memory、skill、eval 和 self-improvement。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：5. Agent 系统层、7. 产品与组织层

## 关联

- [[concepts/DatasetLineageProvenanceGraph边界]]
- [[Research: Dataset lineage provenance graph 边界]]

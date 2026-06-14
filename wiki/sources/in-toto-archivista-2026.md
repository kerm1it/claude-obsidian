---
address: c-000531
type: source
title: "in-toto Archivista"
source_url: https://github.com/in-toto/archivista
source_type: open-source-repository
author: "in-toto"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - in-toto
  - attestation
  - provenance
  - evidence-store
status: active
related:
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
---

# in-toto Archivista

**来源**：in-toto Archivista repository
**URL**：https://github.com/in-toto/archivista

## 摘要

Archivista 是用于 in-toto attestations 的 graph and storage service。它把完整 attestation 存入 object store，同时抽取 metadata 放入可查询的 metadata store，使用户能按 artifact hash、依赖或其他 subject 关系检索相关 attestations。

## 关键贡献

- Evidence store 需要同时保存完整对象和可查询 metadata。
- Graph/API 层让 attestation retrieval 能按 subject、dependency 和 hash 找回。
- 对供应链 evidence 来说，存储与发现同等重要。
- 对本 vault 的意义：AI evidence retention 不应只是归档文件，还要建立 evidence index，支持 release、incident 和 reverify 时按 artifact/claim 找证据。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]
- [[concepts/EvidenceAttestationSignedEvalArtifact边界]]
- [[Research: Evidence retention audit packet lifecycle 边界]]

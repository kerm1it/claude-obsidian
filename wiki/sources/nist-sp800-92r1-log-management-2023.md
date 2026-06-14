---
address: c-000528
type: source
title: "NIST SP 800-92 Rev. 1 Cybersecurity Log Management Planning Guide"
source_url: https://csrc.nist.gov/pubs/sp/800/92/r1/ipd
source_type: draft-standard
author: "NIST"
date_published: 2023-10-11
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - nist
  - logs
  - audit
  - lifecycle
status: active
related:
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
---

# NIST SP 800-92 Rev. 1 Cybersecurity Log Management Planning Guide

**来源**：NIST SP 800-92 Rev. 1 Initial Public Draft
**URL**：https://csrc.nist.gov/pubs/sp/800/92/r1/ipd

## 摘要

NIST SP 800-92r1 把 log management 定义为 log data 的 generation、transmission、storage、access 和 disposal 全流程。日志不仅用于威胁检测，也用于 incident investigation、operational diagnosis 和满足 required retention period。

## 关键贡献

- Log/evidence lifecycle 包含 disposal，不只是收集与存储。
- 日志管理目标横跨 incident response、operations 和 compliance。
- 规划时需要考虑访问权限、保存期限、检索和销毁。
- 对本 vault 的意义：AI evidence packet 应有从生成到销毁的生命周期，而不是 release 后散落在 dashboard、CI 页面和聊天记录里。
- 对 privacy-preserving audit packet 的意义：log lifecycle 的 generation 和 disposal 都要纳入最小化策略，避免把原始 trace dump 当成长期默认证据。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]
- [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]
- [[Research: Evidence retention audit packet lifecycle 边界]]

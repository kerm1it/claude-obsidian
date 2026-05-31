---
address: c-000521
type: source
title: "Sigstore TUF trust root update and client compatibility"
source_url: https://blog.sigstore.dev/tuf-root-update/
source_type: announcement
author: "Sigstore TSC"
date_published: 2024-03-14
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - sigstore
  - tuf
  - trust-root
  - compatibility
status: active
related:
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
---

# Sigstore TUF trust root update and client compatibility

**来源**：Sigstore Blog
**URL**：https://blog.sigstore.dev/tuf-root-update/

## 摘要

Sigstore 2024 年公告计划发布新的 TUF trust root，说明新 root 会更新到新的 TUF specification，并列出不同 client 的兼容性影响。

## 关键贡献

- Trust root 更新可能不改变业务功能，却影响 verifier client 是否能加载新 metadata。
- 兼容 client 可自动获取并验证新的 TUF metadata；旧 client 需要升级。
- Root rotation 需要提前公告、兼容性矩阵和迁移窗口。
- 对本 vault 的意义：AI verifier policy 要把 client compatibility 和 root update 作为 release-gate 风险，而不是只看签名本身。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/VerifierPolicyTrustRootRotation边界]]
- [[Research: Verifier policy trust root rotation 边界]]

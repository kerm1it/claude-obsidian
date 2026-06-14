---
address: c-000522
type: source
title: "The Update Framework Root metadata API"
source_url: https://theupdateframework.readthedocs.io/en/v1.0.0/api/tuf.api.metadata.root.html
source_type: documentation
author: "The Update Framework"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - tuf
  - root-metadata
  - key-rotation
  - supply-chain
status: active
related:
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
---

# The Update Framework Root metadata API

**来源**：The Update Framework Docs
**URL**：https://theupdateframework.readthedocs.io/en/v1.0.0/api/tuf.api.metadata.root.html

## 摘要

TUF Root metadata API 描述 root metadata 的 version、spec_version、expires、keys、roles 和 consistent snapshot 等字段，并提供 add_key / remove_key 操作。

## 关键贡献

- Root metadata 明确包含 keys、roles 和 expiry，不只是一个单独公钥。
- add_key / remove_key 支持有状态的 key/root 轮换。
- metadata expiry 是 verifier 必须检查的 freshness 信号。
- 对本 vault 的意义：AI trust root rotation 应作为可版本化 metadata 生命周期管理，而不是临时替换 trust store。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/VerifierPolicyTrustRootRotation边界]]
- [[Research: Verifier policy trust root rotation 边界]]

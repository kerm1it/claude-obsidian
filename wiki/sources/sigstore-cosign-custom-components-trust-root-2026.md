---
address: c-000519
type: source
title: "Sigstore Cosign custom components and trusted roots"
source_url: https://docs.sigstore.dev/cosign/system_config/custom_components/
source_type: documentation
author: "Sigstore"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - sigstore
  - cosign
  - trust-root
  - tuf
status: active
related:
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
---

# Sigstore Cosign custom components and trusted roots

**来源**：Sigstore Docs
**URL**：https://docs.sigstore.dev/cosign/system_config/custom_components/

## 摘要

Sigstore Cosign custom components 文档说明 keyless verification 需要 Rekor、CT log 和 Fulcio 的验证材料；默认通过 TUF 获取，也可以配置自定义 TUF root、trusted-root file 或环境变量。

## 关键贡献

- 验证材料不是静态常量；默认由 TUF 分发和更新。
- 自建 Sigstore 或企业环境需要显式配置 custom root / trusted root。
- `--trusted-root` 和环境变量为 air-gapped 或自定义 trust boundary 提供路径。
- 对本 vault 的意义：AI evidence verifier 要记录使用哪套 trust root，而不是只记录“cosign verify passed”。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/VerifierPolicyTrustRootRotation边界]]
- [[Research: Verifier policy trust root rotation 边界]]

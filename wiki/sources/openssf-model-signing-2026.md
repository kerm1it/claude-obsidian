---
address: c-000502
type: source
title: "OpenSSF Model Signing"
source_url: https://openssf.org/projects/model-signing/
source_type: project
author: "OpenSSF"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - model-signing
  - openssf
  - ml-supply-chain
  - sigstore
status: active
related:
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
---

# OpenSSF Model Signing

**来源**：OpenSSF
**URL**：https://openssf.org/projects/model-signing/

## 摘要

OpenSSF Model Signing 旨在提供用于 ML model 签名和验证的 library / CLI，支持任意模型格式和模型大小，并支持 Sigstore、自签证书、公私钥等 PKI 方式，同时保持相同 hash scheme 和 signature format。

## 关键贡献

- 将 ML 模型也纳入 artifact signing 和 verification。
- 强调训练模型的团队、上传 hub 的团队和生产部署团队常常不是同一方。
- 建议在训练、上传、部署和作为另一个模型输入时都验证模型签名。
- 对本 vault 的意义：model snapshot 不能只靠文件名、hub 页面或人工信任；release gate 应消费 model signature 和 verification result。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层、2. 模型构建层

## 关联

- [[concepts/EvidenceAttestationSignedEvalArtifact边界]]
- [[Research: Evidence attestation signed eval artifact 边界]]

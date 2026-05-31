---
address: c-000381
type: concept
title: "Data Deletion / Unlearning Impact 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - data-deletion
  - machine-unlearning
  - governance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
sources:
  - "[[sources/gdpr-data-subject-rights-2016]]"
  - "[[sources/eu-gdpr-article-5-data-minimization-storage-accountability-2016]]"
  - "[[sources/machine-unlearning-sisa-2019]]"
  - "[[sources/google-machine-unlearning-challenge-2023]]"
  - "[[sources/machine-unlearning-comprehensive-survey-2024]]"
  - "[[sources/nara-general-records-schedules-2025]]"
  - "[[sources/slsa-source-requirements-evidence-expunging-2026]]"
---

# Data Deletion / Unlearning Impact 边界

Data deletion / unlearning impact 是第 7 层产品与组织层的数据生命周期执行边界：当用户、组织、合同、保留期、错误数据、版权/隐私风险或事故要求删除数据时，它负责定位受影响 artifact，决定删除、限制、匿名化、tombstone、重训、machine unlearning、模型替换或输出抑制，并把结果变成可审计证据。

一句话：**删除是从系统存储里移除数据；unlearning 是从模型行为或参数影响里移除数据痕迹。两者相连，但不是一回事。**

## 主归属

- 主归属：7. 产品与组织层
- 上游输入：deletion request、consent withdrawal、retention expiry、legal/contract policy、incident finding、bad data notice、lineage impact query
- 下游输出：delete/restrict/anonymize/unlearn/retrain/replace/suppress action plan、audit record、data card/model card update、regression eval
- 证据接口：6. 评估与可靠性层、[[concepts/DatasetLineageProvenanceGraph边界]]
- 模型接口：2. 模型构建层
- 知识接口：4. 上下文与知识层
- Agent 接口：5. Agent 系统层

## 稳定链路

```text
deletion trigger
    -> requester identity, scope, legal/contract basis, and exceptions
    -> lineage impact query across logs, RAG, memory, eval, training, models, providers, backups
    -> action plan: delete, restrict, tombstone, anonymize, unlearn, retrain, replace, suppress, or legal-hold
    -> execution with owner, due date, rollback, and provider coordination
    -> verification: data absence, downstream impact, model behavior, privacy attack, utility regression
    -> audit record, user/org response, cards/manifests update, prevent re-ingestion
```

## 删除目标分层

| 位置 | 首选动作 | 关键风险 |
|---|---|---|
| Product DB / files | 删除、限制、tombstone、备份到期清理 | 软删除后仍被检索或导出 |
| Logs / traces | 按用途和保留期删除或脱敏 | 影响 incident evidence 和安全审计 |
| RAG / vector store | 删除原文、chunk、embedding、cache 和索引 | chunk 残留、权限继承失败 |
| Memory / personalization | 用户可见、可删、可关闭 | 删除后又从 trace 重新写入 |
| Eval / benchmark | 删除或隔离样本，重算指标 | hold-out 失真、历史对比断裂 |
| Training dataset | 删除样本和派生合成样本，更新 manifest | lineage 不全导致漏删 |
| Model weights | 重训、exact/approximate unlearning、替换模型 | 无法证明影响已移除 |
| Provider / subprocessor | 触发供应商删除、日志保留和 DPA 流程 | 跨区域、feature-level state、备份延迟 |

## 与相邻概念区别

- 与 [[concepts/DataRightsPrivacyConsent边界]]：data rights 定义是否应该删除；本页定义删除如何执行到系统、数据集、模型和供应商。
- 与 [[concepts/DatasetLineageProvenanceGraph边界]]：lineage 提供影响面；本页消费影响面并执行删除/遗忘计划。
- 与 data retention：retention 是到期策略；deletion/unlearning 是具体请求或事件触发的处置。
- 与 [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]：删除/遗忘处理数据与模型影响；evidence retention 决定相关 logs、audit packet、tombstone、legal hold 和 disposition record 哪些可删、哪些需保留或匿名化。
- 与 [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]：删除/遗忘执行处置动作；privacy-preserving audit packet 决定删除后保留的 tombstone、摘要、hash、private annex 或 disposition record 是否足够且不过度。
- 与 redaction / output suppression：输出过滤可降低泄露，但不等于移除训练影响。
- 与 machine unlearning：machine unlearning 是第 2 层模型层技术；本页是第 7 层的全系统删除闭环，决定何时需要使用它。
- 与 incident response：事故可能触发删除或模型替换；postmortem 要把删除失败转成 regression、lineage 和 policy 测试。

## Unlearning 策略

| 策略 | 适用场景 | 代价 / 限制 |
|---|---|---|
| Full retraining | 高风险、数据量可控、要求强保证 | 成本高、周期长 |
| SISA / partitioned training | 预先按 shard/slice 训练，未来删除高频 | 需要训练前设计，可能影响精度 |
| Exact unlearning | 可证明等价于未见 forget set 的模型 | 通常限制较强，难扩展到大模型 |
| Approximate unlearning | 用梯度、微调、权重编辑、蒸馏近似移除影响 | 证明弱，需强 eval 和攻击测试 |
| Model replacement | 切换到未受影响版本或重训版本 | 需要版本库存和回滚路径 |
| Suppression / guardrail | 临时止血，阻止输出特定内容 | 不是 unlearning，不能单独当完成证据 |

## 评估方式

- Deletion coverage：所有受影响 store、index、cache、backup、provider、dataset 是否处理。
- Lineage impact precision：影响面查询是否漏报或误报。
- Re-ingestion prevention：删除数据是否会从 trace、backup、sync、crawler 或 self-improvement 再进入系统。
- Forgetting quality：forget set 的影响是否下降，membership inference attack 是否失效。
- Retain utility：保留集、hold-out、产品任务和安全 eval 是否保持。
- Retrained-model distance：unlearned model 是否接近从未包含 forget set 的重训模型。
- Audit completeness：request、scope、basis、action、owner、verification、exceptions 是否完整可查。
- User/org response time：是否能在承诺时限内完成或解释例外。

## 过时风险

- Machine unlearning 方法会快速变化，但“删除请求 → lineage 影响面 → 存储删除 → 模型影响处理 → 验证 → 审计 → 防再摄入”的链路稳定。
- 对大模型而言，样本级影响难以证明完全移除；很多实际方案是重训、替换、近似 unlearning 与输出抑制组合。
- 法律义务、合同、供应商保留期和备份策略会变化；工程上必须保留政策版本和例外记录。

## 一句话归类

Data deletion / unlearning impact 主属第 7 层，是 data rights 请求进入真实 AI 系统后的执行闭环；它依赖第 6 层 lineage/eval 定位和验证影响，在必要时调用第 2 层 retraining 或 machine unlearning。

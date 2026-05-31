---
address: c-000467
type: source
title: "Challenges to the Monitoring of Deployed AI Systems"
source_url: https://www.nist.gov/publications/challenges-monitoring-deployed-ai-systems-center-ai-standards-and-innovation
source_type: government-report
author: "NIST Center for AI Standards and Innovation"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai-monitoring
  - post-deployment
  - nist
  - drift
status: active
related:
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
---

# Challenges to the Monitoring of Deployed AI Systems

**来源**：NIST
**URL**：https://www.nist.gov/publications/challenges-monitoring-deployed-ai-systems-center-ai-standards-and-innovation

## 摘要

NIST AI 800-4 是关于 deployed AI system post-deployment monitoring 的官方报告。报告指出，预部署 eval 多在受控环境中进行，而部署后监控负责验证真实场景可靠性、追踪不可预期输出，并让部署上下文中的后果可见。

## 关键贡献

- 给 post-deployment AI monitoring 提供官方问题框架和术语基础。
- 把监控类别拆成 functionality、operational、human factors、security、compliance、large-scale impacts。
- 指出 performance degradation / drift、fragmented logging、human-AI feedback loop、monitor cadence、automated vs human-validated monitoring 是关键挑战。
- 对本 vault 的意义：post-release eval drift 应被视为 release evidence 生命周期问题，而不是普通服务 uptime 监控。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/PostReleaseEvalDrift边界]]
- [[concepts/EvidenceFreshnessStaleProof边界]]
- [[Research: Post-release eval drift 边界]]

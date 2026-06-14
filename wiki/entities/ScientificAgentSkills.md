---
id: c-000113
address: c-000113
type: entity
entity_type: open-source-repo
title: "Scientific Agent Skills"
aka: ["Claude Scientific Skills", "scientific-agent-skills"]
parent: "[[entities/KDenseAI]]"
url: https://github.com/K-Dense-AI/scientific-agent-skills
created: 2026-05-17
updated: 2026-06-12
tags:
  - agent-skills
  - science
  - open-source
  - python
  - research-tools
status: active
---

# Scientific Agent Skills

**23,247 ⭐ · 2,491 forks · MIT · Python · K-Dense Inc.**

> "Transform your AI coding agent into an 'AI Scientist' on your desktop."

由 [[entities/KDenseAI]] 出品。前身为 Claude Scientific Skills，改名以支持开放的 [[concepts/AgentSkillsStandard|Agent Skills 标准]]，兼容 Cursor、Claude Code、Codex、Gemini CLI 等。

---

## 核心数字

| 维度 | 数量 |
|------|------|
| 总 Skills | **135** |
| 科学数据库（直接访问）| **100+** |
| 优化 Python 包 Skills | **70+** |
| 科学领域 | **17** |
| 安全扫描 | 每周（Cisco AI Defense）|

---

## 能力概览（17 类）

| 类别 | 代表工具 |
|------|----------|
| 生物信息学 & 基因组学 | Scanpy, BioPython, scVelo, Arboreto, PyDESeq2, TileDB-VCF |
| 化学信息学 & 药物发现 | RDKit, DeepChem, DiffDock, OpenMM, Rowan |
| 蛋白质组学 | matchms, pyOpenMS |
| 临床研究 & 精准医学 | ClinVar, DepMap, Imaging Data Commons, PyHealth |
| 医学影像 | pydicom, histolab, PathML |
| 机器学习 & AI | PyTorch Lightning, TimesFM, PyMC, Torch Geometric, SHAP |
| 材料科学 & 物理 | Pymatgen, Astropy, PennyLane, Qiskit |
| 工程 & 仿真 | SimPy, SymPy, FluidSim |
| 数据分析 & 可视化 | GeoPandas, GeoMaster, Dask, Polars, NetworkX |
| 实验室自动化 | PyLabRobot, Ginkgo Cloud Lab, Benchling |
| 多组学 & 系统生物学 | PrimeKG, HypoGeniC, LaminDB |
| 蛋白质工程 | ESM, Glycoengineering, Adaptyv |
| 科学传播 | Paper Lookup, BGPT Paper Search, Open Notebook, Infographics |
| 科学数据库 | Database Lookup（78 个），Hugging Science（17 科学领域 HF 目录）|
| 基础设施 | Modal, GPU Optimization, DNAnexus, LatchBio |
| 研究方法论 | What-If Oracle, Consciousness Council, DHDNA Profiler |
| 监管 | ISO 13485 |

---

## 亮点 Skills

**BGPT Paper Search**：从论文全文（非摘要）提取 25+ 结构化字段，包括方法、样本量、质量评分。

**Open Notebook**：自托管 NotebookLM 替代品，支持 PDF/视频/音频/网页，16+ AI 提供商，多说话人播客生成。

**GeoMaster**：遥感、GIS、卫星图像处理，500+ 示例，支持空间机器学习。

**What-If Oracle**：多分支可能性探索，风险分析，战略选项生成。

**Hugging Science**：HuggingFace 上 17 个科学领域（天文、生物、化学、气候、基因组、材料、医学、物理等）的数据集/模型/Space 精选目录。

---

## 安装

```bash
npx skills add K-Dense-AI/scientific-agent-skills
# 或
gh skill install K-Dense-AI/scientific-agent-skills --agent claude-code
```

---

## 与 Skills 体系的关联

→ 见 [[skills/scientific-agent-skills-collection|Skills 详细分类页]]  
→ [[skills/_index|Skills 体系索引]]

## 关联

- [[entities/KDenseAI]] — 出品方
- [[concepts/AgentSkillsStandard]] — 遵循的标准
- [[skills/scientific-agent-skills-collection]] — Skills 集合页
- [[sources/scientific-agent-skills-2026-05-17|来源：GitHub README]]

---
id: c-000111
address: c-000111
type: source
title: "Scientific Agent Skills — GitHub README（2026-05-17）"
source_url: https://github.com/K-Dense-AI/scientific-agent-skills
fetched: 2026-05-17
created: 2026-05-17
updated: 2026-06-12
tags:
  - agent-skills
  - science
  - open-source
  - python
  - research
status: active
---

# Scientific Agent Skills — GitHub README（2026-05-17）

**来源**：https://github.com/K-Dense-AI/scientific-agent-skills  
**抓取日期**：2026-05-17  
**Stars**：23,247 | **Forks**：2,491  
**License**：MIT（各 skill 有独立 license，见各 SKILL.md）  

---

## 核心定位

[[entities/ScientificAgentSkills]] 是 [[entities/KDenseAI]] 出品的**开源科学研究 Agent Skill 合集**，包含 **135 个可即用的科学研究技能**，覆盖生物信息学、药物发现、蛋白质组学、临床研究、医学影像、机器学习、材料科学、物理、工程模拟、数据分析、地理空间科学、实验室自动化和科学写作。

遵循开放的 [[concepts/AgentSkillsStandard|Agent Skills 标准]]（agentskills.io），兼容 **Cursor、Claude Code、Codex、Gemini CLI** 等任意支持该标准的 agent。

> 🔔 **已从 Claude Scientific Skills 改名为 Scientific Agent Skills**，同一套技能，跨平台更广。

---

## 安装

```bash
# 官方标准方式（所有平台通用）
npx skills add K-Dense-AI/scientific-agent-skills

# GitHub CLI（v2.90.0+，支持按 agent 定向安装）
gh skill install K-Dense-AI/scientific-agent-skills
gh skill install K-Dense-AI/scientific-agent-skills scanpy          # 单个 skill
gh skill install K-Dense-AI/scientific-agent-skills --agent claude-code

# 版本锁定
gh skill install K-Dense-AI/scientific-agent-skills --pin v1.0.0
```

---

## 规模

| 维度 | 数量 |
|------|------|
| 总 Skills | **135** |
| 科学数据库（Database Lookup 覆盖）| **78+**（PubChem、ChEMBL、UniProt、ClinVar、ClinicalTrials.gov、FDA、FRED、USPTO 等）|
| 多数据库包（BioServices/BioPython/gget）| **100+** |
| 优化 Python 包 Skills | **70+** |
| 科学领域分类 | **17** |

---

## Skill 分类全览

### 🧬 生物信息学 & 基因组学（21+ skills）

| 工具 | 用途 |
|------|------|
| BioPython, pysam, scikit-bio | 序列分析 |
| Scanpy, AnnData, scvi-tools | 单细胞 RNA-seq |
| scVelo | RNA 速度（RNA Velocity）|
| Arboreto | 基因调控网络（GRN）推断 |
| Cellxgene Census | 单细胞公共数据库整合 |
| gget, geniml, gtars, deepTools | 基因组工具箱 |
| TileDB-VCF | 大规模 VCF 数据库管理 |
| PyDESeq2 | 差异表达分析 |
| ETE Toolkit, MAFFT, IQ-TREE 2, FastTree | 系统发育分析 |

### 🧪 化学信息学 & 药物发现（10+ skills）

| 工具 | 用途 |
|------|------|
| RDKit, Datamol, Molfeat | 分子操作与属性预测 |
| DeepChem, TorchDrug | 深度学习药物发现 |
| DiffDock | 分子对接与虚拟筛选 |
| OpenMM + MDAnalysis | 分子动力学模拟 + 轨迹分析 |
| Rowan | 云端量子化学（pKa、对接、共折叠）|
| MedChem, PyTDC | 药物相似性、基准测试 |

### 🔬 蛋白质组学 & 质谱（2 skills）

matchms（谱图匹配）、pyOpenMS（LC-MS/MS 处理、蛋白质定量）

### 🏥 临床研究 & 精准医学（8+ skills）

- **Database Lookup**：ClinicalTrials.gov、ClinVar、ClinPGx、COSMIC、FDA、cBioPortal
- **DepMap**：癌症细胞系依赖性评分、药物敏感性
- **Imaging Data Commons**：NCI 放射学 & 病理学数据集（idc-index）
- **PyHealth, NeuroKit2**：医疗 AI、生理信号处理
- **Clinical Reports, Treatment Plans**：临床报告生成

### 🖼️ 医学影像 & 数字病理（3 skills）

pydicom（DICOM 处理）、histolab（全切片图像分析）、PathML

### 🧠 神经科学 & 电生理（1 skill）

Neuropixels-Analysis：胞外棘波记录、硅探针、棘波排序

### 🤖 机器学习 & AI（16+ skills）

| 工具 | 用途 |
|------|------|
| PyTorch Lightning, Transformers | 深度学习 |
| Stable Baselines3, PufferLib | 强化学习 |
| scikit-learn, scikit-survival | 经典 ML |
| SHAP | 模型可解释性 |
| aeon, TimesFM | 时间序列（TimesFM 是 Google 零样本基础模型）|
| PyMC | 贝叶斯方法 |
| PyMOO | 多目标优化 |
| Torch Geometric | 图神经网络 |
| UMAP-learn | 降维 |
| statsmodels | 统计建模 |

### 🔮 材料科学 & 物理（7 skills）

Pymatgen、COBRApy（代谢建模）、Astropy（天文数据）、Cirq / PennyLane / Qiskit / QuTiP（量子计算）

### ⚙️ 工程 & 仿真（4 skills）

MATLAB/Octave、FluidSim（CFD）、SimPy（离散事件仿真）、SymPy（符号数学）

### 📊 数据分析 & 可视化（16+ skills）

| 工具 | 用途 |
|------|------|
| Matplotlib, Seaborn | 发表级可视化 |
| GeoPandas | GIS 分析 |
| GeoMaster | 遥感 & 地球观测（500+ 示例）|
| Dask, Polars, Vaex | 大规模数据处理 |
| NetworkX | 网络分析 |
| Document Skills | PDF/DOCX/PPTX/XLSX 处理 |
| Infographics | 10 种类型，8 种风格，色觉无障碍 |
| Markdown & Mermaid | 文本图表（作为文档默认标准）|

### 🧪 实验室自动化（4 skills）

PyLabRobot（液体处理）、Ginkgo Cloud Lab（无细胞蛋白表达）、Protocols.io、Benchling/LabArchives（LIMS）

### 🔬 多组学 & 系统生物学（4+ skills）

PrimeKG（精准医学知识图谱）、HypoGeniC（多组学整合）、LaminDB（数据管理）

### 🧬 蛋白质工程 & 设计（3 skills）

ESM（蛋白质语言模型）、Glycoengineering（糖工程、抗体优化）、Adaptyv（云端自动化蛋白测试）

### 📚 科学传播（20+ skills）

| 工具 | 亮点 |
|------|------|
| Paper Lookup | 10 个数据库：PubMed、PMC、bioRxiv、medRxiv、arXiv、OpenAlex、Crossref、Semantic Scholar、CORE、Unpaywall |
| **BGPT Paper Search** | 25+ 结构化字段（方法、结果、样本量、质量评分），来自全文而非摘要 |
| Literature Review, Scientific Writing, Peer Review | — |
| **Open Notebook** | 自托管 NotebookLM 替代品，16+ AI 提供商，多说话人播客生成 |
| **Parallel Web** | 合成网络搜索摘要，附引用 |
| Scientific Slides, LaTeX Posters, PPTX Posters | — |
| Scientific Schematics, Infographics | — |
| Generate Image | FLUX.2 Pro + Gemini 3 Pro |

### 🔬 科学数据库访问（6 skills → 100+ 数据库）

- **Database Lookup**：统一访问 78 个公共数据库（化学/基因组/临床/通路/专利/经济）
- **Hugging Science**：HuggingFace 上 17 个科学领域的数据集、模型、Space 精选目录

### 🔧 基础设施 & 平台（7+ skills）

Modal（云计算）、GPU Optimization（CuPy、Numba CUDA、cuDF、cuML）、DNAnexus、LatchBio、OMERO、Opentrons、Get Available Resources

### 🎓 研究方法论（12+ skills）

Scientific Brainstorming、Hypothesis Generation、Scientific Critical Thinking、Scholar Evaluation、**What-If Oracle**（多分支可能性探索）、**Consciousness Council**（多专家视角）、**DHDNA Profiler**（从任意文本提取认知特征）、Research Grants、Market Research Reports

### ⚖️ 监管 & 标准

ISO 13485 Certification（医疗器械认证）

---

## 伴侣产品

| 产品 | 定位 |
|------|------|
| **K-Dense BYOK** | 免费开源桌面 AI 共科学家；自带 API 密钥，40+ 模型，100+ 数据库，本地运行，可选 Modal 云计算 |
| **K-Dense Web** | 云端版：200+ skills（含独家），云 GPU，发表级输出，零配置 |

---

## 安全

- 每周对所有 skill 运行 **Cisco AI Defense Skill Scanner** 安全扫描
- 各 skill 有独立 license（可能不同于仓库 MIT）；使用前需查阅各 SKILL.md
- 推荐：只安装实际需要的 skill，不要一次安装全部

---

## 与现有 Skills 体系的关联

→ [[skills/scientific-agent-skills-collection|Skills 集合页：Scientific Agent Skills]]  
→ [[skills/_index|Skills 体系索引]] — 与 mattpocock/skills、claude-obsidian 并列的第三大来源

---

## 关联

- [[entities/ScientificAgentSkills]] — 实体页
- [[entities/KDenseAI]] — 出品方
- [[concepts/AgentSkillsStandard]] — 遵循的开放标准
- [[skills/scientific-agent-skills-collection]] — Skills 详细分类页

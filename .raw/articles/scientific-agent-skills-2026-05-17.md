---
source_url: https://github.com/K-Dense-AI/scientific-agent-skills
fetched: 2026-05-17
---

# Scientific Agent Skills — GitHub README

**Repo**: K-Dense-AI/scientific-agent-skills  
**Stars**: 23,247 | **Forks**: 2,491  
**Language**: Python  
**License**: MIT  
**Updated**: 2026-05-17  
**Org**: K-Dense Inc. (k-dense.ai)

## Description

A set of ready to use Agent Skills for research, science, engineering, analysis, finance and writing.

135 ready-to-use scientific and research skills covering cancer genomics, drug-target binding, molecular dynamics, RNA velocity, geospatial science, time series forecasting, 100+ scientific databases, and more. Works with any AI agent that supports the open Agent Skills standard: Cursor, Claude Code, Codex, Gemini CLI, and more.

## Key Facts

- **135 skills** organized into 17+ categories
- **100+ scientific databases** via unified database-lookup skill (PubChem, ChEMBL, UniProt, COSMIC, ClinicalTrials.gov, FRED, USPTO, and more)
- **70+ optimized Python package skills** — RDKit, Scanpy, PyTorch Lightning, scikit-learn, BioPython, OpenMM, scVelo, TimesFM, and others
- **Open Agent Skills standard** (agentskills.io) — cross-platform, not Claude-specific
- **Originally**: Claude Scientific Skills → rebranded to Scientific Agent Skills for broader compatibility

## Installation

```bash
# Standard (any platform)
npx skills add K-Dense-AI/scientific-agent-skills

# GitHub CLI
gh skill install K-Dense-AI/scientific-agent-skills
gh skill install K-Dense-AI/scientific-agent-skills scanpy  # single skill
gh skill install K-Dense-AI/scientific-agent-skills --agent claude-code
```

## Companion Product

**K-Dense BYOK** (github.com/K-Dense-AI/k-dense-byok): Free open-source AI co-scientist desktop app. Bring your own API keys, 40+ models, 100+ scientific databases, all 135 skills. Data stays local, optional cloud via Modal.

**K-Dense Web** (k-dense.ai): Cloud version with 200+ skills, cloud GPUs, publication-ready outputs, zero setup.

## Skill Categories (135 total)

### Bioinformatics & Genomics (21+ skills)
- Sequence analysis: BioPython, pysam, scikit-bio, BioServices
- Single-cell analysis: Scanpy, AnnData, scvi-tools, scVelo (RNA velocity), Arboreto, Cellxgene Census
- Genomic tools: gget, geniml, gtars, deepTools, FlowIO, Polars-Bio, Zarr, TileDB-VCF
- Differential expression: PyDESeq2
- Phylogenetics: ETE Toolkit, MAFFT, IQ-TREE 2, FastTree

### Cheminformatics & Drug Discovery (10+ skills)
- Molecular manipulation: RDKit, Datamol, Molfeat
- Deep learning: DeepChem, TorchDrug
- Docking & screening: DiffDock
- Molecular dynamics: OpenMM + MDAnalysis
- Cloud quantum chemistry: Rowan
- Drug-likeness: MedChem
- Benchmarks: PyTDC

### Proteomics & Mass Spectrometry (2 skills)
- matchms, pyOpenMS

### Clinical Research & Precision Medicine (8+ skills)
- Database Lookup (ClinicalTrials.gov, ClinVar, ClinPGx, COSMIC, FDA, cBioPortal)
- DepMap (cancer dependency scores, drug sensitivity)
- Imaging Data Commons (NCI radiology & pathology)
- PyHealth, NeuroKit2, Clinical Decision Support
- Clinical Reports, Treatment Plans

### Medical Imaging & Digital Pathology (3 skills)
- pydicom, histolab, PathML

### Neuroscience & Electrophysiology (1 skill)
- Neuropixels-Analysis

### Machine Learning & AI (16+ skills)
- Deep learning: PyTorch Lightning, Transformers, Stable Baselines3, PufferLib
- Classical ML: scikit-learn, scikit-survival, SHAP
- Time series: aeon, TimesFM (Google zero-shot foundation model)
- Bayesian: PyMC
- Optimization: PyMOO
- Graph ML: Torch Geometric
- Dimensionality reduction: UMAP-learn
- Statistical: statsmodels

### Materials Science, Chemistry & Physics (7 skills)
- Materials: Pymatgen
- Metabolic modeling: COBRApy
- Astronomy: Astropy
- Quantum computing: Cirq, PennyLane, Qiskit, QuTiP

### Engineering & Simulation (4 skills)
- MATLAB/Octave, FluidSim, SimPy, SymPy

### Data Analysis & Visualization (16+ skills)
- Matplotlib, Seaborn, Scientific Visualization
- GeoPandas, GeoMaster (remote sensing, GIS, satellite imagery, spatial ML, 500+ examples)
- Dask, Polars, Vaex
- NetworkX
- Document Skills (PDF, DOCX, PPTX, XLSX)
- Infographics (10 types, 8 styles, colorblind-safe)
- Markdown & Mermaid Writing (diagrams as documentation standard)

### Laboratory Automation (4 skills)
- PyLabRobot, Ginkgo Cloud Lab, Protocols.io, Benchling/LabArchives

### Multi-omics & Systems Biology (4+ skills)
- PrimeKG, HypoGeniC, LaminDB, Database Lookup (KEGG, Reactome, STRING)

### Protein Engineering & Design (3 skills)
- ESM, Glycoengineering, Adaptyv

### Scientific Communication (20+ skills)
- Paper Lookup (PubMed, PMC, bioRxiv, medRxiv, arXiv, OpenAlex, Crossref, Semantic Scholar, CORE, Unpaywall)
- BGPT Paper Search (25+ structured fields per paper — methods, results, sample sizes, from full text)
- Literature Review, Scientific Writing, Peer Review
- Open Notebook (self-hosted NotebookLM alternative, 16+ AI providers, podcast generation)
- Parallel Web (synthesized web search with citations)
- Scientific Slides, LaTeX Posters, PPTX Posters
- Scientific Schematics, Markdown & Mermaid Writing
- Infographics, Citation Management
- Generate Image (FLUX.2 Pro, Gemini 3 Pro)

### Scientific Databases & Data Access (6 skills → 100+ databases)
- Database Lookup: 78 public databases (PubChem, ChEMBL, UniProt, PDB, AlphaFold, KEGG, Reactome, STRING, ClinVar, COSMIC, ClinicalTrials.gov, FDA, FRED, USPTO, SEC EDGAR, and more)
- DepMap, Imaging Data Commons, PrimeKG
- U.S. Treasury Fiscal Data
- Hugging Science (curated scientific ML index across 17 scientific domains on HuggingFace)

### Infrastructure & Platforms (7+ skills)
- Modal (cloud compute), GPU Optimization (CuPy, Numba CUDA, cuDF, cuML, cuGraph)
- DNAnexus, LatchBio, OMERO, Opentrons, Get Available Resources

### Research Methodology & Planning (12+ skills)
- Scientific Brainstorming, Hypothesis Generation
- Scientific Critical Thinking, Scholar Evaluation
- What-If Oracle (multi-branch scenario analysis)
- Consciousness Council (diverse expert viewpoints)
- DHDNA Profiler (cognitive pattern extraction)
- Research Grants, Research Lookup, Market Research Reports

### Regulatory & Standards (1 skill)
- ISO 13485 Certification

## Security

- All skills scanned by Cisco AI Defense Skill Scanner (weekly basis)
- SECURITY.md updated with scan results
- Self-scan: `uv pip install cisco-ai-skill-scanner && skill-scanner scan /path/to/skill --use-behavioral`
- Each skill has individual license in SKILL.md (may differ from repo MIT license)

## Topics

agent-skills, ai-scientist, bioinformatics, chemoinformatics, claude, claude-skills, claudecode, clinical-research, computational-biology, data-analysis, drug-discovery, genomics, materials-science, metabolomics, proteomics, scientific-computing, scientific-visualization

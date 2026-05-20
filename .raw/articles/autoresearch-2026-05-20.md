---
source_url: https://github.com/karpathy/autoresearch
fetched: 2026-05-20
---

# karpathy/autoresearch — GitHub README

**Stars:** 82.2k  
**Language:** 83.4% Python, 16.6% Jupyter Notebook  
**Author:** Andrej Karpathy

## Description

Enables autonomous AI agents to conduct machine learning research overnight on a single GPU. The agent independently modifies code, trains models for 5-minute intervals, evaluates improvements, and iterates—allowing researchers to wake up to experimental logs and potentially improved models.

## Core Files

- `prepare.py` — fixed constants, one-time data prep (downloads training data, trains a BPE tokenizer), and runtime utilities. Unmodified.
- `train.py` — the single file the agent edits. Contains the full GPT model, optimizer (Muon + AdamW), and training loop.
- `program.md` — baseline instructions for one agent. Human-edited to guide AI behavior. Functions as "a super lightweight skill."
- `pyproject.toml` — dependencies
- `analysis.ipynb` — analysis notebook

## Installation

1. Install uv: `curl -LsSf https://astral.sh/uv/install.sh | sh`
2. Sync dependencies: `uv sync`
3. Prepare data/tokenizer: `uv run prepare.py` (~2 minutes)
4. Test single experiment: `uv run train.py` (~5 minutes)

## Evaluation Metric

**val_bpb** (validation bits per byte) — lower is better. Vocab-size-independent so architectural changes are fairly compared.

## Experiment Loop Mechanics

- Fixed 5-minute training budget (wall clock, excluding startup)
- ~12 experiments per hour
- ~100 experiments during overnight runs
- Direct comparability across architectural variations

Agent modifies only `train.py`, keeping "the scope manageable and diffs reviewable."

## Agent Usage

User prompts agent: "Hi have a look at program.md and let's kick off a new experiment! let's do the setup first."

## Design Philosophy

"No external dependencies beyond PyTorch and a few small packages. No distributed training, no complex configs. One GPU, one file, one metric."

## Requirements

- Single NVIDIA GPU (H100 tested)
- Python 3.10+
- uv package manager

## Community Forks

Platform adaptations for MacOS, Windows, and AMD GPUs available in the repository.

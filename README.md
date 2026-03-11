# Computational Neuroscience — Thalamus vs Cortex in Visual Processing

This repository contains materials for a computational neuroscience course project analyzing electrophysiology data from the **Allen Brain Observatory** to compare **thalamic** and **cortical** activity during visual processing.

The project’s core question is:

> **How does thalamic activity compare to cortical activity when processing visual input?**

## Project summary

Using Allen Brain Observatory ecephys recordings, we compare units from thalamic nuclei (e.g., **LGd, LP, PO**) to units in visual cortical areas (e.g., **VISp, VISl, VISal, VISpm, VISam, VISrl**) and analyze firing-rate/spike-count differences across visual stimuli (with emphasis on **natural scenes**).

## Repo layout

- **`notebooks/`** — Jupyter notebooks (AllenSDK walkthrough + analysis)
- **`guidelines/`** — course/project guideline documents (PDFs)
- **`report.pdf`** — final short report summarizing methods and results
- **`requirements.txt`** — pinned Python dependencies for reproducible installs
- **`.gitignore`** — ignores AllenSDK cache/download folders (e.g. `allendata/`) and other local artifacts

## Key methods

The analysis pipeline (implemented in a Jupyter notebook) includes:
- Loading an ecephys session with many recorded units across thalamus + cortex
- Separating units by structure acronyms (thalamic vs cortical)
- Comparing:
  - spike count distributions
  - firing rate distributions / mean firing rates
  - temporal response profiles
- Statistical testing (e.g., two-sample tests) and simple decoding:
  - **PCA** (dimensionality reduction)
  - **Logistic regression** classification

### Data download / caching

The notebooks use the AllenSDK cache pattern (creating a local data directory + `manifest.json`).
By default they write to `./allendata/` (gitignored). The first run may download a non-trivial amount of data.

## Results (high level)

A few headline findings from the report:
- Thalamic units showed **higher mean firing rates** than cortical units (example reported means: **9.38 Hz vs 6.44 Hz**, **p < 0.001**).
- A firing-rate–based logistic regression classifier separated thalamus vs cortex only **moderately** (reported accuracy ~**59%**).
- PCA showed partial separation but substantial overlap between populations.

See the included report for details, figures, and discussion.

## Getting started

### Requirements

Recommended:
- Python 3.10+ (3.11 works in many environments)
- Jupyter (Lab or Notebook)

### Install

```bash
python -m venv .venv
source .venv/bin/activate  # (Windows: .venv\Scripts\activate)
pip install --upgrade pip

pip install -r requirements.txt
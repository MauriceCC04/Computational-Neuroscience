# Computational Neuroscience — Thalamus vs Cortex in Visual Processing

This repository contains materials for a computational neuroscience course project analyzing electrophysiology data from the **Allen Brain Observatory** to compare **thalamic** and **cortical** activity during visual processing.

The project’s core question is:

> **How does thalamic activity compare to cortical activity when processing visual input?**

## Project summary

Using Allen Brain Observatory ecephys recordings, we compare units from thalamic nuclei (e.g., **LGd, LP, PO**) to units in visual cortical areas (e.g., **VISp, VISl, VISal, VISpm, VISam, VISrl**) and analyze firing-rate/spike-count differences across visual stimuli (with emphasis on **natural scenes**).
## What’s in this repo

> File/folder names may vary slightly depending on your latest cleanup/re-org.

Typical contents:
- **`notebooks/`** — Jupyter notebooks used for the analysis (main analysis + validation/extra experiments).
- **`guidelines/`** — course/project guideline documents (PDFs).
- **`report.pdf`** (or similar) — final short report summarizing methods and results.

## Key methods

The analysis pipeline (implemented in a Jupyter notebook) includes
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

The notebook uses the AllenSDK cache pattern (e.g., creating a local data directory and manifest).
Expect the first run to download a non-trivial amount of data.

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

Key packages used in the notebook include
- `allensdk`
- `numpy`, `pandas`
- `matplotlib` (and/or `seaborn`)
- `scipy`
- `scikit-learn`

### Install (example)

```bash
python -m venv .venv
source .venv/bin/activate  # (Windows: .venv\Scripts\activate)
pip install --upgrade pip

pip install allensdk numpy pandas matplotlib seaborn scipy scikit-learn jupyterlab
````

### Run the notebooks

```bash
jupyter lab
```

Open the main analysis notebook in `notebooks/` and run cells top-to-bottom.
On first run, allow time for AllenSDK data downloads and caching.

## Notes / tips

* If you rerun often, keep the cached AllenSDK data directory to avoid repeated downloads .
* Results can vary slightly across package versions and due to stochastic steps (if any). If you want strict reproducibility, pin versions in a `requirements.txt`.

## Acknowledgements

This work uses data and tooling from the **Allen Brain Observatory** via the **AllenSDK** .

If you want, I can also propose a simple `requirements.txt` and a `.gitignore` tailored for AllenSDK caches (so you don’t accidentally commit downloaded datasets).

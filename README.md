# WDRO-MOR

Code and study outputs for the paper *"Wasserstein Distributionally Robust
Multi-Objective UAV Routing with Finite-Sample Pareto Coverage Certificates."*

- **`WDRO_MOR_experiment.ipynb`** — the experiment notebook: runs the study end to
  end (dataset → WDRO certificate → ε\* calibration → campaign → Phase C/E/F →
  figures → deployment), with the result tables and figures shown inline.
- **`code/`** — the pipeline modules the notebook imports.
- **`figures/`**, **`cache/consolidated/`** — the figures and consolidated output tables from
  the study.

## Reproduce

1. Download the dataset from Zenodo: **https://doi.org/10.5281/zenodo.20985360**
   Unzip it so `dataset/derived/` and `dataset/data/` sit next to the notebook.
2. `pip install -r requirements.txt`  (Python 3.11, CPU-only).
3. Run `WDRO_MOR_experiment.ipynb` top to bottom. The full campaign (6 zones × 7
   methods × 31 seeds) is checkpointed and resumable and takes a few hours; the
   embedded outputs already show every result.

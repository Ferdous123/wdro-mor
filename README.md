# WDRO-MOR

Code, figures and consolidated results for Wasserstein distributionally robust
multi-objective UAV routing under weather uncertainty.

**Paper:** *Wasserstein Distributionally Robust Multi-Objective UAV Routing.*
In preparation, target venue PLOS ONE.

## The study

The experiment covers six climate zones (Dhaka, New York City, Manaus, In Salah,
La Paz and Tromsø) on ERA5 data for 2023–2025. Each zone is routed on a 3-D
waypoint lattice, and the WDRO method is compared against six baselines
(`saa_cvar`, `saa_cvar_tuned`, `robust_box`, `kl_drcc`, `ws`, `rs`) over 31 seeds,
for 1,302 runs in total. A reanalysis-to-forecast transfer study uses HRES/IFS
forecasts.

## What is in the repository

| Path | Contents |
|---|---|
| `WDRO_MOR_experiment.ipynb` | The experiment notebook. It runs the study end to end and shows every result table and figure inline. |
| `code/` | The pipeline modules the notebook imports (graph, WDRO certificate, ε\* calibration, campaign, evaluation, frontier, tuned baseline, sensitivity, forecast transfer, figures, deployment router). |
| `cache/consolidated/` | Consolidated output tables. `summary.txt` lists ε\* and coverage per zone and method. |
| `figures/` | The study figures as PDF and PNG. |
| `requirements.txt` | Python dependencies. |

The notebook sections run in this order: dataset, zone graph, WDRO certificate,
ε\* calibration, campaign and consolidation, Phase C (minimum-ε\* floor),
coverage–efficiency frontier, tuned baseline, Phase E (hyperparameter
sensitivity), Phase F (reanalysis-to-forecast transfer), smoke test, figures and
deployment routing for any origin–destination pair.

## Setup

Python 3.11, CPU only.

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Reproduce

1. Download the dataset from Zenodo: <https://doi.org/10.5281/zenodo.20985360>.
   Unzip it so that `dataset/derived/` and `dataset/data/` sit next to the notebook.
2. Run `WDRO_MOR_experiment.ipynb` from top to bottom.

The full campaign (6 zones × 7 methods × 31 seeds) is checkpointed and resumable
and takes a few hours. The outputs stored in the notebook already show every
result, so it can be read without running anything.

## Data

The dataset is published on Zenodo as *WDRO-MOR: Altitude-Resolved ERA5/HRES
Environment Dataset* (version 1.0.0) under CC BY 4.0. Per zone and year it
combines ERA5 reanalysis, air quality, convective indices, OpenStreetMap,
WorldPop and NASA POWER layers, and adds HRES/IFS forecasts for the transfer
study. ERA5 and HRES are © ECMWF / Copernicus Climate Change Service, and their
use is governed by the Copernicus licence.

## License

The code is released under the MIT License. See [`LICENSE`](LICENSE).

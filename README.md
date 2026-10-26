# NBA Game Analysis using Kalshi Prediction Market & NBA API Data (Milestone 2)

**Team Members:** Brad Hofmeister, Chris Halvonik, Ryan McCurry

## Overview

This project tests whether traditional NBA statistics add predictive value beyond Kalshi prediction-market prices, and whether that changes as a game progresses. It combines team box scores from the NBA stats API with Kalshi market prices for every 2025–26 regular-season game at four checkpoints: pre-game and the end of quarters 1, 2, and 3.

- **Supervised learning:** compares NBA-only, Kalshi-only, and combined feature sets across logistic regression, random forest, and k-nearest neighbors, evaluated against the raw Kalshi price with time-series cross-validation, a held-out test set, and paired bootstrap significance tests.
- **Unsupervised learning:** clusters games and markets, then compares Kalshi's accuracy and calibration across clusters.

**Team:** Brad Hofmeister, Chris Halvonik, Ryan McCurry

## Repository Structure

```
Milestone2/
├── data/
│   ├── raw/               # CSVs produced by notebooks 01 and 02
│   └── processed/         # Modeling tables produced by notebook 03
├── notebooks/             # Run in numbered order (see below)
├── visualizations/        # Figures used in the report
├── requirements.txt       # Python dependencies (pinned versions)
└── .gitignore
```

## Notebooks

The notebooks are numbered in the order they run. Each one reads the previous step's output from `data/`.

| Notebook | What it does | Reads | Writes |
|---|---|---|---|
| `01_nba_stats_data.ipynb` | Pulls full-game, rolling-average, and end-of-quarter team box scores from the NBA stats API | NBA stats API | `data/raw/` |
| `02_kalshi_data.ipynb` | Pulls quarter start times and Kalshi market prices at each checkpoint | `data/raw/`, NBA stats API, Kalshi API | `data/raw/` |
| `03_data_prep.ipynb` | Checks the raw data, builds home-minus-away features, assigns a chronological train/test split, and exports one table per checkpoint | `data/raw/` | `data/processed/`, figures 01–03 |
| `04_supervised_section.ipynb` | Trains, tunes, and evaluates the supervised models, with significance tests, ablation, sensitivity, and failure analysis | `data/processed/` | figures 04–06 |
| `05_unsupervised_section.ipynb` | Clusters games and compares Kalshi's performance across clusters | `data/processed/` (from GitHub) | figures 07–13 |

**You don't need to run notebooks 01 and 02.** The raw data they produce is already in `data/raw/`, and re-collecting it makes thousands of API requests and takes several hours. To reproduce the analysis, start at notebook 03.

## Getting Started

Tested with Python 3.9.

**1. Clone the repository**

```bash
git clone https://github.com/brad-hof/Milestone2.git
cd Milestone2
```

**2. Create and activate a virtual environment**

```bash
python -m venv .venv
```

macOS/Linux:

```bash
source .venv/bin/activate
```

Windows:

```bash
.venv\Scripts\activate
```

**3. Install dependencies**

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Each notebook also has an install cell at the top (`%pip install -q -r ../requirements.txt`), so this step is optional if you run them in Jupyter. Restart the kernel after the first install.

**4. Run the notebooks**

Open the notebooks in Jupyter (`jupyter notebook`) or VS Code, select the `.venv` kernel, and run them in order starting from `03_data_prep.ipynb`. The notebooks use paths relative to the `notebooks/` folder (for example `../data/processed`), so open them from there rather than moving them.
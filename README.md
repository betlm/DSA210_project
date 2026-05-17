# The Economic Aftershocks: Analyzing the Impact of Major Earthquakes on National Recovery

**Author:** Betül Merey — 33963  
**Course:** DSA 210 — Introduction to Data Science  
**Institution:** Sabancı University  
**Repository:** https://github.com/betlm/DSA210_project

---

## Overview

This project investigates how major earthquakes affect national economies and whether a country's pre-existing wealth determines its recovery speed. Using earthquake event data from EM-DAT, macroeconomic indicators from the World Bank API, and seismic data from USGS, the analysis tests whether earthquake intensity or a nation's underlying economic resilience is the dominant factor in recovery.

---

## Research Questions

- Does earthquake magnitude significantly correlate with economic damage?
- Does a country's income level determine its relative economic vulnerability?
- Can we predict economic recovery time using machine learning, and do ensemble methods outperform linear models?

---

## Hypotheses & Results

| Hypothesis | Test | Result |
|---|---|---|
| **H1:** Higher magnitude → greater economic damage | Spearman correlation | ✅ Supported (ρ=0.164, p=0.007) |
| **H2:** Lower income → higher relative damage | Kruskal-Wallis + Mann-Whitney U | ✅ Supported (p=0.021) |
| **H3:** Non-linear relationship → Random Forest beats Logistic Regression | Stratified 5-fold CV + Wilcoxon | ✅ Supported (p=0.031) |

**Key finding:** Recovery time depends more on the kind of economy the earthquake hits than on how strong the earthquake is. Pre-event GDP growth trend (34%), unemployment (20%), and GDP per capita (19%) are the dominant predictors — magnitude accounts for only 10%.

---

## Data Sources

| Source | Description | Records |
|---|---|---|
| [EM-DAT](https://www.emdat.be/) | Earthquake events, casualties, damage (1990–2026) | 959 events, 110 countries |
| [World Bank API](https://data.worldbank.org/) | GDP growth, GDP per capita, unemployment | 3 indicators, 258 countries |
| [USGS](https://earthquake.usgs.gov/) | Earthquake catalog with depth and magnitude | 14,447 events since 1900 |

---

## Project Structure

```
DSA210_project/
│
├── data/
│   ├── raw/
│   │   ├── emdat/
│   │   │   └── emdat_data.xlsx
│   │   └── usgs/
│   │       └── usgs_1900.csv
│   └── processed/
│       └── merged_dataset.csv
│
├── 02_EDA/
│   ├── outputs/figures/
│   │   ├── 01EDA_magnitude_distribution.png
│   │   ├── 02EDA_damage_distribution.png
│   │   ├── 03EDA_damage_ratio_by_income.png
│   │   ├── 04EDA_gdp_per_capita.png
│   │   ├── 05EDA_correlation_heatmap.png
│   │   ├── 06EDA_events_over_time.png
│   │   └── 07EDA_top15_damaging_events.png
│   └── 02_EDA.ipynb
│
├── 03_hypothesis_testing/
│   ├── hypothesis/
│   │   ├── H1/
│   │   │   ├── H1_plot.png
│   │   │   └── H1_results.txt
│   │   ├── H2/
│   │   │   ├── H2_plot.png
│   │   │   └── H2_results.txt
│   │   └── H3/
│   │       ├── H3_plot.png
│   │       ├── H3_confusion_matrix.png
│   │       └── H3_results.csv
│   ├── results/
│   │   └── hypothesis_testing_results.csv
│   └── 03_hypothesis_testing.ipynb
│
├── 04_machine_learning/
│   ├── outputs/
│   │   ├── feature_importance.png
│   │   ├── feature_importance.csv
│   │   ├── confusion_matrix.png
│   │   ├── model_comparison.png
│   │   └── ml_results.csv
│   └── 04_machine_learning.ipynb
│
├── 01_data_merging.ipynb
├── DSA 210 Project Proposal.pdf
├── requirements.txt
└── README.md
```

---

## How to Reproduce

**1. Clone the repository:**
```bash
git clone https://github.com/betlm/DSA210_project.git
cd DSA210_project
```

**2. Install dependencies:**
```bash
pip install -r requirements.txt
```

**3. Run notebooks in order:**

| Step | Notebook | Description |
|---|---|---|
| 1 | `01_data_merging.ipynb` | Merge EM-DAT + World Bank + USGS into one dataset |
| 2 | `02_EDA/02_EDA.ipynb` | Exploratory data analysis and visualizations |
| 3 | `03_hypothesis_testing/03_hypothesis_testing.ipynb` | H1 and H2 statistical tests |
| 4 | `04_machine_learning/04_machine_learning.ipynb` | H3 machine learning classification |

> **Note:** Notebooks require Google Colab with Google Drive mounted. World Bank API calls in Step 1 may take 2–3 minutes.

---

## Requirements

```
pandas
numpy
matplotlib
seaborn
scipy
scikit-learn
```

---

## AI Usage Disclosure

AI assistance (Claude by Anthropic) was used in this project for:
- Debugging a pandas index misalignment bug that caused 959 phantom rows in the merged dataset
- Identifying target leakage between `gdp_drop` and `recovery_years`
- Code suggestions for API fetch logic, scipy statistical tests, and sklearn pipelines
- Writing assistance for markdown documentation

All analytical decisions — hypothesis design, variable selection, test interpretation, and conclusions — were made by the author.

---

*DSA 210 — Sabancı University, Spring 2025*

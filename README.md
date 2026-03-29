# The economic Aftershocks: Analyzing the Impact of Major Earthquakes on National Recovery
 
**Betül Merey — 33963**  
**DSA 210 Project Proposal**
 
> **Research Question:** Does the magnitude of an earthquake or the pre-existing economic status of a nation more significantly determine the duration of economic recovery?
 
---
 
## Overview
 
This project investigates the long-term economic consequences of major earthquakes and examines how different nations recover from these shocks. While seismic activity causes immediate physical destruction, the "recovery duration"—the time it takes for a country's economy to return to pre-disaster levels—varies significantly across different income groups.
 
Rather than analyzing localized damage, this study is conducted at the national level by merging seismic data with macroeconomic indicators. The goal is to identify whether recovery speed is driven primarily by the physical intensity of the earthquake or by the underlying economic resilience of the affected country.
 
---
 
## Terminology
 
| Term | Definition |
|------|------------|
| **Magnitude (M)** | A logarithmic scale representing the energy released by an earthquake, sourced from USGS. |
| **Depth** | The distance from the earth's surface to the point where the earthquake originated. |
| **GDP Growth Rate (Annual %)** | The yearly percentage increase or decrease in a country's economic output. |
| **Income Group** | Classification of countries (Low, Middle, High) based on World Bank criteria. |
| **Recovery Duration** | A calculated metric representing the number of years required for a country's GDP growth to return to its 5-year pre-earthquake average. |
 
---
 
## Motivation
 
Natural disasters, particularly major earthquakes, cause immediate physical destruction and long-term economic instability. As a student living in Turkey, a country deeply affected by seismic activity, I am motivated to understand the quantitative relationship between earthquake characteristics and economic resilience. I want to investigate whether the speed of economic recovery is determined primarily by the magnitude of the disaster or the pre-existing economic strength of the nation.
 
---
 
## Research Questions
 
1. How does the earthquake magnitude correlate with the immediate drop in a country's GDP growth rate?
2. Does a country's income level (Low, Middle, High) significantly influence the duration of economic recovery?
3. Can we predict the "Economic Recovery Time" by comparing different machine learning models?
 
---
 
## Hypotheses
 
- **H₀ (Null Hypothesis):** There is no significant difference in economic recovery time between different income groups or earthquake magnitudes.
- **H₁:** Higher earthquake magnitudes are correlated with a significant immediate drop in annual GDP growth.
- **H₂:** Higher-income countries have a significantly shorter "Recovery Duration" compared to lower-income countries for similar seismic events.
- **H₃:** A non-linear relationship exists between earthquake impact and economic indicators, which can be modeled more accurately using ensemble learning (Random Forest) than linear methods.
 
---
 
## Data Sources
 
### 1. Primary Seismic Dataset — USGS (U.S. Geological Survey)
- Provides precise seismic data for events from **1990 to the present** with **M ≥ 6.0**.
- **Features:** Magnitude, Depth, Latitude/Longitude, Exact Timestamp.
 
### 2. Impact Dataset — EM-DAT (The International Disaster Database)
- Supplies data on the human and economic impact of specific disaster events.
- **Features:** Country, Total Damage (USD), Total Deaths.
 
### 3. Secondary Economic Dataset — World Bank Open Data
- Annual economic indicators collected using Python-based techniques.
- **Features:** GDP growth (annual %), GDP per capita, Income Group.
 
---
 
## Data Preparation
 
The datasets will be merged by **Country** and **Year** to enrich the analysis. The primary seismic data from USGS will be filtered for events since 1990 with a magnitude of 6.0 or higher. After collection, the datasets will be:
 
- Cleaned and standardized for currency inflation.
- Merged to create a unified panel dataset.
- Enriched with an engineered **"Recovery Duration"** feature.
 
The final dataset is expected to contain approximately **3,500+ earthquake events** and **10–12 statistical features** per sample.
 
---
 
## Analysis Plan
 
The project will include:
 
- **Time-series analysis** of GDP trajectories before and after seismic shocks.
- **Trend visualizations** comparing recovery curves across different income groups.
- **Non-parametric Hypothesis Testing:** Using Mann-Whitney U (for binary comparisons) or Kruskal-Wallis tests to evaluate the significance of recovery differences across income levels.
- **Machine Learning Comparison:** Both Linear Regression and Random Forest Regressor will be implemented to predict economic recovery time. These models will be compared based on **RMSE** and **R²** to identify the most effective predictive approach.
 
---
 
## Expected Outcome
 
This project is expected to show that while higher earthquake magnitude increases immediate damage, **a country's pre-existing economic income level is a dominant factor** in determining the speed of recovery. The Random Forest model is expected to outperform Linear Regression in capturing the complex, non-linear dependencies between disaster intensity and national economic resilience.

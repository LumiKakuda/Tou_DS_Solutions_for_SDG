# Tou_DS_Solutions_for_SDG

This repository was developed for the capstone project of the **"Data Science Solutions for the SDGs"** challenge. It builds machine learning model to forecast how climate change will affect the habitat of the **American pika** (*Ochotona princeps*), a small alpine mammal that is highly sensitive to heat and is often used as an early-warning indicator for climate-driven habitat loss.

Presence/absence records and climatic/topographic predictors are used to train a classifier (Random Forest, selected over XGBoost and LightGBM), which is then used to project habitat suitability to ~2050 under two IPCC emissions scenarios (mild and extreme scenario).

## Main product: `Web UI/`

The main deliverable of this project is **PikaWatch**, a single-page interactive website (`Web UI/index.html` + `styles.css`):

- The conservation problem (who the pika is, why it's climate-sensitive, the SDG angle) and the research questions driving the project.
- A full walkthrough of the data pipeline: data collection → EDA → data cleaning and feature selection (SHAP-driven) → model training/comparison → evaluation.
- A 2050 scenario toggle comparing **observed** occurrences against **mild (SSP2-4.5)** and **extreme (SSP5-8.5)** warming projections, with summary stats per scenario.
- Model limitations and a references section.

## Repository contents
 
### Root
 
| File | Description |
|---|---|
| `.gitignore` | Standard Python gitignore (caches, virtual envs, Jupyter checkpoints, IDE files, etc.). |
| `.DS_Store` | macOS Finder metadata file — not part of the project. |
 
### `Reports/`
 
| File | Description |
|---|---|
| `Data Sources.pdf` | Documents the datasets used to build the training data|
| `Data Collection and preprocessing.pdf` | Explains how presence and absence occurrence records were compiled and how climatic and topographic variables were attached to each record. |
| `Forecasting Climate Change Impacts on the Habitat of the American Pika (1).pdf` | The written capstone report: introduction, SDM approach, methodology and results summary, and references — the narrative counterpart to the Web UI. |
| `Future_Projections.pdf` | Explains how the ~2050 climate inputs were produced for the mild (SSP2-4.5) and extreme (SSP5-8.5) scenarios used in the future-projection feature. |
 
### `Reports/EDA/`
 
| File | Description |
|---|---|
| `pika_presence_absence_EDA.ipynb` | Main exploratory analysis notebook. Covers schema comparison, missing data, duplicates/record provenance, the presence/absence class imbalance, temporal and spatial distribution, univariate/bivariate analysis of the bioclimatic, snow, and drought (PDSI) variables, correlation structure, outlier detection, and a summary of key findings. |
| `pika_regional_EDA_absence_area.ipynb` | Follow-up notebook that restricts presence records to the absence dataset's geographic bounding box, to remove a range-mismatch confound.|
| `presence_pika_final_with_extraTPDSIandSnow.csv` | Presence dataset (~17,949 records): coordinates, year, status, elevation/slope/patch size, and the full set of bioclimatic, temperature, drought (PDSI), and snow predictors. |
| `absence_pika_final_with_extraTPDSIandSnow.csv` | Absence dataset (225 records) with the same climatic/topographic schema, used as the negative class for training. |
 
### `Web UI/` (main product)
 
| File | Description |
|---|---|
| `index.html` | The "PikaWatch" site itself — see the main product description above. |
| `styles.css` | The site's design system: color/typography tokens, hero and section layouts, the interactive map and scenario-toggle styling, accessibility-mode overrides, and responsive rules. |
| `images/` | Chart and figure assets embedded throughout the site. |
| `.DS_Store` | macOS Finder metadata file — not part of the project. |
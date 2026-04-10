# Gender Gap in ASD Diagnosis

A global-scale data analysis covering 194 countries to quantify the gender gap in Autism Spectrum Disorder (ASD) diagnosis. This project examines the age of diagnosis, reported prevalence, and access to therapies, cross-referenced with socioeconomic indicators per country.

## Key Features

* Data Consolidation: Builds a unified dataset from diverse public sources (GBD/IHME, Our World in Data, WHO Atlas, World Bank, UNDP).

* DDistribution Analysis: Analyzes the diagnosis gap across different genders and geographic regions.

* DCorrelation Mapping: Identifies links between the gender gap and variables such as the Gender Inequality Index (GII), GDP, and mental health spending.

* DPredictive Modeling: Trains regression models to predict the age of diagnosis in women.

* DRisk Classification: Classifies countries based on the probability of late diagnosis (binary variable).

* DClustering: Segments countries into four distinct "diagnostic inequity profiles" using K-Means.

* DAutomated Visualization: Generates exportable charts directly to the outputs/ directory.

## Project Structure

```
tfm-autism-gender-gap/
├── autism_gender_gap.ipynb   # pipeline completo: EDA, modelos, clustering
├── requirements.txt
└── README.md
```

## Installation & Usage

```bash
pip install -r requirements.txt
jupyter notebook autism_gender_gap.ipynb
```

Note: The notebook automatically creates an outputs/ folder to store all generated visualizations.

## Primary Dataset Variables

* `age_gap` — Difference in age of diagnosis (Women − Men, in years).
* `diagnosis_gap` — Difference in reported prevalence (Men − Women, per 100k).
* `gii` — Gender Inequality Index (PNUD)
* `mental_health_exp` — Mental health expenditure as a % of total health spending (WHO).
* `late_diagnosis` — Binary variable (1 if age_gap exceeds the 75th percentile).
  
## Applied Models

* Regression: Ridge, Random Forest.
* Classification: Logistic Regression, Random Forest (Target AUC-ROC: 0.89).
* Clustering: K-Means ($K=4$) validated by Silhouette Score and the Elbow Method.
* Explainability: Feature importance via Random Forest and SHAP values included in the full pipeline.

## Data Sources

* GBD Study — IHME: ASD prevalence by country and gender.
* Our World in Data: Autism research datasets.
* WHO Mental Health Atlas 2020: Global mental health infrastructure.
* World Bank: World Development Indicators
* UNDP: Human Development Reports.

## Tech Stack

Python · Pandas · Numpy · Scikit-learn · Matplotlib · Seaborn

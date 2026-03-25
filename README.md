# Harris County Motivated Seller Model

## Overview
This project builds a machine learning pipeline to identify residential properties that may be associated with motivated sellers using public data sources in Harris County, Texas.

The goal is to move beyond static lead lists and instead generate **data-driven, ranked acquisition opportunities** for real estate investors.



## Business Problem
Real estate acquisition teams typically rely on:
- Static tax delinquency lists
- Manual prospecting
- Limited visibility into early distress signals

This project aims to improve targeting by predicting which properties are more likely to exhibit **distress-related sale behavior**.



## Data Sources
- Harris County Appraisal District (HCAD)
- Deed transfer records
- Tax delinquency indicators
- Lien records
- 311 service request data
- Probate filings
- Civil court filings



## Data Pipeline (Architecture)
Raw Files → DuckDB Warehouse → Feature Tables → ML Model → Scored Output

- Raw public data ingested into DuckDB
- Cleaned and standardized into structured tables
- Feature engineering applied across multiple sources
- Model outputs property-level probability scores



## Feature Engineering
Key feature groups include:
- Ownership tenure
- Absentee ownership indicators
- 311 complaint frequency and severity
- Property valuation and structure features



## Modeling
- Random Forest predicting current property tax delinquency (baseline model)
- Logistic Regression (planned comparison)



## Evaluation
Due to heavy class imbalance (~3% positive cases), evaluation focuses on:

- ROC-AUC
- Precision / Recall
- F1 Score
- Predicted probabilities for ranking



## Preliminary Results
Initial Random Forest model achieved:
- ROC-AUC ≈ 0.83
- Strong separation in an imbalanced dataset



## Repository Structure
notebooks/
├── 01_data_understanding.ipynb
├── 02_feature_engineering.ipynb
├── 03_modeling_random_forest.ipynb
└── 04_model_evaluation.ipynb


## How to Run
1. Load raw data into local environment (not included in repo)
2. Run feature engineering notebook
3. Train model
4. Generate prediction scores



## Important Note
Raw datasets and DuckDB files are not included due to:
- Data size
- Privacy considerations

This repository focuses on **methodology, modeling, and reproducibility**.


## Key Challenges
- Severe class imbalance (only 3% of properties are currently tax delinquent)
- Multi-source data integration
- Entity resolution (matching records across datasets)



## Next Steps
- Expand ownership-history modeling
- Improve deed-to-property matching
- Add additional target variables (e.g., distressed sale pricing)
- Deploy pipeline to Azure
- Build front-end application for property scoring



## Future Vision
This project is intended to evolve into a **production-grade real estate analytics platform** combining:
- Predictive modeling
- Data pipelines
- User-facing application
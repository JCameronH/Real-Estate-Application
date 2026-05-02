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
- Ownership snapshot windows by calendar year
- 311(city code violation) complaint frequency and severity
- Civil Court Filing timelines and types of court filings
- Probate timeilne



## Modeling
- Random Forest predicting motivated seller
- Logistic Regression (initial baseline model)



## Evaluation
Due to heavy class imbalance (a motivated seller is not a common event), evaluation focuses on:

- ROC-AUC
- Precision / Recall
- F1 Score
- Predicted probabilities for ranking



## Preliminary Results
Initial Random Forest model achieved (note, baseline seller rate is 9.5%):
- ROC-AUC ≈ 0.543849411914147
- Precision: .08
- Recall: .68
- F1: .14




## Repository Structure
notebooks/



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
- Severe class imbalance with Target variable of motivated seller, rare probate events 760 events out of 1,048,00 properties.
- Multi-source data integration from governmental sources
- Entity resolution (matching records across datasets)



## Next Steps
- Expand ownership-history modeling
- Add additional target variables (e.g., distressed sale pricing, need access to Multiple Listings Site)
- Deploy pipeline to Azure
- Data goes back to 2015 - need to source more historical data. This may help with imbalances.
- Build front-end application for property scoring



## Future Vision
This project is intended to evolve into a **production-grade real estate analytics platform** combining:
- Predictive modeling
- Data pipelines
- User-facing application

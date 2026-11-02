# IDX-Exchange-Data-Science
Data Science Internship Project | IDX Exchange
# California Home Price Prediction
## IDX Exchange — Data Science Internship

**Author:** Hind Mhaouer

## Project Overview

This project develops and evaluates machine learning models to predict California single-family home sale prices using historical MLS data provided through the IDX Exchange internship.

The target variable is `ClosePrice`. The workflow includes exploratory analysis, data preprocessing, chronological validation, model comparison, and feature engineering.

This repository documents the Data Science track. Data Analyst deliverables are maintained separately.

## Data and Scope

| Item | Description |
|---|---|
| Source | CRMLS sold-property files supplied through IDX Exchange |
| Available archive | January 2024–September 2026 |
| Property type | `Residential` |
| Property subtype | `SingleFamilyResidence` |
| Prediction target | `ClosePrice` |
| Final test period | Most recent available month |
| Training period | Consecutive months immediately preceding the test period; window length evaluated through validation |

The Residential sold dataset prepared upstream contains 495,291 records before duplicate removal and the additional single-family modeling filter. This is not the final modeling sample size.

Final sample sizes and exclusions will be recorded in the preprocessing notebook.

## Main Fields

| Field | Purpose |
|---|---|
| `ClosePrice` | Sale price to predict |
| `LivingArea` | Recorded interior living area |
| `BedroomsTotal` | Number of bedrooms |
| `BathroomsTotalInteger` | Bathroom count |
| `LotSizeSquareFeet` | Recorded lot area |
| `YearBuilt` | Construction year |
| `City`, `CountyOrParish` | Geographic context |
| `Latitude`, `Longitude` | Geographic validation and spatial features |
| `CloseDate` | Chronological dataset splitting |

Additional fields are considered only after checking their meaning, coverage, and availability at the intended prediction time.

## Data Preparation

The modeling workflow will:

1. Retain Residential single-family records.
2. Review missing values, duplicate records, and quality flags.
3. Exclude missing, nonfinite, or nonpositive target prices.
4. Document how invalid feature values are handled.
5. Encode categorical variables and impute features when appropriate.
6. Apply scaling when required by the modeling approach.
7. Fit preprocessing transformations using training data only.

Flagged records are not automatically excluded from every analysis. Each exclusion or transformation must have a documented reason.

## Validation Strategy

The latest available month is reserved for final testing.

Training-window length is treated as a tunable choice. Candidate windows are compared using earlier chronological validation periods. The final test month is not used to select the window, features, or hyperparameters.

Features derived from the target or information unavailable at prediction time are excluded to reduce data leakage.

## Internship Roadmap

| Week | Focus | Planned deliverable |
|---|---|---|
| 1 | Dataset access, setup, and feature definitions | Access confirmation and column notes |
| 2 | Exploratory data analysis | `01_exploration.ipynb` |
| 3 | Preprocessing and chronological splitting | `02_preprocessing.ipynb` and prepared data |
| 4 | Linear Regression baseline | `03_baseline_model.ipynb` |
| 5 | Decision Tree and Random Forest comparison | `04_model_comparison.ipynb` |
| 6 | Feature engineering and school-district spatial features | Updated notebook and feature comparison |
| 7 | Gradient Boosting and light hyperparameter tuning | `05_advanced_models.ipynb` |
| 8 | Expanded evaluation and price-band analysis | `06_evaluation.ipynb` and `metrics_summary.csv` |
| 9 | Optional prediction application | `app.py` |
| 10 | Reproducibility and documentation | Updated README |
| 11 | Presentation of methods, findings, and limitations | Presentation slides |

This table describes the project plan, not completion status. Week 12 requirements will be added when provided.

## Models and Evaluation

Models considered:

- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor
- Gradient Boosting, such as XGBoost or LightGBM

Evaluation includes:

- **R²:** performance relative to predicting the test-set mean.
- **MAPE:** mean absolute percentage error.
- **MdAPE:** median absolute percentage error.

Percentage-error metrics require positive target prices. Results will also be examined across price bands.

## Results

Verified results from the updated modeling dataset will be added after rerunning the notebooks.

Each comparison will document:

- Training, validation, and test periods.
- Training-window length.
- Record counts and exclusions.
- Feature set and preprocessing.
- Model settings and evaluation metrics.

## Running the Project

1. Obtain authorized access to the internship data.
2. Open the notebooks in Jupyter or Google Colab.
3. Update input paths to match your data location.
4. Run notebooks in numerical order.
5. Run cells from top to bottom and review validation outputs.

Required packages and environment versions will be documented alongside the finalized notebooks.

## Limitations

MLS records may contain missing values, inconsistent dates, questionable measurements, and extreme prices. Model performance may vary by geography, price range, and market period.

Predictions are intended for educational analysis and are not professional property appraisals.

## Data Access

Raw MLS data and confidential internship resources are not included in this repository. Only materials permitted for sharing should be published.

# Predicting 30-Day Hospital Readmission in Diabetes Patients

## Project Overview

Hospital readmissions are an important quality-of-care and cost metric. Early identification of patients at high risk of readmission can support targeted interventions, improve patient outcomes, and reduce healthcare costs.

This project develops an end-to-end machine learning pipeline to predict **30-day hospital readmission** using the UCI Diabetes 130-US hospitals dataset. The workflow includes data cleaning, exploratory data analysis (EDA), feature engineering, predictive modeling, model evaluation, and an initial causal inference analysis.

---

## Objectives

- Explore factors associated with 30-day hospital readmission.
- Build and compare multiple machine learning models.
- Evaluate model performance using metrics appropriate for imbalanced classification.
- Interpret important predictors of readmission.
- Investigate potential causal relationships using propensity score methods.

---

## Dataset

**Source**

- UCI Machine Learning Repository
- Diabetes 130-US hospitals for years 1999–2008

The dataset contains over 100,000 hospital encounters for patients with diabetes across 130 U.S. hospitals.

Target variable:

- Readmitted within 30 days (`readmitted_30d`)

---

## Project Structure

```
├── 01_EDA.ipynb
├── 02_Feature_Engineering_Modeling.ipynb
├── 03_Causal_Inference.ipynb
├── data/
├── figures/
└── README.md
```

---

## Exploratory Data Analysis

The EDA includes:

- Data cleaning and preprocessing
- Missing value analysis
- Distribution of demographic variables
- Readmission rate analysis
- Healthcare utilization analysis
- Medication analysis
- Correlation analysis
- Visualizations of important clinical variables

---

## Feature Engineering

Key engineered features include:

- Prior healthcare utilization
- Diagnosis count
- Age midpoint
- Medication counts
- Binary encoding of readmission
- Group-based train/test split using patient identifiers to prevent patient-level data leakage

---

## Predictive Modeling

The following models were evaluated:

- Baseline classifier
- Logistic Regression
- Decision Tree
- Random Forest

Performance was evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC AUC
- Average Precision
- Precision-Recall Curve
- ROC Curve

---

## Results

### Baseline

Although the baseline classifier achieved the highest accuracy due to class imbalance, it failed to identify any positive cases.

- Accuracy: **0.887**
- Recall: **0.000**
- F1-score: **0.000**

This demonstrates why accuracy alone is not an appropriate evaluation metric for imbalanced healthcare prediction problems.

### Random Forest

Random Forest achieved the strongest overall predictive performance.

| Metric | Value |
|---------|-------|
| ROC AUC | **0.671** |
| Average Precision | **0.215** |
| F1-score | **0.274** |

### Important Predictors

The most influential variables included:

- Number of inpatient visits
- Prior healthcare utilization
- Discharge disposition
- Number of medications
- Number of laboratory procedures
- Time in hospital
- Diagnosis count
- Age

These findings were consistent with the exploratory data analysis.

---

## Initial Causal Inference Analysis

To complement predictive modeling, the project includes an initial causal inference analysis using propensity score methods.

The analysis investigates whether receiving diabetes medication is associated with 30-day hospital readmission by estimating the Average Treatment Effect on the Treated (ATT).

Methods include:

- Propensity score estimation
- Inverse probability weighting (IPW)
- Propensity score matching
- Covariate balance assessment using standardized mean differences
- Sensitivity analysis

Because the dataset is observational, the causal estimates rely on assumptions such as no unmeasured confounding and should not be interpreted as definitive evidence of causation.

---

## Technologies

- Python
- pandas
- NumPy
- scikit-learn
- matplotlib
- Jupyter Notebook

---

## Future Work

Planned improvements include:

- Additional causal analyses using alternative treatment definitions
- Hyperparameter tuning
- XGBoost and LightGBM models
- Calibration analysis
- SHAP-based model interpretation
- External validation on additional healthcare datasets

---

## Key Takeaways

- Patient-level train/test splitting prevents data leakage.
- Accuracy alone is insufficient for evaluating imbalanced healthcare classification.
- Previous healthcare utilization was one of the strongest predictors of readmission.
- Random Forest achieved the strongest predictive performance among the evaluated models.
- Propensity score methods provide a framework for investigating causal questions beyond prediction while highlighting the importance of careful adjustment for confounding.

---

## License

This project is intended for educational and research purposes.

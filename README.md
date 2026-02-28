# Consumer Loan – Data Preprocessing & Feature Engineering

![Python](https://img.shields.io/badge/Python-3.9-blue)
![Pandas](https://img.shields.io/badge/Pandas-1.4-green)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.5-orange)

This project performs comprehensive data cleaning and feature engineering on a consumer loan dataset (30,000 records, 24 features) to prepare it for building a default prediction model. The processed dataset is ready to be used with classification algorithms such as logistic regression, decision trees, or random forests.

## 🔍 Project Overview
- **Goal**: Transform raw loan repayment data into a structured, clean, and feature-rich dataset suitable for machine learning.
- **Dataset**: 30,000 loan records with features including credit limit, demographic info, repayment statuses over 6 months, bill amounts, and payment amounts.
- **Key Tasks**:
  - Duplicate removal
  - Categorical encoding (gender, education, marriage, default flag)
  - Repayment status analysis: counted occurrences of each status (e.g., "paid on time", "delayed 1 month") across 6 months
  - Cross‑feature combinations (e.g., total early/on‑time payments, total delayed payments grouped by severity)
  - Outlier detection and removal (e.g., conflicting records with perfect payment history but marked as default)
  - Discretization of continuous variables (credit limit, age) using deciles
  - Sophisticated binning of bill amounts (negative values handled separately, then merged with positive deciles)
  - Payment amount discretization based on percentiles
  - Feature selection via correlation with the target (keeping features with correlation > 0.1)

## 📁 Repository Structure
consumer-loan-default-prediction/
├── data/个人消费贷是否违约.xlsx  – sample data or instructions to obtain
├── notebooks/ # Jupyter notebook with the full analysis
│ └── eda_feature_engineering.ipynb
├── requirements.txt # Python dependencies
├── README.md # This file
├── LICENSE # MIT License
└── .gitignore # Ignores data, notebooks checkpoints, etc.

text

## 🚀 How to Use
1. Clone this repository.
2. Install required packages:
   ```bash
   pip install -r requirements.txt
Open and run the notebook notebooks/eda_feature_engineering.ipynb to reproduce the data processing.

The final cleaned dataset (df_m) is ready for modeling. You can extend the notebook by adding a classifier (e.g., sklearn.ensemble.RandomForestClassifier) to build a full prediction pipeline.

📊 Results
After preprocessing, the dataset contains 40 features and 29,228 records (after removing duplicates and outliers). The final feature set (selected by correlation > 0.1) includes:

延迟还款_2_5_total_cnt (total delayed payments of 2–5 months)

还款延迟二个月_cnt (count of 2‑month delays)

信用额度 (credit limit, discretized)

按时还款_cnt (count of on‑time payments)

10月支付金额 (payment amount in Oct, discretized)

… and 15 other features.

These features show the strongest linear relationship with the target 是否违约 (default flag) and can be used directly in classification models.

🛠️ Technologies Used
Python 3.9

pandas, numpy

matplotlib (for histograms)

scikit-learn (only for correlation; modeling can be added)

📌 Future Work
Train and evaluate classification models (logistic regression, random forest, XGBoost) on the processed dataset.

Perform hyperparameter tuning and cross‑validation.

Deploy the best model as a simple API.

📄 License
MIT

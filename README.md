# ⭐ FinSecure Loan Default Prediction — Machine Learning Project ⭐

## 📌 Overview
FinSecure is a peer-to-peer lending platform where investors fund loans for borrowers.  
The goal of this project is to build a **data-driven model** that predicts whether a loan will be paid back (**1**) or default (**0**).

A high-quality prediction system helps FinSecure:
- ⭐ Reduce investor losses  
- ⭐ Improve trust  
- ⭐ Strengthen automated loan approval  

---

## 🎯 Project Objectives
- Understand the target variable and what constitutes a default  
- Preprocess and engineer features using a structured pipeline  
- Train and evaluate ML models (baseline + tuned model)  
- Maximize **ROC–AUC** for probability predictions  
- Check fairness across education and loan purpose subgroups  
- Visualize **EDA, model curves, and subgroup performance**  

---

## 📊 Dataset Description
The dataset contains **268,114 loan applications** with features including:

- **Borrower information:** income, credit score, DTI  
- **Loan details:** amount, interest rate, purpose  
- **Risk indicators:** grade, subgrade  
- **Demographic information:** gender, education, employment  
- **Target:** `loan_paid_back` (1 = paid, 0 = default)  

---

## 📓 Notebooks
| Notebook | Purpose |
|----------|---------|
| **01_eda.ipynb** | Exploratory Data Analysis + visuals |
| **02_preprocessing_pipeline.ipynb** | Feature engineering + preprocessing + saving artifacts |
| **03_modeling_auc.ipynb** | Model training (Logistic + XGBoost), ROC/PR curves, thresholding |
| **04_subgroup_analysis.ipynb** | Fairness analysis + subgroup AUC bar charts |

---

## 🤖 Models Used
### 1. Logistic Regression (Baseline)
- **ROC–AUC:** 0.9121  
- **PR–AUC:** 0.9716  

### 2. XGBoost (Final Model)
- **ROC–AUC:** 0.9190  
- **PR–AUC:** 0.9739  
- **Selected threshold:** 0.7856  

✅ Balanced performance + strong nonlinear learning  

---

## ⚙️ Preprocessing Pipeline
- Dropped `id`  
- Split `grade_subgrade` → `grade` + `subgrade_num`  
- Engineered features:  
  - `income_to_loan`  
  - `credit_bucket` (FICO-style)  
  - `interest_bin` (quartiles)  
- Encodings:  
  - **Ordinal:** grade  
  - **One-hot:** all categorical features  
- Scaling: **StandardScaler** on numerical columns  
- Stratified **80/20 train-test split**  
- Saved preprocessing pipeline as `preprocessor_finsecure.pkl`  

---

## 📈 Subgroup AUC Analysis
### 🎓 Education Level
- Range: **0.915 – 0.929**  
- No biased performance across any level  

### 💳 Loan Purpose
- **Top 3:** Education, Medical, Vacation  
- **Bottom 3:** Other, Debt consolidation, Car  
- Still fair and acceptable (**all AUC > 0.90**)  

---

## 📊 Visuals Included
- Histograms for numeric features  
- Category count plots  
- Correlation heatmap  
- ROC Curve  
- Precision–Recall Curve  
- Subgroup AUC bar charts  

---

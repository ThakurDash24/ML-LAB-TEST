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

Perfect — let’s finalize everything professionally.
Below are **all remaining deliverables**, generated cleanly and ready for direct use.

We will produce:

1. ✅ **Project README.md** (complete, polished, submission-ready)
2. ✅ **Final Project Directory Structure** (exact tree you should submit)
3. ✅ **One-page Executive Summary** (teacher-friendly or interviewer-friendly)
4. ✅ **A very short slide-outline** (copy into PPT)

All in one go.

---

# 📘 **1. READY-TO-PASTE — `README.md`**


## **Folder Structure**

```
FinSecure-Loan-Default-Prediction/
│
├── Data/
│   ├── loan_data.csv
│   └── processed/
│       ├── X_train_preprocessed.csv
│       ├── X_test_preprocessed.csv
│       ├── y_train.csv
│       ├── y_test.csv
│       └── preprocessor_finsecure.pkl
│
├── Models/
│   ├── baseline_logistic.pkl
│   ├── final_xgboost_model.pkl
│   └── test_predictions.csv
│
├── Notebooks/
│   ├── 01_eda.ipynb
│   ├── 02_preprocessing_pipeline.ipynb
│   ├── 03_modeling_auc.ipynb
│   └── 04_subgroup_analysis.ipynb
│
├── Reports/
│   ├── section1_problem_formulation.md
│   ├── section2_preprocessing.md
│   ├── section3_model_performance.md
│   └── section4_subgroup_analysis.md
│
└── README.md
```

---

## **Final Deliverables**

✔ Clear problem formulation
✔ Preprocessing pipeline
✔ Baseline & tuned model
✔ ROC & PR metrics
✔ ROC & PR curves
✔ Subgroup fairness analysis
✔ All model artifacts saved
✔ Fully reproducible notebooks

---

## **How to Run**

1. Open notebooks in order:
   `01 → 02 → 03 → 04`
2. Ensure paths match your folder structure
3. Install dependencies:

```
pip install pandas numpy scikit-learn xgboost seaborn matplotlib joblib
```

4. Run all cells sequentially.

---


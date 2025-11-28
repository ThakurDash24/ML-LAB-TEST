# **Section 2: Feature Engineering & Preprocessing Pipeline**

## **Overview**

To prepare the loan dataset for machine learning, a structured preprocessing pipeline was developed.
The goal of this pipeline is to clean, transform, and encode the raw data in a consistent way, ensuring that the final model receives high-quality numerical inputs.
The entire preprocessing pipeline is fitted only on the **training data** to avoid data leakage, and the same transformations are applied to the test data.

---

## **1. Data Cleaning**

### **Dropped Columns**

* `id`
  This column uniquely identifies each loan application but contains no predictive information.
  It was removed from the feature set.

### **Splitting Combined Grade**

The dataset originally contained a combined feature:

```
grade_subgrade (e.g., C3, B1, D4)
```

This was split into:

* `grade` → alphabetic part (A–E), representing the high-level credit grade
* `subgrade` → numeric part, later converted to `subgrade_num` for modeling

This split improves interpretability and supports ordinal encoding.

---

## **2. Feature Engineering**

Several meaningful features were created to enhance model performance:

### **● income_to_loan**

```
income_to_loan = annual_income / loan_amount
```

Measures how comfortably a borrower can afford the requested loan.

### **● credit_bucket (FICO-style bins)**

Credit score was grouped into meaningful risk categories:

* Poor
* Fair
* Good
* Very Good
* Excellent

### **● interest_bin (Quarterly Risk Bins)**

The interest rate was divided into four equal-frequency bins:

* ir_q1 (lowest rates)
* ir_q2
* ir_q3
* ir_q4 (highest rates)

Higher bins often correlate with higher borrower risk.

---

## **3. Handling Missing Values**

Although the dataset contained **no missing values**, the pipeline is designed to handle missingness safely:

* **Numerical features** → `median` imputation
* **Categorical features** → fill `"missing"` token

This makes the pipeline robust in case of future data shifts.

---

## **4. Encoding Categorical Variables**

Different encodings were chosen depending on the nature of the feature:

### **● Ordinal Encoding**

`grade` was encoded using a defined order:

```
A > B > C > D > E
```

This preserves the natural ranking of loan grades.

### **● One-Hot Encoding**

Applied to non-ordinal categories:

* gender
* marital_status
* education_level
* employment_status
* loan_purpose
* credit_bucket
* interest_bin

This avoids introducing artificial order into these variables.

---

## **5. Scaling Numerical Features**

Numerical features were standardized using:

```
StandardScaler (mean = 0, std = 1)
```

This helps gradient-based models and stabilizes training.

---

## **6. Train/Test Split**

A stratified 80/20 split was performed on the target variable (`loan_paid_back`) to preserve the original class distribution:

* Training data: 80%
* Testing data: 20%

Stratification ensures both sets retain the ~20% default rate.

---

## **7. Pipeline Summary**

The final preprocessing pipeline includes:

* Median imputation (numeric)
* Constant imputation + One-Hot (categorical)
* Ordinal encoding (grade)
* Standard scaling (numeric)
* Derived features (income_to_loan, credit_bucket, interest_bin)
* Train/test split with no leakage

---

## **8. Saved Artifacts**

The following files have been saved to `Data/processed/`:

* `preprocessor_finsecure.pkl`
* `X_train_preprocessed.csv`
* `X_test_preprocessed.csv`
* `y_train.csv`
* `y_test.csv`



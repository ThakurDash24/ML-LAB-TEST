# **Section 3: Model Development & ROC–AUC Evaluation**

## **1. Modeling Approach**

To predict loan repayment outcomes, two models were developed and evaluated:

1. **Logistic Regression (Baseline)**
2. **XGBoost (Final Model)**

The preprocessing pipeline created in Section 2 was applied to both training and test datasets to ensure identical feature transformations.

The primary evaluation metric, as required, is the **Area Under the ROC Curve (ROC–AUC)**.
Additionally, **PR–AUC** was computed to understand performance on the minority class (defaults).

---

## **2. Baseline Model: Logistic Regression**

Logistic Regression was trained with `class_weight='balanced'` to address the ~20% default class imbalance.

### **Performance**

* **ROC–AUC:** *0.9121*
* **PR–AUC:** *0.9716*

The baseline model already demonstrated strong discriminatory power.

---

## **3. Final Model: XGBoost**

XGBoost was chosen as the final model due to its ability to capture nonlinear patterns.
The model was trained with the following optimized parameters:

```
n_estimators = 300
learning_rate = 0.05
max_depth = 5
subsample = 0.9
colsample_bytree = 0.9
eval_metric = 'logloss'
```

### **Performance**

* **ROC–AUC:** *0.9190*
* **PR–AUC:** *0.9739*

This improvement over the baseline indicates that XGBoost captures more complex relationships in borrower behavior.

---

## **4. Threshold Selection (Operational Decision Boundary)**

Although ROC–AUC evaluates ranking quality, real-world decisions require a **probability threshold**.

Using **Youden’s J statistic (TPR – FPR)**, the optimal operating threshold was identified as:

```
Best Threshold = 0.7856
```

---

## **5. Confusion Matrix at Best Threshold**

|                      | Predicted Paid Back | Predicted Default |
| -------------------- | ------------------- | ----------------- |
| **Actual Paid Back** | 8451                | 2358              |
| **Actual Default**   | 4604                | 38210             |

---

## **6. Final Classification Metrics**

* **Accuracy:** *0.8702*
* **F1 Score:** *0.9165*

These results demonstrate a strong balance between default detection and correct approval of safe loans, making the model suitable for FinSecure’s loan decision pipeline.

---
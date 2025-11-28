# Section 1: Problem Formulation & Target Variable Analysis

## Business Problem

**FinSecure** is a peer-to-peer lending platform. Its success relies on accurately predicting loan defaults, which cause **direct monetary loss** for investors and reduce platform **trust**.

The objective is to build a machine-learning model to predict the probability that a borrower will repay their loan in full.

---

## Target Variable: `loan_paid_back`

The dataset features a **binary target variable** capturing the repayment outcome:

* **1** → Loan was **paid back in full** (Non-default)
* **0** → Loan was **not paid back (Default)**

In this problem, a **default** is defined as the case where `loan_paid_back` = **0**. This is the critical outcome the model must learn to predict.

---

## Target Class Distribution

The dataset contains **268,114** loan applications:

* **Paid back (1):** ~79.8%
* **Default (0):** ~20.2%

This presents a **moderately imbalanced classification problem**. The default class (0) is the less frequent but **more critical** class from a business standpoint.

---

## Modeling Objective

The goal is to develop a predictive model that achieves the following:

* Produces a **probability score** for each borrower.
* **Maximizes ROC–AUC**, ensuring strong separation between good and risky borrowers.
* Supports **automated loan approval**, helps **control default rates**, and protects **investor capital**.
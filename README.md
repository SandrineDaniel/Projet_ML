# **Diabetes Readmission Prediction – Machine Learning Project**

**Authors**: Sandrine Daniel, Ovia Chanemouganandam
**Group**: DIA 4
**Dataset**: [https://www.kaggle.com/datasets/brandao/diabetes](https://www.kaggle.com/datasets/brandao/diabetes)

---

## **✿ Project Overview**

This project aims to predict **hospital readmission** for diabetic patients using machine learning.
The goal is to help hospitals and medical staff **identify high-risk patients**, optimize resource planning, and potentially reduce preventable readmissions.

We address a **multiclass classification problem**:

* **0** → No Readmission
* **1** → Readmitted after 30 days
* **2** → Readmitted within 30 days

This prediction task is challenging due to:

* High class imbalance (very few “<30 days” cases)
* Many categorical medical variables (race, medications, ICD-9 diagnosis codes, etc.)
* Noisy data and inconsistent medical coding
* Sparse and high-dimensional one-hot encoded features

---

## **✿ Notebooks**

### **1. Preprocessing Notebook**

Includes:

* Dataset loading and quality checks
* Exploratory data analysis 
* Visualization: age distribution, diagnoses, medication patterns
* Handling missing values & inconsistent categories
* Encoding strategies:
  * **One-hot encoding** for categorical variables
  * **Ordinal encoding / mapping** for ordered categories
  * ICD-9 diagnostic grouping into medical categories
* Scaling numerical variables
* Splitting the dataset into **train/test** sets

At the end, all processed datasets (`X_train`, `X_test`, `scaled`, etc.) are saved in the **data/** folder.

---

### **2. Modeling Notebook**

Covers all model development steps:

#### ** ❥ Baseline Models**

* Logistic Regression
* Decision Tree
* Random Forest
* K-Nearest Neighbors
* XGBoost

Evaluated using **F1-macro**, **F1-weighted**, **ROC-AUC**, and **confusion matrices**.

#### ** ❥ Class Imbalance Strategies**

* `class_weight="balanced"`
* SMOTE (used selectively)

#### ** ❥ Dimensionality Reduction**

* PCA applied (but not kept — no performance improvement)

#### ** ❥ Hyperparameter Tuning**

* RandomizedSearchCV for:
  * Logistic Regression
  * Decision Tree
  * Random Forest
  * XGBoost

#### ** ❥ Ensemble Learning**

* Bagging
* Soft Voting
* Stacking

#### ** ❥ Advanced Model**

We selected **CatBoost**, justified by scientific literature showing strong performance on tabular datasets with many categorical features.

---

## ** Performance Summary**

Across all models, the best performing approach was:

 **Tuned Random Forest**, reaching an **F1-macro ≈ 0.45**.

Given the difficulty of the dataset (noise, imbalance, sparse features), this performance aligns with scientific literature on the same diabetes readmission task.

---

## ✿ Project Structure

```
Projet_ML/
│
├── data/                        # Train/test splits 
│
├── preprocessing_notebook.ipynb
├── model_training_notebook.ipynb
├── requirements.txt
└── README.md
```

---

## ✿ Dataset 

Dataset available on Kaggle:
[https://www.kaggle.com/datasets/brandao/diabetes](https://www.kaggle.com/datasets/brandao/diabetes)



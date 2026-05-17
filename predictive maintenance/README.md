# 🔧 Predictive Maintenance for Manufacturing

> A machine learning pipeline to predict machine failure
> using sensor data to avoid unplanned downtime.

---

## 📌 Objective
Predict whether a machine will fail (binary classification)
using sensor readings collected from industrial equipment.
The goal is to enable proactive maintenance before failure
occurs.

---

## 📊 Dataset

- Name    : AI4I 2020 Predictive Maintenance Dataset
- Source  : Kaggle
- Link    : https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-classification
- Rows    : 10,000
- Columns : 10
- Target  : Target (0 = No Failure, 1 = Failure)

---

## 📋 Dataset Features

| Feature               | Type        | Description                        |
|-----------------------|-------------|------------------------------------|
| UDI                   | ID          | Dropped (not useful)               |
| Product ID            | ID          | Dropped (not useful)               |
| Type                  | Categorical | Machine quality (L, M, H)          |
| Air Temperature [K]   | Numerical   | Ambient air temperature in Kelvin  |
| Process Temp [K]      | Numerical   | Process temperature in Kelvin      |
| Rotational Speed [rpm]| Numerical   | Machine rotational speed           |
| Torque [Nm]           | Numerical   | Rotational force applied           |
| Tool Wear [min]       | Numerical   | Cumulative tool usage time         |
| Target                | Binary      | 0 = Normal, 1 = Failure            |
| Failure Type          | Categorical | Type of failure (encoded, dropped) |

---

## ⚙️ Pipeline

1. Load CSV data
2. Drop UDI and Product ID columns
3. Label encode Type and Failure Type columns
4. Convert all columns to numeric
5. Drop rows with NaN values
6. Separate features and target
7. Replace NaN/inf with np.nan_to_num()
8. Train/Test split (80/20, stratified)
9. Train Random Forest and XGBoost models
10. Evaluate and visualize results

---

## 🧠 Models Used

### 1. Random Forest Classifier
- n_estimators : 100
- random_state : 42
- Used for     : Prediction + Feature Importance

### 2. XGBoost Classifier
- eval_metric  : logloss
- tree_method  : hist
- random_state : 42
- Used for     : Prediction + Confusion Matrix

---

## 📈 Analysis Performed

- Data loading and inspection (head, info)
- Label encoding of categorical columns
- Null value handling
- Train/test split with stratification
- Binary classification with two models
- Confusion matrix visualization (XGBoost)
- Feature importance bar chart (Random Forest)
- Classification report (Precision, Recall, F1)
- ROC-AUC score for both models

---

## 📊 Visualizations

- Confusion Matrix — XGBoost predictions heatmap
- Feature Importance — Top features ranked by
  Random Forest importance scores

---

## 📦 Technologies Used

| Tool             | Purpose                        |
|------------------|--------------------------------|
| Python 3         | Programming language           |
| Pandas           | Data loading and manipulation  |
| NumPy            | Numerical operations           |
| Scikit-learn     | Random Forest, metrics, splits |
| XGBoost          | Gradient boosting model        |
| Matplotlib       | Plotting charts                |
| Seaborn          | Confusion matrix heatmap       |
| Jupyter Notebook | Development environment        |

---

## ▶️ How to Run

### Step 1 — Install required libraries
pip install pandas numpy scikit-learn xgboost matplotlib seaborn

### Step 2 — Download the dataset
Visit:
https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-classification

Download and rename the file to:
predictive_maintenance.csv

Place it in the same folder as your code.

### Step 3 — Run the code
Open Jupyter Notebook and run all cells
OR run directly:
python predictive_maintenance.py

### Step 4 — Outputs you will see
- df.head() and df.info() printed
- Random Forest classification report
- Random Forest ROC-AUC score
- XGBoost classification report
- XGBoost ROC-AUC score
- Confusion Matrix plot (XGBoost)
- Feature Importance plot (Random Forest)

---

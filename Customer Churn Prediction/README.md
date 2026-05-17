# ═══════════════════════════════════════
# PROJECT 2: Customer Churn Prediction
# ═══════════════════════════════════════

## 1. PROJECT OVERVIEW
This project builds a machine learning system to predict
whether a telecom customer will churn (cancel their
subscription). By analyzing historical customer data
including usage patterns, contract details, and billing
information, the model identifies at-risk customers early
so the business can take retention actions.

Customer acquisition costs 5x more than retention. Early
churn prediction directly impacts business revenue.

---

## 2. OBJECTIVES
- Predict whether a customer will churn (binary classification)
- Handle imbalanced churn data using SMOTE
- Compare Logistic Regression, Decision Tree, and Neural Network
- Identify top features driving customer churn
- Provide actionable insights for business retention strategy

---

## 3. DATASET

| Property      | Details                                      |
|---------------|----------------------------------------------|
| Name          | Telco Customer Churn - IBM Dataset           |
| Source        | Kaggle                                       |
| Kaggle Link   | kaggle.com/datasets/yeanzc/telco-customer-churn-ibm-dataset |
| Format        | Excel (.xlsx)                                |
| Rows          | ~7,000                                       |
| Columns       | 33                                           |
| Target Column | Churn Label (Yes = 1, No = 0)                |
| Class Balance | ~73% No Churn, ~27% Churn (imbalanced)       |

---

## 4. DATASET FEATURES

| Feature          | Type        | Description                          |
|------------------|-------------|--------------------------------------|
| Tenure Months    | Numerical   | How long customer has been with service |
| Monthly Charges  | Numerical   | Monthly bill amount                  |
| Total Charges    | Numerical   | Total amount billed to date          |
| Contract         | Categorical | Month-to-month, One year, Two year   |
| Internet Service | Categorical | DSL, Fiber Optic, None               |
| Payment Method   | Categorical | Electronic check, Credit card, etc.  |
| Phone Service    | Categorical | Yes/No                               |
| Tech Support     | Categorical | Yes/No/No internet service           |
| Streaming TV     | Categorical | Yes/No/No internet service           |
| Senior Citizen   | Binary      | 1 = Senior, 0 = Not senior           |
| Partner          | Categorical | Yes/No                               |
| Dependents       | Categorical | Yes/No                               |
| Churn Label      | Binary      | Yes = Churned, No = Retained         |

### Dropped Columns (not useful for prediction)
CustomerID, Count, Country, State, City, Zip Code,
Lat Long, Latitude, Longitude, Churn Value,
Churn Score, CLTV, Churn Reason

---

## 5. TECHNOLOGIES USED

| Technology       | Version  | Purpose                           |
|------------------|----------|-----------------------------------|
| Python           | 3.x      | Core programming language         |
| Pandas           | Latest   | Data loading and manipulation     |
| NumPy            | Latest   | Numerical operations              |
| Scikit-learn     | Latest   | ML models and evaluation          |
| Imbalanced-learn | Latest   | SMOTE for class balancing         |
| Matplotlib       | Latest   | Data visualization                |
| Seaborn          | Latest   | Statistical plots                 |
| OpenPyXL         | Latest   | Reading Excel (.xlsx) files       |
| Jupyter Notebook | Latest   | Development environment           |

---

## 6. ANALYSIS PERFORMED

### 6.1 Data Preprocessing
- Loaded Excel file using pd.read_excel()
- Dropped irrelevant location and score columns
- Mapped Churn Label: Yes → 1, No → 0
- Label encoded all remaining categorical columns
- Converted all features to numeric
- Dropped rows with missing/null values
- Replaced NaN/inf values using np.nan_to_num()

### 6.2 Exploratory Analysis
- Checked churn distribution (before and after SMOTE)
- Reviewed all 33 column names and data types
- Identified categorical vs numerical features
- Visualized churn distribution as bar chart

### 6.3 Class Imbalance Handling
- Applied SMOTE on training set only
- Balanced distribution from 73/27 to 50/50
- Prevents model from always predicting majority class

### 6.4 Feature Scaling
- Applied StandardScaler on training data
- Fitted on training set, transformed test set
- Required for Logistic Regression and Neural Network

### 6.5 Model Training
- Logistic Regression (max_iter=1000)
- Decision Tree with GridSearchCV
  - Tuned: max_depth, min_samples_split, criterion
- Neural Network MLP
  - Architecture: 64 → 32 neurons, ReLU activation
  - alpha=0.001, max_iter=300

### 6.6 Model Evaluation
- Classification Report for all 3 models
- ROC-AUC Score on test set
- 5-Fold Cross Validation ROC-AUC
- Side-by-side Confusion Matrices (3 plots)
- ROC Curve comparison (all 3 models)
- Top 10 Feature Importance (Decision Tree)
- Churn distribution before/after SMOTE

---

## 7. MODELS & RESULTS

| Model               | ROC-AUC | CV ROC-AUC |
|---------------------|---------|------------|
| Logistic Regression | ~0.85   | ~0.84      |
| Decision Tree       | ~0.82   | ~0.80      |
| Neural Network      | ~0.86   | ~0.85      |

Neural Network performed best overall.
Logistic Regression is a strong and interpretable baseline.

---

## 8. KEY FINDINGS
- Contract type is the strongest churn predictor
- Month-to-month customers churn significantly more
- Customers with higher monthly charges churn more
- Shorter tenure customers are at higher churn risk
- Fiber optic internet users churn more than DSL users
- Neural Network gives best ROC-AUC after SMOTE

---

## 9. HOW TO RUN

### Step 1 — Install dependencies
pip install pandas numpy scikit-learn imbalanced-learn
pip install matplotlib seaborn openpyxl

### Step 2 — Download Dataset
Go to: https://www.kaggle.com/datasets/yeanzc/telco-customer-churn-ibm-dataset
Download and place Telco_customer_churn.xlsx inside a
folder named telco/ in your project directory

### Step 3 — Folder structure should look like
customer_churn/
├── customer_churn.py
└── telco/
    └── Telco_customer_churn.xlsx

### Step 4 — Run the code
Open Jupyter Notebook and run all cells
OR
python customer_churn.py

### Step 5 — View Outputs
- Churn distribution plots (before/after SMOTE)
- 3 Confusion Matrix plots side by side
- ROC Curve comparison for all 3 models
- Top 10 Feature Importance chart
- Model comparison table printed in console

---

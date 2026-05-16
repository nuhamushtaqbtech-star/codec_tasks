# 🔧 Predictive Maintenance for Manufacturing

> An end-to-end machine learning pipeline to predict when machinery is likely to fail and avoid unplanned downtime.

## 📌 Goal
Predict machine failure using sensor data (temperature, torque, tool wear, etc.) before it happens.

## 📊 Dataset
- **Kaggle:** https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-classification
- **UCI:** https://archive.ics.uci.edu/dataset/601/ai4i+2020+predictive+maintenance+dataset
- **Size:** 10,000 rows × 10 columns
- **Features:** Air Temperature, Process Temperature, Rotational Speed, Torque, Tool Wear, Machine Type

## ⚙️ Pipeline
Raw Data → Drop Irrelevant Cols → Label Encoding → Handle NaN → Train/Test Split → SMOTE → Model Training → Evaluation

## 🧠 Models Used
- Random Forest — ensemble classifier with feature importance
- XGBoost — gradient boosted trees with GridSearchCV tuning

## 📈 Evaluation
- Classification Report (Precision, Recall, F1)
- ROC-AUC Score
- 5-Fold Cross Validation
- Confusion Matrix
- ROC Curve Comparison
- Feature Importance Plot

## ▶️ How to Run
pip install pandas numpy scikit-learn xgboost imbalanced-learn matplotlib seaborn

python predictive_maintenance.py

## 📦 Dependencies
pandas
numpy
scikit-learn
xgboost
imbalanced-learn
matplotlib
seaborn

## 📊 Results
| Model         | ROC-AUC |
|---------------|---------|
| Random Forest | ~0.98   |
| XGBoost       | ~0.99   |

## 💡 Key Techniques
- SMOTE — handles class imbalance
- GridSearchCV — hyperparameter tuning
- 5-Fold Cross Validation — robust evaluation
- Label Encoding — categorical preprocessing

## 📜 License
MIT License

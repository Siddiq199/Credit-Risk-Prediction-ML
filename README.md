💳Credit Card Default Prediction Model (Classification Project)

This project implements a complete Machine Learning pipeline to predict the probability of a credit card customer defaulting on their next payment. The goal is to build a robust classification model that helps financial institutions identify high-risk accounts and reduce financial losses.

🛠️ Project Goals & Methodology

The core objective was to develop a predictive model from raw data to a final, interpretable ML model ready for deployment.
| Aspect               | Details                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| **Problem Type**     | Binary Classification (`default_payment_next_month`: 1 or 0)                                      |
| **Dataset**          | Default of Credit Card Clients (30,000 records)                                                   |
| **Model Used**       | Logistic Regression (simple, interpretable baseline)                                              |
| **Key Deliverables** | Data Cleaning, Feature Engineering, Model Training, Performance Evaluation, Visual Interpretation |

✨ Machine Learning Pipeline
1. Preprocessing (ColumnTransformer)
✔ Handling Categorical Features
Columns like SEX, EDUCATION, and all PAY_* repayment status columns were processed using One-Hot Encoding.

✔ Feature Scaling
High-range numeric features like:
LIMIT_BAL
BILL_AMT*
PAY_AMT*
were scaled using StandardScaler to normalize values.

✔ Imputation
SimpleImputer was used to handle missing values and maintain pipeline robustness.

2. Model Training
A scikit-learn Pipeline connected preprocessing to a LogisticRegression classifier.
Training was performed on 80% of the dataset (X_train, y_train).

🔬 Performance Evaluation
The model achieved the following on the test set:
| Metric                  | Result     | Interpretation                            |
| ----------------------- | ---------- | ----------------------------------------- |
| **Accuracy**            | **81.70%** | Overall correctness                       |
| **Precision (Default)** | **66%**    | When predicting default, 66% were correct |
| **Recall (Default)**    | **35%**    | Captures 35% of actual defaulters         |

Confusion Matrix Analysis
|                           | Predicted No Default (0) | Predicted Default (1) |
| ------------------------- | ------------------------ | --------------------- |
| **Actual No Default (0)** | 4,463 (True Negatives)   | 210 (False Positives) |
| **Actual Default (1)**    | 860 (False Negatives)    | 467 (True Positives)  |

Key Insight:
The 860 False Negatives (actual defaulters predicted as safe) represent the largest business risk.

📈 Feature Importance (Interpretation)
🔥 Features Increasing Default Risk
PAY_1 through PAY_6 (repayment delays)

❄ Features Decreasing Default Risk
LIMIT_BAL
PAY_AMT*
These coefficients help identify behavioral patterns linked to financial risk.

🔑 Technologies Used
Python
Pandas (Data Manipulation)
NumPy (Numerical Operations)
Scikit-learn (Pipelines, Models, Preprocessing)
Matplotlib & Seaborn (Visualization)
Jupyter / Google Colab (Development Environment)

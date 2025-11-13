💳 Credit Risk Classification: Predicting Customer Default
This project demonstrates the development of a predictive machine learning model to assess and classify the credit risk of clients. Using historical payment data, the model predicts the likelihood of a customer defaulting on their next credit card payment. This capability is foundational for financial institutions to manage exposure and mitigate financial loss.

⚙️ Project Overview & Methodology
The objective was to create a highly interpretable classification model that serves as a robust baseline for credit risk assessment.
Component,Detail
Problem Type,Binary Classification
Dataset,"Default of Credit Card Clients (30,000 records)"
Goal,Predict whether the client will default on the next payment (dpnm: 1 or 0)
Algorithm,Logistic Regression
Key Features,"LIMIT_BAL, AGE, BILL_AMT*, and the critical PAY_* history columns."
Target Column,"dpnm (Binary: 0: No Default, 1: Default)"

🛠️ Steps Performed in the Pipeline
The final solution utilized a comprehensive scikit-learn Pipeline to ensure all data preparation was consistent and reproducible before model training.

Data Cleaning & Feature Engineering:
The redundant ID column was dropped.
Categorical features (SEX, EDUCATION, MARRIAGE, PAY_*) were identified for encoding.

Splitting the Dataset:
Data was split into 80% training and 20% testing sets using stratified sampling to maintain the original class balance.

Preprocessing (ColumnTransformer):
Numerical Features: Features like LIMIT_BAL and BILL_AMT* were scaled using StandardScaler to prevent any single feature from disproportionately influencing the distance-based model calculation.

Categorical Features: Columns were transformed using One-Hot Encoding to convert them into a numerical format suitable for the Logistic Regression model.

Model Building & Training:
A Logistic Regression classifier was embedded in the final pipeline, ensuring that the model learned patterns from the preprocessed (scaled and encoded) data.
Metric,Score
Overall Accuracy,0.817 (81.7%)
Precision (No Default),0.84
Recall (No Default),0.95
Precision (Default),0.66
Recall (Default),0.35

Confusion Matrix Insight:
True \ Predicted,No Default (0),Default (1)
No Default (0),"4,463 (True Negatives)",210 (False Positives)
Default (1),860 (False Negatives),467 (True Positives)

Interpretation
False Negatives (860): This represents the greatest risk. The model predicted these 860 customers would pay, but they actually defaulted. This directly leads to financial loss, indicating a need for optimization to increase Recall (Default).

Feature Importance: The Logistic Regression model is highly interpretable. Analysis of the coefficients showed that the past payment status columns (PAY_1 through PAY_6) were overwhelmingly the most influential features, proving that historical payment discipline is the primary driver of credit risk.

🚀 Conclusion
The project successfully built a production-ready pipeline that classifies credit risk with 81.7% accuracy. While the model demonstrates strong predictive power for non-defaulters, the high False Negative count highlights the opportunity to iterate using more advanced techniques (e.g., ensemble methods like Random Forest or XGBoost) to better detect the minority class of actual defaulters.

Tools Used
Python 3
NumPy, Pandas (Data Manipulation)
Scikit-learn (ML Pipeline, Preprocessing, Modeling)
Matplotlib, Seaborn (Visualization)
🔬 Model Evaluation & Results
The model's performance was measured on the unseen test set, focusing heavily on Recall for the minority (Default) class, as missing a defaulter is the most costly error for the bank.

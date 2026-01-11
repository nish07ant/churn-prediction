# Customer Churn Prediction

## Problem Statement
Customer churn is a critical challenge for businesses, especially in the telecommunications industry. This project aims to predict which customers are likely to churn (cancel their service) based on various customer attributes. By identifying high-risk customers early, companies can proactively implement retention strategies to reduce churn rates and increase customer lifetime value.

## Dataset Description
The dataset contains information about telecom customers with various attributes:

- **Demographics**: gender, senior citizen status, partner status, dependents
- **Contract Details**: tenure, phone service, internet service, online security, tech support, etc.
- **Usage Information**: payment method, monthly charges, total charges
- **Target Variable**: Churn (Yes/No)

Each row represents a customer, and the dataset contains both categorical and numerical features. The churn rate in the dataset is approximately 26%, indicating class imbalance.

## Tools and Libraries
- **Python**: Primary programming language
- **pandas**: Data manipulation and analysis
- **NumPy**: Numerical computing
- **scikit-learn**: Machine learning algorithms and evaluation metrics
- **Matplotlib/Seaborn**: Data visualization
- **Jupyter Notebook**: Interactive development environment

## Machine Learning Pipeline
The project follows a structured machine learning pipeline:

1. **Data Understanding**: Initial exploration of the dataset to understand its structure, features, and target variable.

2. **Data Cleaning and EDA**: 
   - Checking for missing values (none found)
   - Exploratory data analysis to identify patterns and relationships
   - Key findings: Lower tenure and higher monthly charges correlate with higher churn rates

3. **Feature Engineering**:
   - Feature selection based on EDA insights
   - Target encoding (mapping "Yes"/"No" to 1/0)
   - Ordinal encoding for contract types
   - One-hot encoding for categorical variables like internet service and payment method

4. **Modeling**:
   - Stratified train-test split to handle class imbalance
   - Logistic Regression implementation
   - Evaluation using classification metrics and ROC-AUC

## Model Evaluation and Threshold Tuning
The model was evaluated using precision, recall, F1-score, and ROC-AUC metrics. Given that false negatives (missing potential churners) are more costly than false positives, we prioritized recall over precision.

Initial evaluation with the default threshold (0.5):
- Precision: 63%
- Recall: 52%
- ROC-AUC: Good performance (specific value in notebook)

After threshold tuning (lowered to 0.4):
- Precision: 58%
- Recall: 65%
- Better balance for business needs

## Business Value and Insights
The model provides actionable insights for customer retention strategies:

1. **Targeted Retention Campaigns**: By contacting just 30% of customers (those predicted as high-risk), the company could reach 65% of actual churners.

2. **Key Churn Factors**:
   - Fiber optic customers are more likely to churn (higher expectations)
   - Electronic check payment method correlates with higher churn
   - Month-to-month contracts have significantly higher churn rates
   - Longer tenure correlates with lower churn probability

3. **Recommended Actions**:
   - Improve fiber optic service quality or customer expectations management
   - Encourage automatic payment methods
   - Offer incentives for longer-term contracts
   - Provide special attention to customers in early months of service

## How to Run the Project
1. Clone this repository
2. Install the required dependencies:
   ```
   pip install -r requirements.txt
   ```
3. Navigate to the notebooks directory and run the Jupyter notebooks in sequence:
   - 01_data_understanding.ipynb
   - 02_cleaning_and_EDA.ipynb
   - 03_features.ipynb
   - 04_model.ipynb

The notebooks are designed to be run sequentially, with each building upon the results of the previous one.
"# Customer Churn Prediction 📊

A comprehensive machine learning project for predicting customer churn using various algorithms and techniques including data preprocessing, feature engineering, and model comparison.

## 🎯 Project Overview

This project analyzes customer data to predict whether a customer will churn (leave the service) or remain loyal. The analysis includes extensive exploratory data analysis (EDA), feature engineering, and comparison of multiple machine learning models with and without SMOTE (Synthetic Minority Oversampling Technique).

## 📋 Table of Contents

- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Key Findings](#key-findings)
- [Model Performance](#model-performance)
- [Feature Engineering](#feature-engineering)
- [Results](#results)
- [Usage](#usage)
- [Contributing](#contributing)

## 📊 Dataset

The dataset contains customer information including:
- **Customer demographics**: Senior citizen status, partner, dependents
- **Service information**: Phone service, internet service type, online services
- **Account information**: Contract type, payment method, billing preferences
- **Usage metrics**: Monthly charges, total charges, tenure
- **Target variable**: Churn (Yes/No)

**Dataset Statistics:**
- Total records: 7,043 customers
- Features: 21 columns
- Target distribution: Imbalanced dataset with more non-churn customers
- Missing values: 11 null values in TotalCharges column

## 🗂️ Project Structure

```
customer_churn_prediction/
├── customer_churn_prediction.ipynb  # Main analysis notebook
├── data.csv                         # Dataset
├── README.md                        # Project documentation
└── .git/                           # Git repository
```

## 🚀 Installation

### Prerequisites
- Python 3.7+
- Jupyter Notebook or JupyterLab

### Required Libraries
```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost imbalanced-learn
```

### Libraries Used
- **Data Manipulation**: pandas, numpy
- **Visualization**: matplotlib, seaborn
- **Machine Learning**: scikit-learn, xgboost
- **Imbalanced Learning**: imbalanced-learn (SMOTE)

## 🔍 Key Findings

### Customer Behavior Insights

1. **High-Risk Segments**:
   - Customers without partners or dependents have higher churn rates
   - Fiber optic internet users show >50% churn rate
   - Month-to-month contract customers have 88.6% churn rate

2. **Service Impact**:
   - Customers without online services (Security, Backup, Protection, Support) show >50% churn
   - Add-on services play a critical role in customer retention

3. **Tenure Patterns**:
   - Bimodal distribution: Early churn (around 10 months) and loyal customers (around 70 months)
   - Most churn occurs in the first 12 months

4. **Payment & Billing**:
   - Electronic check users show highest churn (57.3%)
   - Paperless billing correlates with higher churn rates

## 🎯 Feature Engineering

Enhanced the dataset with additional features:

1. **Derived Features**:
   - `AvgChargesPerMonth`: Total charges divided by tenure
   - `HasInternetService`: Binary indicator for internet service
   - `TenureGroup`: Categorized tenure into groups (0-12, 13-24, etc.)
   - `NoOfServices`: Count of additional services subscribed

2. **Interaction Features**:
   - `Contract_MonthlyCharges`: Combined contract type with charge level
   - `IsSeniorWithTechSupport`: Senior citizens with tech support

3. **Data Preprocessing**:
   - Handled missing values in TotalCharges using median imputation
   - Applied standard scaling for numerical features
   - One-hot encoding for categorical variables

## 📈 Model Performance

### Experiment 1: Basic Models (No Feature Engineering)

| Model | SMOTE | Accuracy | ROC-AUC | Recall (Churn) | F1-score (Churn) |
|-------|-------|----------|---------|----------------|------------------|
| Logistic Regression | ✅ | 0.7374 | 0.8400 | 0.7941 | 0.6162 |
| Logistic Regression | ❌ | **0.8055** | **0.8419** | 0.5588 | 0.6040 |
| XGBoost | ❌ | 0.7850 | 0.8254 | 0.5428 | 0.5726 |
| XGBoost | ✅ | 0.7779 | 0.8224 | 0.5963 | 0.5876 |

### Experiment 2: With Feature Engineering

| Model | SMOTE | Accuracy | ROC-AUC | Precision (Churn) | Recall (Churn) | F1-score (Churn) |
|-------|-------|----------|---------|-------------------|----------------|------------------|
| Logistic Regression | ✅ | 0.7580 | 0.8570 | 0.5279 | **0.8123** | **0.6399** |
| Logistic Regression | ❌ | **0.8155** | **0.8589** | **0.6928** | 0.5442 | 0.6096 |
| XGBoost | ❌ | 0.7913 | 0.8395 | 0.6287 | 0.5174 | 0.5676 |
| XGBoost | ✅ | 0.7857 | 0.8408 | 0.6017 | 0.5630 | 0.5817 |

## 🏆 Results & Recommendations

### Best Model Selection by Use Case:

1. **Maximize Churn Detection (High Recall)**: 
   - **Logistic Regression + SMOTE + Feature Engineering**
   - Recall: 81.23%, ROC-AUC: 0.8570

2. **Balanced Performance**: 
   - **Logistic Regression (No SMOTE) + Feature Engineering**
   - Accuracy: 81.55%, ROC-AUC: 0.8589

3. **Complex Pattern Recognition**: 
   - **XGBoost** for non-linear relationships and feature interactions

### Business Recommendations:

1. **Retention Strategies**:
   - Focus on customers in first 12 months (highest churn risk)
   - Promote add-on services (Online Security, Backup, etc.)
   - Incentivize longer contract commitments

2. **Service Improvements**:
   - Address Fiber Optic service quality issues
   - Improve customer onboarding experience
   - Offer bundled services at competitive rates

3. **Payment & Billing**:
   - Encourage automatic payment methods
   - Provide incentives for annual billing cycles

## 🔧 Usage

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd customer_churn_prediction
   ```

2. **Open the Jupyter notebook**:
   ```bash
   jupyter notebook customer_churn_prediction.ipynb
   ```

3. **Run all cells** to reproduce the analysis

4. **Customize the analysis** by modifying parameters or trying different models

## 📝 Key Takeaways

- **Feature Engineering significantly improves model performance**
- **SMOTE helps detect more churners but may reduce overall accuracy**
- **Logistic Regression performs surprisingly well, often outperforming XGBoost**
- **Business insights are as valuable as model performance metrics**
- **Early intervention (first 12 months) is crucial for churn prevention**

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

*This analysis demonstrates the importance of combining robust data science techniques with business understanding to create actionable insights for customer retention.*" 

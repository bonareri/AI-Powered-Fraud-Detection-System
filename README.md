# Fraud Detection System

## Overview
This project is an AI-driven fraud detection system that identifies suspicious transactions using machine learning and anomaly detection techniques. It leverages supervised and unsupervised learning models to enhance security and prevent fraudulent activities in financial transactions.

## Dataset
The dataset used for this project is sourced from **Kaggle** and contains **284,807** transactions with the following attributes:

- **Time**: Seconds elapsed between the transaction and the first transaction in the dataset.
- **V1 to V28**: Features obtained from PCA transformation (principal component analysis).
- **Amount**: The transaction amount.
- **Class**: The target variable (0 = legitimate transaction, 1 = fraudulent transaction).

### Dataset Summary
- **Total Entries**: 284,807
- **Features**: 30 numerical features + target variable
- **Target Variable**: Binary (0 = non-fraud, 1 = fraud)

## Features
- **Machine Learning Models:** Logistic Regression, Random Forest, XGBoost, Isolation Forest, Autoencoders.
- **Anomaly Detection:** Identifies fraudulent patterns in financial data.
- **Real-Time Predictions:** API-based fraud detection system.
- **Interactive Dashboard:** Visualization using Tableau/Power BI.
- **Automated Alerts:** Email/SMS notifications for flagged transactions.
- **Cloud Deployment:** Scalable integration with AWS, GCP, or Azure.

## Technologies Used
- Python
- Pandas & NumPy for data manipulation
- Scikit-learn for machine learning models
- Matplotlib & Seaborn for data visualization
- TensorFlow for deep learning models
  
## Project Workflow
1. Data Cleaning
2. Exploratory data analysis (EDA)
3. Data preprocessing
4. Feature engineering and selection
5. Model training and evaluation (ML & deep learning approaches)
6. Performance optimization and hyperparameter tuning
7. Model deployment

## Data Cleaning

To ensure data quality and improve model performance, the following data cleaning steps were performed:

### 1. Handling Duplicate Rows
- Identified **1,081 duplicate rows** in the dataset.
- Removed all duplicate rows to prevent data leakage and model bias.

### 2. Checking for Missing Values
- No missing values were found in the dataset, so no imputation was needed.

### 3. Feature Scaling
- The `Amount` feature was normalized using **StandardScaler** to ensure consistent scaling across features.
- The `Time` column was left as is since it represents transaction timing in seconds.

### 4. Class Imbalance Handling
- The dataset is highly imbalanced, with fraudulent transactions being significantly fewer than legitimate ones.
- Implemented **SMOTE (Synthetic Minority Over-sampling Technique)** to balance the classes.

## Exploratory data analysis (EDA)

### Summary Statistics

| Statistic | Time    | V1       | V2       | V3       | V4       | V5       | V6       | V7       | V8       | V9       | ... | V21      | V22      | V23      | V24      | V25      | V26      | V27      | V28      | Amount   | Class   |
|-----------|--------|----------|----------|----------|----------|----------|----------|----------|----------|----------|-----|----------|----------|----------|----------|----------|----------|----------|----------|----------|---------|
| count     | 284807 | 284807   | 284807   | 284807   | 284807   | 284807   | 284807   | 284807   | 284807   | 284807   | ... | 284807   | 284807   | 284807   | 284807   | 284807   | 284807   | 284807   | 284807   | 284807   | 284807  |
| mean      | 94813.86 | 0.00     | 0.00     | 0.00     | 0.00     | 0.00     | 0.00     | 0.00     | 0.00     | 0.00     | ... | 0.00     | 0.00     | 0.00     | 0.00     | 0.00     | 0.00     | 0.00     | 0.00     | 88.35    | 0.0017  |
| std       | 47488.14 | 1.96     | 1.65     | 1.52     | 1.41     | 1.38     | 1.33     | 1.24     | 1.19     | 1.10     | ... | 0.73     | 0.72     | 0.62     | 0.61     | 0.52     | 0.48     | 0.40     | 0.33     | 250.12   | 0.04    |
| min       | 0.00   | -56.41   | -72.72   | -48.33   | -5.68    | -113.74  | -26.16   | -43.56   | -73.22   | -13.43   | ... | -34.83   | -10.93   | -44.81   | -2.84    | -10.30   | -2.60    | -22.57   | -15.43   | 0.00     | 0.00    |
| 25%       | 54201.5 | -0.92    | -0.60    | -0.89    | -0.85    | -0.69    | -0.77    | -0.55    | -0.21    | -0.64    | ... | -0.23    | -0.54    | -0.16    | -0.35    | -0.32    | -0.33    | -0.07    | -0.05    | 5.60     | 0.00    |
| 50%       | 84692.0 | 0.02     | 0.07     | 0.18     | -0.02    | -0.05    | -0.27    | 0.04     | 0.02     | -0.05    | ... | -0.03    | 0.01     | -0.01    | 0.04     | 0.02     | -0.05    | 0.00     | 0.01     | 22.00    | 0.00    |
| 75%       | 139320.5 | 1.32     | 0.80     | 1.03     | 0.74     | 0.61     | 0.40     | 0.57     | 0.33     | 0.60     | ... | 0.19     | 0.53     | 0.15     | 0.44     | 0.35     | 0.24     | 0.09     | 0.08     | 77.16    | 0.00    |
| max       | 172792.0 | 2.45     | 22.06    | 9.38     | 16.88    | 34.80    | 73.30    | 120.59   | 20.01    | 15.59    | ... | 27.20    | 10.50    | 22.53    | 4.58     | 7.52     | 3.52     | 31.61    | 33.85    | 25691.16 | 1.00    |

---

### Key Insights

#### 1. Dataset Overview
- The dataset consists of **284,807 transactions**, with a highly imbalanced distribution of fraud cases (`Class = 1`).
- The **mean transaction amount** is **$88.35**, but there is a wide range, with the **maximum transaction** reaching **$25,691.16**.

#### 2. Fraud Class Distribution
- The fraud cases account for **only 0.17% of the total transactions**, making fraud detection a highly imbalanced classification problem.
- The data preprocessing should include **techniques like oversampling (SMOTE) or undersampling** to balance the dataset.

#### 3. Correlation Analysis
- Highly correlated features with fraud include **V11 (0.1549), V4 (0.1334), and V2 (0.0913)**.
- Some features are **strongly negatively correlated** with fraud, particularly **V17 (-0.3265), V14 (-0.3025), and V12 (-0.2606)**.
- Feature engineering should focus on **these top correlated features** for model training.

#### 4. Feature Distributions
- Most of the **V1-V28 features** are statistically centered around **0**, indicating that they are already standardized (likely from PCA transformation).
- The **distribution of transaction time** suggests that **fraud cases are not uniformly distributed across the day**. Further analysis can be done using **hourly fraud trends**.

#### 5. Skewness in Transaction Amount
- The **distribution of `Amount` is highly skewed**, with most transactions being of small amounts, but fraud transactions often involve **larger sums**.
- Applying **log transformation** may help stabilize variance and improve model performance.

#### 6. Outliers and Anomalies
- Features **V10, V12, and V14 show extreme values**, which might be **useful indicators for fraud detection**.
- Outlier removal or robust modeling techniques may improve fraud prediction accuracy.

---

### Fraud vs. Non-Fraud Distribution

![image](https://github.com/user-attachments/assets/367d5949-c3a9-41a6-845b-0e79ccc5218c)

#### **Class Imbalance Insights**
- The dataset is highly imbalanced, with **284,315 non-fraudulent transactions** and only **492 fraudulent transactions**.
- Fraudulent transactions make up **only 0.17%** of the total dataset, making fraud detection a challenging task.
- The extreme imbalance can lead to biased models that favor the majority class (non-fraudulent transactions).
- Standard machine learning models may **fail to detect fraud** effectively due to this imbalance.
- To address this, techniques like **oversampling the minority class (SMOTE), undersampling the majority class, or using weighted loss functions** may be required to improve model performance.

### Transaction Amount Distribution

| Distribution of Transaction Amount | Outlier Detection |
|------------------------------------|-------------------|
| ![Image 1](https://github.com/user-attachments/assets/1c90515d-2ed0-4f1b-87be-2b0d501bb40b) | ![Image 2](https://github.com/user-attachments/assets/b727ea11-bb87-4d2f-a749-bfe728ed1d1f) |

#### Skewness in Transaction Amount

- The majority of transactions are concentrated at lower amounts, while a few transactions have extremely high values.
- A significant number of outliers exist, suggesting rare but high-value transactions. These could indicate anomalies or potential fraudulent activities.
- The distribution appears to be **highly skewed**, meaning that most transactions are of smaller amounts with a long tail of larger transactions.

### Identifying Outliers

- **Fraudulent outliers:** 91  
- **Non-fraudulent outliers:** 31,813  

### Comparing the Transaction Amounts of Fraud vs. Non-Fraud Transactions  

#### Fraudulent vs. Non-Fraudulent Transactions Summary  

<table>
<tr>
    <th>Fraudulent Transactions Summary</th>
    <th>Non-Fraudulent Transactions Summary</th>
</tr>
<tr>
    <td>

| Statistic | Value |
|-----------|--------------|
| **Count** | 492.000000 |
| **Mean** | 122.211321 |
| **Standard Deviation (std)** | 256.683288 |
| **Minimum (min)** | 0.000000 |
| **25th Percentile (Q1)** | 1.000000 |
| **Median (50%)** | 9.250000 |
| **75th Percentile (Q3)** | 105.890000 |
| **Maximum (max)** | 2125.870000 |

</td>
    <td>

| Statistic | Value |
|-----------|--------------|
| **Count** | 284315.000000 |
| **Mean** | 88.291022 |
| **Standard Deviation (std)** | 250.105092 |
| **Minimum (min)** | 0.000000 |
| **25th Percentile (Q1)** | 5.650000 |
| **Median (50%)** | 22.000000 |
| **75th Percentile (Q3)** | 77.050000 |
| **Maximum (max)** | 25691.160000 |

</td>
</tr>
</table>


### Insights from the Transaction Amount Analysis  

#### Fraudulent Transactions Tend to Have Higher Median Amounts  
- The **median** transaction amount for fraudulent transactions is **9.25**, whereas for non-fraudulent transactions, it's **22.00**.  
- This suggests that fraudsters often process **lower amounts** on average to avoid detection.  

#### Fraudulent Transactions Have a Much Lower Maximum Value  
- The **highest** fraudulent transaction amount is **2,125.87**, while for non-fraudulent transactions, it's **25,691.16**.  
- This implies that **extreme high-value transactions are usually legitimate** rather than fraudulent.  

#### Fraudulent Transactions Have a Higher Standard Deviation Relative to Their Mean  
- **Std for fraud:** 256.68, **Std for non-fraud:** 250.10  
- Even though both groups have similar standard deviations, fraudulent transactions have a **higher variance relative to their mean** (122.21 for fraud vs. 88.29 for non-fraud).  
- This suggests that fraud transactions are **more dispersed**, making them harder to detect using simple threshold-based methods.  

#### Fraudulent Transactions Are More Concentrated in the Lower Ranges  
- **75% of fraudulent transactions** are below **105.89**, while for non-fraudulent transactions, **75% are below 77.05**.  
- This indicates that **most fraud occurs in relatively small amounts**, likely an attempt to bypass security measures.  










## 📂 Project Structure
```
├── data/               # Dataset and preprocessed data
├── notebooks/          # Jupyter notebooks for analysis
├── src/               # Source code for model training and deployment
│   ├── preprocessing.py  # Data cleaning and feature engineering
│   ├── train.py         # Model training script
│   ├── predict.py       # Model inference script
│   ├── api.py           # Flask/FastAPI application
├── models/            # Saved machine learning models
├── reports/           # Visualizations and analysis reports
├── README.md          # Project documentation
```

## 📊 Data Processing
1. **Data Cleaning:** Handle missing values, outliers, and normalization.
2. **Feature Engineering:** Extract meaningful features for better model performance.
3. **Exploratory Data Analysis (EDA):** Visualize fraud trends and data distribution.

## 🤖 Model Development
1. Train multiple ML models and evaluate using precision, recall, F1-score, and AUC-ROC.
2. Optimize performance using hyperparameter tuning.
3. Select the best-performing model for deployment.

## 🚀 Deployment & Automation
1. Deploy the model as an API using Flask or FastAPI.
2. Store transaction data in an SQL database.
3. Integrate cloud-based solutions (AWS/GCP/Azure) for scalability.

## 📈 Visualization & Monitoring
- Develop an interactive dashboard in Tableau/Power BI.
- Track fraud trends and model performance in real time.
- Set up automated alerts for flagged transactions.

## 🔧 Installation
```bash
# Clone the repository
git clone https://github.com/your-username/fraud-detection.git
cd fraud-detection

# Create and activate virtual environment
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run the API
python src/api.py
```

## 📝 Usage
- Train the model: `python src/train.py`
- Make predictions: `python src/predict.py`
- Start API: `python src/api.py`

## 🎯 Future Enhancements
- Integrate deep learning techniques for improved fraud detection.
- Implement real-time streaming with Kafka.
- Expand dataset for better generalization.

## 🤝 Contributing
Feel free to open issues or submit pull requests for improvements.

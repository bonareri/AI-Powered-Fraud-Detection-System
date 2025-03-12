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
1. Data preprocessing and exploratory data analysis (EDA)
2. Feature engineering and selection
3. Model training and evaluation (ML & deep learning approaches)
4. Performance optimization and hyperparameter tuning
5. Model deployment

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

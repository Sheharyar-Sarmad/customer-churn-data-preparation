# Customer Churn Data Preparation

## 📋 Project Overview

This project focuses on preparing customer churn data for machine learning modeling. The goal is to clean, preprocess, and engineer features from raw customer data to create a clean, model-ready dataset.

## 🎯 Objectives

- Perform Exploratory Data Analysis (EDA) to understand data patterns
- Clean and preprocess data for ML algorithms
- Engineer meaningful features to improve model performance
- Prepare data for model training (train/test split)
- Establish a reproducible data preparation pipeline

## 📊 Dataset Description

### Raw Data
- **Source:** Synthetic customer churn dataset
- **Samples:** 1,000 customers
- **Features:** 12 columns
- **Target Variable:** `churned` (Yes/No)

### Features
| Feature | Type | Description |
|---------|------|-------------|
| `customer_id` | Identifier | Unique customer ID |
| `age` | Numerical | Customer age (18-70) |
| `gender` | Categorical | Male/Female |
| `income` | Numerical | Annual income |
| `subscription_type` | Categorical | Basic/Standard/Premium |
| `contract_length` | Categorical | Monthly/Quarterly/Yearly |
| `payment_method` | Categorical | Credit Card/PayPal/Bank Transfer/Cash |
| `monthly_usage_hours` | Numerical | Hours of service usage per month |
| `customer_service_calls` | Numerical | Number of support calls |
| `has_loyalty_card` | Categorical | Yes/No |
| `region` | Categorical | North/South/East/West |
| `churned` | Target | Yes/No |

## 🔧 Data Processing Steps

### 1. Exploratory Data Analysis (EDA)
- Checked for missing values (none found)
- Analyzed feature distributions
- Examined correlations with target variable
- Visualized patterns and relationships

### 2. Data Cleaning
- No missing values to handle
- Removed duplicate entries (none found)
- Fixed data types (converted categoricals)

### 3. Preprocessing
- **Encoding Categorical Variables:**
  - Binary columns: Mapped to 0/1 (e.g., `has_loyalty_card`)
  - Multi-category columns: One-hot encoding (e.g., `subscription_type`)
  - Target variable: Encoded as 0/1 (`churned` → 0/1)

- **Feature Scaling:**
  - Applied StandardScaler to numerical features
  - Features scaled: `age`, `income`, `monthly_usage_hours`, `customer_service_calls`

### 4. Feature Engineering
Created new features to capture more information:

| New Feature | Formula | Purpose |
|-------------|---------|---------|
| `engagement_score` | usage_hours / (calls + 1) | Measure customer engagement |
| `high_value_customer` | Premium AND high income | Identify valuable customers |
| `risk_score` | Weighted risk factors | Quantify churn risk |
| `usage_per_age` | usage_hours / age | Usage relative to age |
| `low_engagement` | usage_hours < 30 | Flag inactive customers |

### 5. Feature Selection
- Analyzed correlations with target
- Selected features with meaningful relationships
- Dropped `customer_id` (not useful for prediction)

### 6. Train/Test Split
- **Training Set:** 80% (800 samples)
- **Test Set:** 20% (200 samples)
- Used stratification to maintain churn rate distribution

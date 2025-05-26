# Credit Risk Modeling Pipeline

This repository contains an end-to-end pipeline for credit risk modeling using loan application, account, and enquiry data. The process includes data loading, sanity checks, EDA, feature engineering, model training, and predictions.

---

## 1. Loading Data

- Flattened nested JSON structures to extract data into clean, analyzable DataFrames.

---

## 2. Data Sanity Checks

### 2.1 Data Shapes and UID Counts
- Verified shapes of all DataFrames.
- Counted unique `UID` values to ensure consistency.

### 2.2 Missing Values
- Identified missing values across all columns.

### 2.3 Duplicate Rows
- Checked and handled duplicate records.

### 2.4 UID Overlap Across Datasets
- Cross-checked UID overlaps between flag data and account/enquiry data for consistency.

---

## 3. Exploratory Data Analysis (EDA)

### 3.1 Flags Dataset
- Examined target variable distribution.
- Analyzed `name_contract_type` distribution across target classes.

### 3.2 Accounts Dataset
- Validated loan amount and overdue values for negative entries.
- Verified min/max open and close dates.
- Flagged cases where `closed_date < open_date`.
- Analyzed anomalies in the `payment_string` column.
- Used boxplots and histograms to identify outliers in loan amount and amount overdue.

### 3.3 Enquiry Data
- Checked for negative enquiry amounts.
- Evaluated range of enquiry dates.

### 3.4 Data Cleaning
- Consolidated repeated cleaning logic into reusable functions.

---

## 4. Feature Engineering

- Created UID-level features separately for enquiry and account data.
- Merged derived features with the target (flags) dataset.
- Encapsulated logic into reusable functions for easy application on test data.

---

## 5. Feature Selection (Optional)

- Implemented RFE-based feature elimination using LightGBM.
- Removed the least important feature iteratively and monitored AUC-ROC changes.

---

## 6. Model Training

- Trained baseline models:
  - LightGBM Classifier
  - CatBoost Classifier

---

## 7. Hyperparameter Tuning

- Used Optuna to find optimal hyperparameters for model performance improvement.

---

## 8. Test Predictions

- Applied trained models to test data for inference and final predictions.

---

## Folder Structure


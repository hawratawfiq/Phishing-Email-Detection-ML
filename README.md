# 🛡️ Machine Learning-Based Email Phishing Detection

## 📌 Project Overview

This project implements a **machine learning-based phishing email detection system** using the CEAS08 dataset (Phishing Email Curated Dataset).

The goal is to classify emails as:

* **Legitimate (0)**
* **Phishing (1)**

The project extracts structural and behavioral features from email content and trains multiple supervised learning models to detect phishing attempts accurately.

---

## 📂 Dataset

* **Dataset:** CEAS08 Phishing Email Dataset from Zenodo
* **Original Size:** 71,487 emails
* **After Cleaning:** 39,154 emails
* **Class Distribution:**

  * 55.8% Phishing
  * 44.2% Legitimate
 
Due to file size limitations, the dataset is not included in this repository.
It can be downloaded from:
https://zenodo.org/record/1229831

### Features Used from Dataset:

* `sender`
* `subject`
* `body`
* `label`

---

## 🧹 Data Preprocessing

* Removed rows with missing subject/body
* Combined subject + body into one text column
* Standardized sender addresses
* Extracted URLs from email text
* Cleaned and saved as `modified_dataset.csv`

---

## ⚙️ Feature Engineering

Three main feature groups were engineered:

### 🔗 1. URL-Based Features

* Number of URLs
* Maximum URL length
* Suspicious TLD detection (.ru, .xyz, etc.)
* IP address usage in URL
* Presence of @ symbol
* Multiple subdomains
* Dash in domain
* Hex strings in URL

### 📧 2. Header / Sender Features

* Free email provider detection (gmail, etc.)
* Sender domain length
* Numbers in domain
* Dashes in domain

### 📝 3. Text-Based Features

* Urgent word count (e.g., "urgent", "verify")
* Exclamation mark count
* Uppercase ratio
* Total text length

All features were combined into a final matrix:

```
final_features.csv
```

---

## 🤖 Models Trained

Three supervised learning models were trained:

1. **Logistic Regression**
2. **Random Forest**
3. **XGBoost**

Train/Test split:

* 80% Training
* 20% Testing
* Stratified sampling

---

## 📊 Model Performance

| Model               | Accuracy   | Precision  | Recall     | F1 Score   |
| ------------------- | ---------- | ---------- | ---------- | ---------- |
| Logistic Regression | 89.19%     | 88.13%     | 93.17%     | 90.58%     |
| Random Forest       | **97.79%** | **98.21%** | **97.82%** | **98.01%** |
| XGBoost             | 97.60%     | 98.05%     | 97.64%     | 97.84%     |

### ✅ Best Model: Random Forest

Random Forest achieved the highest overall performance and was selected as the final deployed model.

---

## 🛠️ Technologies Used

* Python
* Pandas, NumPy
* Scikit-learn
* XGBoost
* Matplotlib & Seaborn
* tldextract
* joblib
* Jupyter Notebook








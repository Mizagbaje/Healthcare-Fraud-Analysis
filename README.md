#  Healthcare Provider Fraud Detection
This project analyzes healthcare claims data to identify patterns linked to potentially fraudulent providers.  We combine patient, claim, and provider data, engineer meaningful features, and build a machine learning model to predict fraud risk.



# 📑 Table of Contents



1. [Project Overview](#project-overview)  
2. [Dataset Description](#dataset-description)  
3. [Tools & Technologies Used](#tools--technologies-used)  
4. [Data Preparation](#data-preparation)  
5. [Feature Engineering](#feature-engineering)  
6. [Machine Learning Model](#machine-learning-model)  
7. [Model Performance](#model-performance)  
8. [Feature Importance](#feature-importance)  
9. [Key Takeaways](#key-takeaways)  
10. [Future Improvements](#future-improvements)  
11. [How to Run This Project](#how-to-run-this-project)  
12. [Author](#author)









### Project Overview

Healthcare fraud is a major challenge that leads to billions of dollars in losses each year. In this project, we analyze healthcare claims data to identify patterns associated with potentially fraudulent healthcare providers and build a machine learning model to help detect fraud.

The goal is to use **data analytics and predictive modeling** to distinguish between fraudulent and non-fraudulent providers based on their billing and patient activity.

---

### Dataset Description

The dataset consists of multiple tables representing different aspects of healthcare claims:

| File                  | Description                                           |
| --------------------- | ----------------------------------------------------- |
| **Beneficiary Data**  | Patient demographics and chronic condition indicators |
| **Inpatient Claims**  | Claims for hospital admissions                        |
| **Outpatient Claims** | Claims for outpatient services                        |
| **Provider Data**     | Provider IDs and fraud labels (Yes/No)                |

Each claim is linked to a **beneficiary (patient)** and a **provider**, allowing us to combine patient, claim, and provider-level information.

---

### Tools & Technologies Used

* **Python**
* **Pandas** – Data cleaning and transformation
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Scikit-learn** – Machine learning modeling

---

### Data Preparation

The following preprocessing steps were performed:

1. **Merged inpatient and outpatient claims** into one dataset
2. **Joined beneficiary data** to include patient-level information
3. **Joined provider data** to attach fraud labels
4. Aggregated claim-level data to create **provider-level features**
5. Handled **missing values** using mean imputation
6. Converted fraud labels:

   * `Yes → 1`
   * `No → 0`

---

### Feature Engineering

To improve fraud detection, several provider-level features were created:

* **Average Claim Amount**
* **Average Deductible Paid**
* **Total Number of Claims**
* **Total Reimbursed Amount**
* **Total Deductible Amount**
* **Number of Unique Patients**

These features help capture unusual billing behavior and patient patterns that may indicate fraud.

---

### Machine Learning Model

A **Random Forest Classifier** was trained to predict whether a provider is potentially fraudulent.

### Why Random Forest?

* Handles non-linear patterns well
* Works effectively with structured/tabular data
* Provides feature importance for interpretability

The dataset was split into:

* **80% Training**
* **20% Testing**

Class imbalance (fraud is rare) was addressed using **balanced class weights**.

---

### Model Performance

| Metric        | Non-Fraud (0) | Fraud (1) |
| ------------- | ------------- | --------- |
| **Precision** | 0.94          | 0.75      |
| **Recall**    | 0.99          | 0.40      |
| **F1-Score**  | 0.96          | 0.52      |

### Interpretation

* The model performs very well at identifying **non-fraudulent providers**
* Fraud detection recall is moderate, which is common in real-world fraud detection problems due to class imbalance
* Precision for fraud is strong, meaning flagged providers are likely to truly be suspicious

---

### Feature Importance

Feature importance analysis showed that the most influential indicators of fraud include:

* Total reimbursed amount
* Number of claims
* Unique patient count

These suggest that unusual billing volume and patient patterns are key signals in fraud detection.

---

### Key Takeaways

* Healthcare fraud detection requires **careful feature engineering**
* **Provider-level aggregation** is critical for meaningful insights
* Handling **imbalanced data** is essential in fraud analytics
* Even simple models can provide valuable signals when built on well-prepared data

---

### Future Improvements

* Add more behavioral features (e.g., diagnosis diversity, procedure patterns)
* Use advanced imbalance techniques like **SMOTE**
* Try gradient boosting models (XGBoost, LightGBM)
* Deploy as a simple fraud risk scoring dashboard

---

### How to Run This Project

1. Clone the repository
2. Install required libraries:

   ```bash
   pip install pandas numpy matplotlib scikit-learn
   ```
3. Place dataset CSV files in the project folder
4. Open the Jupyter Notebook and run cells sequentially

---

### Author

**Oseni Monsurat Olabisi**
Healthcare Data Analyst | Data Analytics & Machine Learning Enthusiast



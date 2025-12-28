[README-customer-churn.md](https://github.com/user-attachments/files/24357604/README-customer-churn.md)
# Customer Churn Classification for E-commerce

## Project Overview
This project builds a customer churn prediction model using transactional data from a UK-based e-commerce retailer. The goal is to identify customers at risk of churning and uncover the key behavioral drivers behind churn to support data-driven retention strategies.

Using customer-level features derived from transaction data, multiple classification models were evaluated, with Random Forest emerging as the best performer.

---

## Business Problem
Customer acquisition is expensive, and retaining existing customers is critical for long-term profitability. However, not all customers exhibit the same churn risk.

This project aims to:

1. Predict which customers are likely to churn
2. Identify the strongest drivers of churn
3. Provide actionable insights to reduce customer loss

Churn will be defined as a customer who did not make a purchase within 90 days of December 9, 2011.

---

## Data Description
- **Source:** UCI Machine Learning Repository
- **Time Period:** December 1, 2010 – December 9, 2011
- **Raw Records:** 541,909 transaction-level rows
- **Customers After Cleaning:** 4,364
- **Churn Rate:** ~33%

The following features were engineered:
- Total items bought
- Total money spent
- Number of invoices
- Number of canceled and non-canceled orders
- Invoice statistics (mean, std dev, max)
- Purchase volume statistics
- Country (UK indicator)

Transactional data was aggregated to customer-level granularity prior to modeling.

--- 

## Methodology
- Cleaned data and removed missing customer IDs
- Engineered customer-level behavioral features
- Conducted EDA to examine skewness and correlations
- Split data into train (60%) / validation (20%) / test (20%)
- Scaled features to [0,1]
- Balanced classes using SMOTE + Tomek Links
- Evaluated multiple models:
  - Random Forest
  - XGBoost
  - K-Nearest Neighbors
  - Stacking with voting
- Tuned hyperparameters using cross-validation
- Optimized classification threshold using Youden’s J statistic
- Prioritized Recall and ROC AUC to minimize false negatives 

---

## Results
The Random Forest model performed best, achieving the following metrics:

- Recall: 84.8%
- ROC AUC: 79.7%
- Accuracy: 67.0%
- Precision: 50.8%
- F1 Score: 63.5%
- PR AUC: 64.2%

Train vs test performance indicated strong generalization.

Permutation feature importance revealed:

1. Total items bought
2. Total money spent

Partial dependence analysis showed:

1. Customers buying < 200 items or spending < $300 had churn rates above 50%
2. Customers buying > 800 items or spending > $900 had churn rates between 10-14%

---

## Key Insights
- High-value customers are significantly less likely to churn
- Low-spending, low-volume customers represent the highest churn risk
- Retention efforts should prioritize low-value customers rather than already loyal ones

**Recommendations:**
Target low-spending customers with:
1. Personalized discounts
2. Coupons
3. Loyalty incentives

These interventions are low-cost relative to the cost of customer churn.

---

## Tools & Technologies
- **Python**
- **pandas**, **NumPy** – data manipulation  
- **matplotlib**, **seaborn** – visualization  
- **scikit-learn**, **XGBoost** – machine learning models  
- **Jupyter Notebook** – analysis and documentation  

---

## Repository Structure
```
├── Customer Churn E-commerce Online Retail Report.pdf
├── Customer Churn Prediction on E-commerce Data.ipynb
├── UCI Online Retail Dataset.xlsx
├── README.md
```

---

## Next Steps
- Incorporate advertising exposure features (e.g., ad watch time, channel)
- Add temporal features capturing purchase recency trends
- Apply stronger regularization or pruning to reduce overfitting
- Evaluate cost-sensitive learning approaches

---

## Contact
If you’d like to discuss this project or explore related work, feel free to connect with me on LinkedIn or view my other repositories.

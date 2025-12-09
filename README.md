# Causal-Analysis-of-Discount-on-Sales

## Overview
This project investigates the causal effect of discounts on sales using the Sample Superstore dataset. We aim to answer the question:

**"Do discounts increase sales, and by how much?"**

Two causal inference methods are used:
1. **Propensity Score Matching (PSM)**  
2. **Causal Regression (OLS with covariates)**


## Dataset
- **Source:** Sample Superstore dataset
- **Entries:** 9,994
- **Columns:** 21, including Sales, Quantity, Discount, Profit, Product details, Customer segment, Region, Ship Mode, and Order dates.


## Methods
### 1. Data Preprocessing
- Parsed dates for order and shipment.
- Created features: `order_year`, `order_month`, `order_weekday`.
- Created binary treatment variable: `Treated = 1 if Discount > 0 else 0`.
- Generated dummies for categorical variables: Category, Sub-Category, Segment, Region, Ship Mode.
- Scaled numeric covariates for modeling.

### 2. Propensity Score Matching (PSM)
- Estimated propensity scores using logistic regression.
- Applied 1:1 nearest neighbor matching.
- Checked covariate balance using standardized mean differences.
- Estimated Average Treatment Effect on the Treated (ATT).
- Bootstrapped 95% confidence intervals for robustness.

### 3. Causal Regression
- Built OLS regression with robust standard errors.
- Included numeric covariates and all dummies.
- Estimated discount effect controlling for other factors.

---

## Key Results
- **PSM ATT:** \$68.8 (95% CI: \$54.5 – \$84.7)  
- **OLS Discount Coefficient:** \$77.6 (p = 0.227, not significant due to multicollinearity)  
- Discounts have a positive and meaningful effect on sales.


## Libraries
- pandas, numpy  
- scikit-learn (LogisticRegression, StandardScaler, NearestNeighbors)  
- statsmodels (OLS, robust standard errors)  
- scipy  

---


## Author
**James Kingsley Philip**  
Data Scientist | Causal Analysis | Python, ML, Analytics

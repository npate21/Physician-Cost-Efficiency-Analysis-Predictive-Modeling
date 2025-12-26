# Physician Cost Efficiency Analysis Using BCBS Medicare Data

## Overview
This project analyzes physician-level healthcare data provided by **Blue Cross Blue Shield (BCBS)** and enriched with Medicare features to understand variation in **physician cost efficiency**. The analysis combines exploratory data analysis, responsible feature selection, and predictive modeling to support **data-driven decision-making for healthcare insurance organizations**.

The project is designed as a **decision-support analytics tool**, not as an evaluation or ranking system for individual physicians.

---

## Business Problem
BCBS faces meaningful variation in healthcare costs across physicians treating similar patient populations. Understanding whether these differences are driven by **patient risk, utilization patterns, or systemic factors** is essential for:
- Cost management and forecasting
- Value-based care initiatives
- Provider engagement and education strategies
- Identifying opportunities for systemic improvement

This project addresses that challenge by analyzing physician efficiency patterns at an aggregate level.

---

## Data Description
- **Unit of analysis:** Individual physicians  
- **Target variable:** `physician_efficiency`  
  - Continuous, normalized efficiency score  
  - Lower values indicate more cost-efficient care  
  - Higher values indicate less cost-efficient care  
- **Feature categories include:**
  - Physician demographics and experience
  - Education and credentials
  - Geographic practice location
  - Medicare patient volume
  - Patient risk scores
  - Engineered features derived from Medicare data  

The dataset contains missing values and engineered variables, requiring careful validation to avoid bias and data leakage.

---

## Methodology

### 1. Exploratory Data Analysis (EDA)
- Examined the distribution of physician efficiency across specialties
- Analyzed relationships between efficiency, experience, geography, and patient risk
- Identified variables that appeared overly correlated with the target and required further scrutiny

### 2. Feature Evaluation & Data Integrity
- Removed non-predictive identifiers (e.g., physician ID)
- Excluded leaky features derived from the target variable
- Preserved the continuous nature of physician efficiency
- Handled missing values using imputation rather than row deletion

### 3. Predictive Modeling
- Framed the problem as a **regression task**
- Built a **Decision Tree regression model** to estimate physician efficiency
- Selected the model for interpretability and ability to capture non-linear relationships
- Evaluated performance using regression-appropriate metrics:
  - Mean Absolute Error (MAE)
  - Root Mean Squared Error (RMSE)
  - R² (coefficient of determination)

### 4. Model Validation
- Performed **5-fold cross-validation** to confirm generalization
- Observed consistently high R² values with very low variance across folds
- Validation results reduced the likelihood of overfitting or residual data leakage

---

## Model Performance

**Test Set Metrics**
- **MAE:** 0.0074  
- **RMSE:** 0.0092  
- **R²:** 0.9993  

**Cross-Validation**
- **Mean R²:** 0.9993  
- **Standard Deviation:** 0.00003  

These results indicate strong explanatory power and stable performance across data splits.

---

## Key Findings
- Physician cost efficiency is primarily influenced by **patient risk and Medicare utilization patterns**
- Cost variation is largely **systemic**, not attributable to individual physician behavior alone
- Non-linear relationships highlight thresholds where patient complexity significantly impacts costs
- Certain engineered features can artificially inflate performance if not carefully excluded

---

## Business Impact & Use Case
BCBS can use insights from this analysis to:
- Identify systemic cost drivers across physician populations
- Support value-based care and reimbursement strategies
- Inform provider engagement and resource allocation
- Prioritize areas for deeper operational or clinical review
- Make fairer, data-informed cost management decisions

---

## Conclusion
The Decision Tree regression model demonstrates strong and stable performance (**MAE = 0.0074, RMSE = 0.0092, R² = 0.9993**), making it well-suited for identifying key drivers of physician cost efficiency. This project illustrates how responsible analytics can support BCBS in understanding cost variation and making informed, ethical, data-driven business decisions.

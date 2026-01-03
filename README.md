# Physician Cost Efficiency Analysis Using BCBS Medicare Data

## Overview
This project analyzes physician-level healthcare data provided by **Blue Cross Blue Shield (BCBS)** and enriched with Medicare features to understand variation in **physician cost efficiency**. The analysis combines exploratory data analysis, rigorous data leakage detection, and predictive modeling to support **data-driven decision-making for healthcare insurance organizations**.

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
- **Dataset size:** 7,393 physicians across 20 features
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
- Examined the distribution of physician efficiency across 68 medical specialties
- Analyzed relationships between efficiency, patient risk, and utilization patterns
- Identified variables that appeared overly correlated with the target and required further scrutiny

### 2. Data Leakage & Feature Selection
- Removed non-predictive identifiers (e.g., physician ID)
- Excluded leaky features derived from the target variable
- Preserved the continuous nature of physician efficiency
- Handled missing values using imputation rather than row deletion

### 3. Predictive Modeling
- Framed the problem as a **regression task**
- Built a **Random Forest model** to estimate physician efficiency
- Selected the model for interpretability and ability to capture non-linear relationships between patient risk and costs
- Evaluated performance using regression-appropriate metrics:
  - Mean Absolute Error (MAE)
  - Root Mean Squared Error (RMSE)
  - R² (coefficient of determination)

### 4. Model Evaluation
- Train-test split: 75/25
- Validation: 5-fold cross-validation to ensure generalization
- Metrics: MAE, RMSE, R² for comprehensive performance assessment

---

## Model Performance

**Test Set Metrics**
- **MAE:** 0.2190  
- **RMSE:** 0.3040 
- **R²:** 0.2609  

**Cross-Validation**
- **Mean R²:** 0.2733  
- **Standard Deviation:** 0.0254 

These results indicate moderate predictive power with consistent performance across data splits. In the healthcare context, where data exhibits high variability due to complex interacting factors, an R² of approximately 0.27 represents meaningful predictive capability.

---

## Key Findings
The Random Forest model identified the following key drivers of physician cost efficiency:
- Patient complexity measures (HCC risk scores, Medicare utilization patterns)
- Medicare patient volume
- Engineered feature 3 (patient complexity indicator)

---

## Business Impact & Use Case
BCBS can use insights from this analysis to:
- **Value-based care programs:** Design fair reimbursement models that account for patient risk factors, ensuring physicians treating higher-complexity populations are not penalized
- **Resource allocation:** Identify and prioritize high-risk patient populations that require additional support and resources to improve cost efficiency
- **Provider engagement:** Focus education and intervention strategies on systemic factors (care coordination, utilization management) rather than individual physician performance
- **Cost forecasting:** Leverage patient risk scores and Medicare utilization patterns as key predictors for more accurate healthcare cost projections
- **Policy development:** Create evidence-based policies that recognize cost variation is largely driven by patient complexity, not physician behavior, leading to fairer and more effective cost management decisions

---

## Conclusion
The Random Forest regression model demonstrates meaningful predictive performance (**MAE = 0.2190, RMSE = 0.3040, R² = 0.2609**), making it well-suited for identifying key drivers of physician cost efficiency. This project illustrates how responsible analytics—including rigorous data leakage detection—can support BCBS in understanding cost variation and making informed, ethical, data-driven business decisions.

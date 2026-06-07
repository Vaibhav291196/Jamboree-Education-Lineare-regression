# 🎓 Jamboree Education - Graduate Admission Prediction

## Overview

This project analyzes factors influencing graduate school admissions and develops a predictive model to estimate a student's **Chance of Admission** based on academic and profile-related attributes.

The objective is to identify the key factors affecting admission probability and build an interpretable regression model that can assist students in evaluating their chances of securing admission to international universities.

---

## Dataset Features

| Feature           | Description                        |
| ----------------- | ---------------------------------- |
| GRE Score         | Graduate Record Examination score  |
| TOEFL Score       | English proficiency test score     |
| University Rating | Rating of undergraduate university |
| SOP               | Statement of Purpose strength      |
| LOR               | Letter of Recommendation strength  |
| CGPA              | Undergraduate GPA                  |
| Research          | Research experience (0/1)          |
| Chance of Admit   | Target Variable                    |

---

## Project Workflow

### 1. Data Preprocessing

* Removed outliers from the target variable using the IQR method.
* Cleaned and standardized numerical features using StandardScaler.
* Performed train-test split (75:25 ratio).
* Checked feature distributions and data quality.

### 2. Exploratory Data Analysis

* Generated correlation matrix and heatmaps.
* Studied relationships between admission probability and predictor variables.
* Identified highly influential features.

### Key Correlations with Admission Probability

| Feature           | Correlation |
| ----------------- | ----------- |
| CGPA              | 0.882       |
| GRE Score         | 0.803       |
| TOEFL Score       | 0.786       |
| SOP               | 0.687       |
| University Rating | 0.678       |
| LOR               | 0.629       |
| Research          | 0.540       |

**Observation:** CGPA and GRE Score showed the strongest positive relationship with admission chances.

---

## Model Development

### Linear Regression (OLS)

A Multiple Linear Regression model was built using StatsModels to estimate admission probability.

#### Initial Model Findings

* R² Score: 0.830
* Adjusted R² Score: 0.827

Statistical significance testing showed that:

* SOP
* University Rating

had p-values greater than 0.05 and contributed minimally to prediction performance.

### Feature Selection

The following features were retained:

* GRE Score
* TOEFL Score
* LOR
* CGPA
* Research

The model was retrained using only statistically significant predictors.

---

## Regression Assumption Validation

To ensure reliability of the linear regression model, all standard assumptions were tested.

### ✅ Linearity

Strong positive correlations observed between predictors and target.

### ✅ No Multicollinearity

Variance Inflation Factor (VIF) values remained below 5 for all variables.

| Feature     | VIF  |
| ----------- | ---- |
| CGPA        | 4.73 |
| GRE Score   | 4.41 |
| TOEFL Score | 4.05 |
| LOR         | 1.67 |
| Research    | 1.48 |

### ✅ Normal Distribution of Errors

Residual histogram indicated approximately normal error distribution.

### ✅ Homoscedasticity

Residual scatterplots and Goldfeld-Quandt test confirmed constant variance.

### ✅ No Autocorrelation

Dataset is not time-series based; autocorrelation assumption is not applicable.

---

## Model Performance

| Metric                    | Value  |
| ------------------------- | ------ |
| R² Score                  | 0.83   |
| Adjusted R² Score         | 0.83   |
| Mean Squared Error (MSE)  | 0.0038 |
| Mean Absolute Error (MAE) | 0.0456 |

The model explains approximately **83% of the variance** in admission probability, indicating strong predictive performance.

---

## Important Findings

### Most Influential Factors

1. **CGPA** emerged as the strongest predictor of admission probability.
2. **GRE Score** was the second most influential factor.
3. TOEFL Score and LOR also contributed significantly.
4. Research experience had a positive but relatively smaller effect.
5. SOP and University Rating showed limited statistical significance in the final model.

### Practical Insight

Students seeking to improve admission chances should primarily focus on:

* Maintaining a high CGPA
* Achieving a strong GRE score
* Strengthening recommendation letters
* Gaining research experience

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-Learn
* StatsModels

---

## Conclusion

This study demonstrates that a carefully validated Linear Regression model can effectively predict graduate admission probability. Academic performance indicators, particularly CGPA and GRE Score, play the most significant role in determining admission outcomes. The final model achieved strong explanatory power while satisfying all major regression assumptions, making it both interpretable and reliable.

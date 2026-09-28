# EDA Findings — Telco Customer Churn

## 1. Dataset Overview

The Telco Customer Churn dataset contains **7,043 rows and 21 columns**. It includes numerical and categorical customer information, with `Churn` as the binary target variable.

- **No Churn:** 5,174 customers (73.46%)
- **Churn:** 1,869 customers (26.54%)

The dataset is moderately imbalanced toward the `No Churn` class.

## 2. Data Quality and Preprocessing

The `TotalCharges` column was initially loaded as a text/object data type because some records contained blank strings. These blanks occur for customers with **tenure = 0**.

`TotalCharges` was converted to numeric values, and the resulting missing values were filled with **0**.

No duplicate rows were found.

## 3. Numerical Features and Skewness

The numerical features analyzed were:

- `SeniorCitizen`
- `tenure`
- `MonthlyCharges`
- `TotalCharges`

| Feature | Skewness |
|---|---:|
| tenure | 0.240 |
| MonthlyCharges | -0.221 |
| TotalCharges | 0.963 |

`TotalCharges` has the clearest positive/right skew. `tenure` has mild positive skewness, while `MonthlyCharges` is approximately symmetric with slight negative skewness.

For skewed distributions, extreme values can affect the mean, so the median may sometimes be more representative of a typical customer.

## 4. Churn Distribution

- **No Churn:** 73.46%
- **Churn:** 26.54%

The target variable is imbalanced. Because the churn class represents only about one-quarter of the dataset, accuracy alone can be misleading. Precision, recall, and F1-score should also be considered.

## 5. Bivariate Analysis

### Contract Type vs Churn

| Contract Type | Churn Rate |
|---|---:|
| Month-to-month | 42.71% |
| One year | 11.27% |
| Two year | 2.83% |

Customers with month-to-month contracts have a substantially higher churn rate than customers with one-year or two-year contracts. Contract type is therefore an important feature to consider when analyzing customer churn. This is an association and does not prove causation.

### Tenure vs Churn

| Churn Status | Mean Tenure | Median Tenure |
|---|---:|---:|
| No | 37.57 | 38 |
| Yes | 17.98 | 10 |

Customers who did not churn have much higher average and median tenure than customers who churned. This indicates that newer customers tend to have higher churn in this dataset. This relationship is associative and does not establish causation.

### Monthly Charges vs Churn

| Churn Status | Mean Monthly Charges | Median Monthly Charges |
|---|---:|---:|
| No | $61.27 | $64.43 |
| Yes | $74.44 | $79.65 |

Customers who churned had higher average and median monthly charges than customers who stayed. This suggests an association between higher monthly charges and churn, but does not establish that higher charges directly cause churn.

## 6. Correlation Analysis

Important numerical correlations include:

- `tenure` ↔ `TotalCharges`: approximately **0.83**
- `MonthlyCharges` ↔ `TotalCharges`: approximately **0.65**
- `tenure` ↔ `MonthlyCharges`: approximately **0.25**
- `SeniorCitizen` has generally weak correlations with the other numerical features.

The strong relationship between `tenure` and `TotalCharges` is expected because total charges accumulate over customer tenure. `TotalCharges` also overlaps with information from tenure and monthly charges and should therefore be considered carefully during later feature engineering.

## 7. Key Findings

1. The dataset contains 7,043 customers and 21 columns.
2. `No Churn` is the majority class at 73.46%.
3. `Churn` represents 26.54% of customers.
4. `TotalCharges` required conversion from text to numeric.
5. `TotalCharges` has the clearest right-skewed distribution.
6. Month-to-month customers have the highest observed churn rate.
7. Churned customers have substantially lower tenure.
8. Churned customers have higher monthly charges.
9. `tenure` and `TotalCharges` have a strong positive correlation of approximately 0.83.
10. Accuracy alone should not be used to evaluate future churn models.

## 8. Conclusion

The exploratory analysis identifies several features associated with customer churn, particularly contract type, tenure, and monthly charges. The class imbalance also demonstrates why future classification models should be evaluated using multiple metrics rather than accuracy alone.

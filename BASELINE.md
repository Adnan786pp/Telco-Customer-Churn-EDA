# Majority-Class Baseline — Telco Customer Churn

## 1. Baseline Approach

A majority-class baseline was created using Scikit-learn's `DummyClassifier` with the `most_frequent` strategy.

The classifier always predicts the majority class, which is **No Churn**, the majority class in the dataset.

## 2. Baseline Results

| Metric | Score |
|---|---:|
| Accuracy | 73.46% |
| Precision (Churn) | 0.00 |
| Recall (Churn) | 0.00 |
| F1 Score (Churn) | 0.00 |

## 3. Interpretation

The majority-class baseline achieves **73.46% accuracy** because 73.46% of customers belong to the `No Churn` class.

However, the classifier does not predict any customers as `Churn`. Therefore, precision, recall, and F1-score for the churn class are all 0.00.

This demonstrates why accuracy alone can be misleading. A classifier can achieve relatively high accuracy by always predicting the majority class while completely failing to identify customers who churn.

Therefore, future classification models should be evaluated using accuracy together with precision, recall, and F1-score, particularly for the `Churn` class.

## 4. Why This Baseline Matters

The majority-class baseline provides a simple benchmark for future classification models.

No train/test split was required at this stage because the Week 2 task focuses on exploratory data analysis and establishing a simple baseline rather than final predictive modeling.

## 5. Next Steps

Future models can be compared against this baseline after appropriate preprocessing, categorical encoding, feature selection, and train/test splitting.

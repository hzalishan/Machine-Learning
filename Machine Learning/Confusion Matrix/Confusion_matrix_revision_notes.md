# Confusion Matrix – Revision Notes (with Code)

## 1. What is a Confusion Matrix?
A **Confusion Matrix** is used to evaluate the performance of a **classification model**.

It compares:

➡ Actual values vs Predicted values

---

## 2. Structure of Confusion Matrix

|                | Predicted Positive | Predicted Negative |
|---------------|------------------|------------------|
| Actual Positive | True Positive (TP) | False Negative (FN) |
| Actual Negative | False Positive (FP) | True Negative (TN) |

---

## 3. Important Terms (Very Important 🔥)

### True Positive (TP)
Model predicted **Positive** and it was actually Positive.

### True Negative (TN)
Model predicted **Negative** and it was actually Negative.

### False Positive (FP)
Model predicted **Positive** but actually Negative.

➡ Type I Error

### False Negative (FN)
Model predicted **Negative** but actually Positive.

➡ Type II Error

---

# 4. Example

Actual:     [1, 0, 1, 1, 0]
Predicted:  [1, 0, 0, 1, 1]

TP = 2  
TN = 1  
FP = 1  
FN = 1

---

# 5. Evaluation Metrics

## Accuracy
Accuracy = (TP + TN) / Total

## Precision
Precision = TP / (TP + FP)

## Recall
Recall = TP / (TP + FN)

## F1 Score
F1 = 2 × (Precision × Recall) / (Precision + Recall)

---

# 6. Python Code (Important 🔥)

## 6.1 Confusion Matrix using sklearn

```python
from sklearn.metrics import confusion_matrix

# Actual and predicted values
y_true = [1, 0, 1, 1, 0]
y_pred = [1, 0, 0, 1, 1]

cm = confusion_matrix(y_true, y_pred)
print(cm)
```

Output:

[[TN FP]
 [FN TP]]

---

## 6.2 Classification Report

```python
from sklearn.metrics import classification_report

print(classification_report(y_true, y_pred))
```

This gives:
- Precision
- Recall
- F1-score

---

## 6.3 Visualization (Heatmap)

```python
import seaborn as sns
import matplotlib.pyplot as plt
from sklearn.metrics import confusion_matrix

cm = confusion_matrix(y_true, y_pred)

sns.heatmap(cm, annot=True, fmt='d')
plt.xlabel('Predicted')
plt.ylabel('Actual')
plt.show()
```

---

# 7. When to Use Which Metric?

- Accuracy → balanced data
- Precision → false positives matter
- Recall → false negatives matter
- F1 Score → balance both

---

# 8. Key Concepts Summary

Confusion Matrix → model evaluation tool

TP, TN, FP, FN → core components

Precision → correctness

Recall → detection ability

F1 Score → balance


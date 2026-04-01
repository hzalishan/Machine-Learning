# 📘 Voting Methods (Ensemble Learning) - Complete Revision Guide

## 🔹 What are Voting Methods?

Voting methods are **ensemble techniques** used to combine predictions from multiple models to improve accuracy.

👉 Idea: Multiple models → Combine predictions → Better final result

These methods are used in **Supervised Learning**.

---

## 🔹 Types of Voting Methods

1. Max Voting (Majority Voting)
2. Average Voting
3. Weighted Voting

---

# 1️⃣ Max Voting (Majority Voting)

## 🔸 Concept:

Used in **classification problems**.

👉 Final prediction = class with **maximum votes**.

### Example:

| Model   | Prediction |
| ------- | ---------- |
| Model 1 | Cat        |
| Model 2 | Dog        |
| Model 3 | Cat        |

👉 Final Output = **Cat** (majority)

---

## 🔸 Python Code:

```python
from sklearn.ensemble import VotingClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.svm import SVC

# Models
model1 = LogisticRegression()
model2 = DecisionTreeClassifier()
model3 = SVC(probability=True)

# Voting (Hard Voting)
voting = VotingClassifier(
    estimators=[('lr', model1), ('dt', model2), ('svc', model3)],
    voting='hard'
)

# Fit model
voting.fit(X_train, y_train)

# Predict
pred = voting.predict(X_test)
```

---

# 2️⃣ Average Voting

## 🔸 Concept:

Used in **regression problems**.

👉 Final output = average of predictions

### Example:

Predictions:

- Model 1 → 100
- Model 2 → 120
- Model 3 → 110

👉 Final Output = (100 + 120 + 110) / 3 = 110

---

## 🔸 Python Code:

```python
from sklearn.ensemble import VotingRegressor
from sklearn.linear_model import LinearRegression
from sklearn.tree import DecisionTreeRegressor

# Models
model1 = LinearRegression()
model2 = DecisionTreeRegressor()

# Voting Regressor
voting = VotingRegressor([
    ('lr', model1),
    ('dt', model2)
])

# Fit
voting.fit(X_train, y_train)

# Predict
pred = voting.predict(X_test)
```

---

# 3️⃣ Weighted Voting

## 🔸 Concept:

Each model is assigned a **weight** based on its importance.

👉 Better model → Higher weight

### Example:

| Model | Prediction | Weight |
| ----- | ---------- | ------ |
| M1    | 100        | 0.5    |
| M2    | 120        | 0.3    |
| M3    | 110        | 0.2    |

👉 Final Output:

(100×0.5 + 120×0.3 + 110×0.2)

---

## 🔸 Python Code:

```python
from sklearn.ensemble import VotingClassifier

voting = VotingClassifier(
    estimators=[('lr', model1), ('dt', model2), ('svc', model3)],
    voting='soft',
    weights=[2, 1, 1]
)

voting.fit(X_train, y_train)
pred = voting.predict(X_test)
```

👉 Note:

- Soft voting uses probabilities
- Weights control influence of each model

---

## 🔹 Hard Voting vs Soft Voting

| Type        | Description        |
| ----------- | ------------------ |
| Hard Voting | Uses class labels  |
| Soft Voting | Uses probabilities |

👉 Soft voting is usually more accurate.

---

## 🔹 Advantages of Voting Methods

- Improves accuracy
- Reduces overfitting
- Combines strengths of multiple models

---

## 🔹 Disadvantages

- Computationally expensive
- Needs multiple models
- Complex to tune

---

## 🔹 Important Interview Points

- Voting = Ensemble method
- Used in supervised learning
- Hard voting → classification
- Average voting → regression
- Weighted voting → improved performance

---

## 🔹 Final Summary

Voting Methods:

- Combine multiple models
- Improve prediction accuracy
- Work in supervised learning

👉 Simple but powerful ensemble technique.

---

**End of Notes ✅**


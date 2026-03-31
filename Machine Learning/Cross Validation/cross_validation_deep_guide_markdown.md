# 📘 Cross Validation - Complete Revision Guide (English)

## 🔹 What is Cross Validation?
Cross Validation is a technique used to evaluate the performance of machine learning models.

Normally, we split data into training and testing sets (e.g., 80/20). The problem with this approach is that the result depends on a single split.

👉 Cross Validation solves this by:
- Creating multiple splits
- Training and testing the model on each split
- Taking the average performance

---

## 🔹 Why Cross Validation is Important?

- Helps detect overfitting
- Gives a better estimate of real-world performance
- Works well with small datasets

---

## 🔹 Types of Cross Validation

---

## 1️⃣ K-Fold Cross Validation

### 🔸 Concept:
The dataset is divided into **K equal parts (folds)**.

Example: K = 5

Steps:
1. Use 1 fold as test, remaining 4 as training
2. Repeat 5 times (each fold becomes test once)
3. Compute average performance

### 🔸 Diagram (Conceptual):
```
Fold 1: [Test] [Train] [Train] [Train] [Train]
Fold 2: [Train] [Test] [Train] [Train] [Train]
...
```

### 🔸 Python Code:
```python
from sklearn.model_selection import KFold
from sklearn.linear_model import LinearRegression
from sklearn.datasets import load_boston
from sklearn.metrics import mean_squared_error
import numpy as np

# Load data
X, y = load_boston(return_X_y=True)

kf = KFold(n_splits=5, shuffle=True, random_state=42)
model = LinearRegression()

scores = []

for train_index, test_index in kf.split(X):
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]

    model.fit(X_train, y_train)
    preds = model.predict(X_test)
    mse = mean_squared_error(y_test, preds)
    scores.append(mse)

print("Average MSE:", np.mean(scores))
```

---

## 2️⃣ Stratified K-Fold

### 🔸 Concept:
Used for classification problems.

👉 Maintains the **same class distribution** in each fold.

Example:
- 70% class A
- 30% class B

Each fold will have approximately the same ratio.

### 🔸 Python Code:
```python
from sklearn.model_selection import StratifiedKFold
from sklearn.datasets import load_iris
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score
import numpy as np

X, y = load_iris(return_X_y=True)

skf = StratifiedKFold(n_splits=5)
model = LogisticRegression(max_iter=200)

scores = []

for train_index, test_index in skf.split(X, y):
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]

    model.fit(X_train, y_train)
    preds = model.predict(X_test)
    acc = accuracy_score(y_test, preds)
    scores.append(acc)

print("Average Accuracy:", np.mean(scores))
```

---

## 3️⃣ Leave-One-Out Cross Validation (LOOCV)

### 🔸 Concept:
- Each iteration uses **1 sample for testing**
- All remaining samples for training

If dataset size = N
👉 Number of iterations = N

### 🔸 Pros:
- Maximum data used for training

### 🔸 Cons:
- Very slow for large datasets

### 🔸 Python Code:
```python
from sklearn.model_selection import LeaveOneOut
from sklearn.linear_model import LinearRegression
import numpy as np

loo = LeaveOneOut()
model = LinearRegression()

scores = []

for train_index, test_index in loo.split(X):
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]

    model.fit(X_train, y_train)
    pred = model.predict(X_test)
    scores.append((y_test - pred)**2)

print("Average Error:", np.mean(scores))
```

---

## 4️⃣ Leave-P-Out Cross Validation

### 🔸 Concept:
- Each iteration uses **P samples for testing**
- Remaining samples for training

👉 Computationally expensive

---

## 5️⃣ Time Series Cross Validation

### 🔸 Concept:
Used for time-based data.

👉 Always train on past data and test on future data (no random shuffling)

### 🔸 Python Code:
```python
from sklearn.model_selection import TimeSeriesSplit


ts = TimeSeriesSplit(n_splits=5)

for train_index, test_index in ts.split(X):
    print("TRAIN:", train_index, "TEST:", test_index)
```

---

## 🔹 Built-in Cross Validation (Shortcut)

### 🔸 cross_val_score
```python
from sklearn.model_selection import cross_val_score
from sklearn.linear_model import LinearRegression

model = LinearRegression()

scores = cross_val_score(model, X, y, cv=5)

print("Scores:", scores)
print("Average:", scores.mean())
```

---

## 🔹 When to Use Which?

| Situation | Best Method |
|----------|------------|
| General ML | K-Fold |
| Imbalanced data | Stratified K-Fold |
| Very small data | LOOCV |
| Time-based data | TimeSeriesSplit |

---

## 🔹 Key Interview Points

- Cross Validation gives a better generalization estimate
- K-Fold is the most commonly used method
- Stratified K-Fold is important for classification
- LOOCV is accurate but computationally expensive

---

## 🔹 Final Summary

Cross Validation is a powerful technique that:
- Makes model evaluation more reliable
- Reduces overfitting
- Provides a better estimate of real-world performance

👉 Always prefer it over a simple train/test split in real projects.

---

## 🔹 Bonus Tip

If you are building an ML project (e.g., house price prediction 👀):

👉 Always use:
```python
cross_val_score(model, X, y, cv=5)
```

This gives a strong and reliable evaluation 🔥

---

**End of Notes ✅**


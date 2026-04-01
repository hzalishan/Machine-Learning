# 📘 Bagging and Boosting - Complete Revision Notes

## 🔹 What is Ensemble Learning?

Ensemble Learning means **combining multiple models** to improve accuracy and performance.

Main Ensemble Methods:
1. Voting
2. Bagging
3. Boosting

All of these are **Supervised Learning techniques**.

---

# 1️⃣ Bagging (Bootstrap Aggregation)

## 🔸 Concept:
Bagging means **training multiple models on different random subsets of data** and then combining their predictions.

👉 Steps:
1. Randomly select data with replacement (Bootstrap sampling)
2. Train multiple models on different datasets
3. Combine predictions (average or voting)

👉 Main Goal: **Reduce Variance & Overfitting**

---

## 🔸 Example:

Suppose we have dataset with 100 rows.

We create random datasets:
- Dataset 1 → Random 100 rows
- Dataset 2 → Random 100 rows
- Dataset 3 → Random 100 rows

Train model on each dataset → Combine results.

---

## 🔸 Random Forest = Bagging Algorithm

Random Forest is the **most famous Bagging algorithm**.

👉 It uses multiple Decision Trees and combines their results.

---

## 🔸 Python Code (Bagging):

```python
from sklearn.ensemble import BaggingClassifier
from sklearn.tree import DecisionTreeClassifier

model = BaggingClassifier(
    base_estimator=DecisionTreeClassifier(),
    n_estimators=10
)

model.fit(X_train, y_train)
pred = model.predict(X_test)
```

---

## 🔸 Advantages of Bagging

- Reduces overfitting
- Improves accuracy
- Works well with high variance models (like Decision Tree)

---

## 🔸 Disadvantages

- Training time high
- Not good for low variance models

---

# 2️⃣ Boosting

## 🔸 Concept:
Boosting means **training models sequentially**, where each new model focuses on the errors of the previous model.

👉 Steps:
1. Train first model
2. Find errors
3. Train second model on errors
4. Train third model on remaining errors
5. Combine all models

👉 Main Goal: **Reduce Bias & Improve Accuracy**

---

## 🔸 Popular Boosting Algorithms

| Algorithm | Description |
|----------|-------------|
| AdaBoost | Adaptive Boosting |
| Gradient Boosting | Uses gradient descent |
| XGBoost | Optimized Gradient Boosting |

---

## 🔸 Python Code (AdaBoost):

```python
from sklearn.ensemble import AdaBoostClassifier

model = AdaBoostClassifier(n_estimators=50)
model.fit(X_train, y_train)
pred = model.predict(X_test)
```

---

# 🔥 Bagging vs Boosting

| Feature | Bagging | Boosting |
|--------|--------|---------|
| Training | Parallel | Sequential |
| Goal | Reduce Variance | Reduce Bias |
| Overfitting | Reduced | Reduced |
| Models | Independent | Dependent |
| Example | Random Forest | AdaBoost, XGBoost |

---

## 🔹 Interview Points

- Bagging = Parallel training
- Boosting = Sequential training
- Random Forest = Bagging
- AdaBoost = Boosting
- Bagging reduces variance
- Boosting reduces bias

---

## 🔹 Final Summary

| Method | Purpose |
|-------|--------|
| Voting | Combine predictions |
| Bagging | Reduce Overfitting |
| Boosting | Improve Accuracy |

👉 These are the **most important Ensemble Learning methods**.

---

**End of Notes ✅**


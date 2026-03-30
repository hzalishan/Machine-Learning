# Model Parameters, Hyperparameters & Tuning – Detailed Notes (with Code)

---

# 1. Model Parameters

## 1.1 What are Model Parameters?

Model parameters are the values that a machine learning model **learns automatically from data during training**.

➡ They are the **core of the model** ➡ They directly affect predictions

---

## 1.2 Examples

### Linear Regression

ŷ = b0 + b1x

- b0 → intercept (parameter)
- b1 → slope (parameter)

These values are **learned using data**.

---

### Key Points

- Learned during training
- Not set manually
- Change when training data changes

---

# 2. Hyperparameters

## 2.1 What are Hyperparameters?

Hyperparameters are values that are **set before training the model**.

➡ They control **how the model learns** ➡ They are NOT learned from data

---

## 2.2 Examples

- Learning rate (α)
- Number of neighbors (K in KNN)
- Max depth (Decision Tree)

---

## 2.3 Difference (Very Important 🔥)

| Feature     | Model Parameters | Hyperparameters  |
| ----------- | ---------------- | ---------------- |
| Learned     | Yes              | No               |
| Set by user | No               | Yes              |
| Role        | Make predictions | Control training |

---

# 3. Why Hyperparameter Tuning?

Different hyperparameters → different results

Example:

K = 1 → overfitting\
K = 20 → underfitting

Goal:

➡ Find best values for best performance

---

# 4. GridSearchCV

## 4.1 What is GridSearchCV?

GridSearchCV tries **all possible combinations** of hyperparameters.

---

## 4.2 How it Works

Example:

C = [0.1, 1, 10]\
Kernel = ['linear', 'rbf']

Combinations:

(0.1, linear) (0.1, rbf) (1, linear) (1, rbf) (10, linear) (10, rbf)

➡ Total = 6 models trained

---

## 4.3 Cross Validation (cv)

GridSearch uses **cross-validation**.

Example: cv = 5

➡ Data split into 5 parts ➡ Train on 4, test on 1 (repeat 5 times) ➡ Average score is calculated

---

## 4.4 Code (GridSearchCV)

```python
from sklearn.model_selection import GridSearchCV
from sklearn.neighbors import KNeighborsClassifier

# Model
model = KNeighborsClassifier()

# Hyperparameter grid
param_grid = {
    'n_neighbors': [3, 5, 7],
    'weights': ['uniform', 'distance']
}

# Grid Search
grid = GridSearchCV(model, param_grid, cv=5)
grid.fit(X_train, y_train)

print("Best Parameters:", grid.best_params_)
print("Best Score:", grid.best_score_)
```

---

## 4.5 Pros & Cons

✔ Finds best combination\
❌ Very slow for large datasets

---

# 5. RandomizedSearchCV

## 5.1 What is RandomizedSearchCV?

RandomizedSearchCV tries **random combinations** instead of all.

---

## 5.2 Why Use It?

When search space is large:

➡ GridSearch becomes too slow

---

## 5.3 Code (RandomizedSearchCV)

```python
from sklearn.model_selection import RandomizedSearchCV
from sklearn.neighbors import KNeighborsClassifier
import numpy as np

model = KNeighborsClassifier()

param_dist = {
    'n_neighbors': np.arange(1, 20),
    'weights': ['uniform', 'distance']
}

random_search = RandomizedSearchCV(model, param_dist, n_iter=5, cv=5)
random_search.fit(X_train, y_train)

print("Best Parameters:", random_search.best_params_)
print("Best Score:", random_search.best_score_)
```

---

## 5.4 Pros & Cons

✔ Faster than GridSearch\
✔ Works well for large data\
❌ May miss best combination

---

# 6. GridSearch vs RandomizedSearch

| Feature  | GridSearch       | RandomizedSearch |
| -------- | ---------------- | ---------------- |
| Method   | All combinations | Random selection |
| Speed    | Slow             | Fast             |
| Accuracy | Best possible    | Good (approx)    |

---

# 7. Key Concepts Summary

Model Parameters → learned from data\
Hyperparameters → set before training

GridSearchCV → exhaustive search\
RandomizedSearchCV → random search

Cross-validation → reliable evaluation

Goal → best model performance 🚀


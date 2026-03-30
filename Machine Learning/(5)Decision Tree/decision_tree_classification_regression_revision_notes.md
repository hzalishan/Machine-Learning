# Decision Tree (Classification & Regression) – Detailed Notes (with Code)

## 1. What is a Decision Tree?

A **Decision Tree** is a supervised ML algorithm used for:

- Classification (predict categories)
- Regression (predict continuous values)

It works like a **flowchart (tree structure)**:

➡ Ask questions → split data → reach decision

---

## 2. Basic Structure

- Root Node → starting point
- Decision Node → condition (e.g., Age > 30?)
- Leaf Node → final output (class/value)

---

## 3. How Decision Tree Works?

Model splits data based on **best feature**.

Goal:

➡ Create pure groups (same class)

---

# 4. Decision Tree for Classification

Used when output is **categorical**.

Example:

Predict: Spam or Not Spam

---

## 4.1 Splitting Criteria (Important 🔥)

### Gini Index

Gini = 1 − Σ(p²)

Where p = probability of each class

Lower Gini → better split

---

### Entropy (Information Gain)

Entropy = − Σ(p log₂ p)

Information Gain = Reduction in entropy after split

Higher gain → better split

---

# 5. Decision Tree for Regression

Used when output is **continuous**.

Example:

Predict house price

---

## 5.1 Splitting Criteria (Regression)

Uses:

➡ Mean Squared Error (MSE)

Goal:

➡ Minimize variance within groups

---

# 6. Example Intuition

Dataset:

Age → Buy Product?

Tree:

Age > 30? ├── Yes → Buy └── No → Not Buy

---

# 7. Overfitting in Decision Trees

Trees can grow very deep and memorize data.

Result:

- Low training error
- High test error

---

# 8. Pruning (Very Important 🔥)

Pruning means **cutting unnecessary branches**.

Goal:

➡ Reduce overfitting

---

## 8.1 Types of Pruning

### Pre-Pruning (Early Stopping)

Stop tree growth early using:

- max\_depth
- min\_samples\_split
- min\_samples\_leaf

---

### Post-Pruning

Build full tree → then remove weak branches

In sklearn:

➡ cost\_complexity\_pruning (ccp\_alpha)

---

## 8.2 Example

Before pruning:

Very complex tree (overfit)

After pruning:

Simpler tree (better generalization)

---

# 9. Python Code (Important 🔥)

## 9.1 Classification Tree

```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report

# Sample data
X = [[1],[2],[3],[4],[5]]
y = [0,0,1,1,1]

# Split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Model
model = DecisionTreeClassifier(max_depth=3)
model.fit(X_train, y_train)

# Predict
y_pred = model.predict(X_test)

print(classification_report(y_test, y_pred))
```

---

## 9.2 Regression Tree

```python
from sklearn.tree import DecisionTreeRegressor

# Sample data
X = [[1],[2],[3],[4],[5]]
y = [2,4,6,8,10]

# Model
model = DecisionTreeRegressor(max_depth=3)
model.fit(X, y)

# Predict
print(model.predict([[6]]))
```

---

## 9.3 Pruning using ccp\_alpha

```python
from sklearn.tree import DecisionTreeClassifier

model = DecisionTreeClassifier(ccp_alpha=0.01)
model.fit(X_train, y_train)
```

---

# 10. Advantages

- Easy to understand
- Works with both classification & regression
- No need for feature scaling

---

# 11. Limitations

- Prone to overfitting
- Unstable (small data change → different tree)

---

# 12. Key Concepts Summary

Decision Tree → tree-based model

Classification → uses Gini / Entropy

Regression → uses MSE

Pruning → reduces overfitting

Pre-pruning → stop early

Post-pruning → remove branches later

Goal → simple + accurate model 🚀


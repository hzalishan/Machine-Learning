# Support Vector Machine (SVM) – Classification & Regression (Detailed Notes + Code)

## 1. What is SVM?
Support Vector Machine (SVM) is a **powerful supervised machine learning algorithm** used for:

- Classification
- Regression

Main idea:

➡ Find the **best boundary (hyperplane)** that separates data

---

## 2. SVM for Classification

### 2.1 Hyperplane
A hyperplane is a **decision boundary** that separates classes.

In 2D → line  
In 3D → plane

---

### 2.2 Margin

Margin = distance between hyperplane and nearest data points

Goal of SVM:

➡ **Maximize the margin**

---

### 2.3 Support Vectors (Important 🔥)

Support vectors are the **closest data points to the boundary**.

They **control the position of hyperplane**.

---

## 3. Hard Margin vs Soft Margin

### Hard Margin
- No misclassification allowed
- Works only for perfectly separable data

### Soft Margin
- Allows some errors
- More practical for real-world data

---

## 4. Regularization Parameter (C)

C controls **trade-off between margin and error**.

- Small C → wider margin, more tolerance to errors
- Large C → narrow margin, less error allowed

---

## 5. Non-Linear Data & Kernel Trick

Real-world data is often not linearly separable.

SVM uses **Kernel Trick** to transform data into higher dimension.

---

### Common Kernels

#### Linear Kernel
Used for linearly separable data

#### Polynomial Kernel
Creates curved boundaries

#### RBF (Radial Basis Function)
Most commonly used

---

## 6. SVM Classification Example

Data:

Class A ● ● ●
Class B ○ ○ ○

SVM finds a line that **maximizes separation**.

---

# 7. SVM for Regression (SVR)

SVM can also be used for regression.

Called:

➡ Support Vector Regression (SVR)

---

## 7.1 Key Idea

Instead of minimizing error strictly, SVR allows a margin of tolerance (ε).

➡ Errors inside margin are ignored

---

## 7.2 Epsilon (ε)

Defines a **tube (margin)** around prediction line.

- Inside tube → no penalty
- Outside → penalty

---

## 7.3 Objective

➡ Fit a line that keeps most points inside ε margin

---

## 8. Python Code (Important 🔥)

## 8.1 SVM Classification

```python
from sklearn.svm import SVC
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report

# Sample data
X = [[1],[2],[3],[4],[5]]
y = [0,0,1,1,1]

# Split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Model
model = SVC(kernel='rbf', C=1.0)
model.fit(X_train, y_train)

# Predict
y_pred = model.predict(X_test)

print(classification_report(y_test, y_pred))
```

---

## 8.2 SVM Regression (SVR)

```python
from sklearn.svm import SVR

# Sample data
X = [[1],[2],[3],[4],[5]]
y = [2,4,6,8,10]

# Model
model = SVR(kernel='rbf', C=1.0, epsilon=0.1)
model.fit(X, y)

# Predict
print(model.predict([[6]]))
```

---

## 8.3 With Feature Scaling (Very Important ⚠️)

```python
from sklearn.pipeline import make_pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.svm import SVC

model = make_pipeline(StandardScaler(), SVC(kernel='rbf'))
model.fit(X_train, y_train)
```

---

## 9. Advantages

- Works well in high-dimensional data
- Effective for complex boundaries
- Memory efficient (uses support vectors)

---

## 10. Limitations

- Slow for large datasets
- Requires careful tuning (C, kernel)
- Hard to interpret

---

## 11. Key Concepts Summary

SVM → finds best separating boundary

Hyperplane → decision boundary

Margin → distance to nearest points

Support Vectors → critical data points

Kernel Trick → handles non-linear data

SVR → regression version of SVM

C → controls margin vs error

ε → tolerance in regression

Goal → maximum margi
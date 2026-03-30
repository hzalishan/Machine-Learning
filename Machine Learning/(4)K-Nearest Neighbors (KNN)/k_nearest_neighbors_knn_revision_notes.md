# K-Nearest Neighbors (KNN) – Revision Notes (with Code)

## 1. What is KNN?
K-Nearest Neighbors (KNN) is a **supervised machine learning algorithm** used for:

- Classification
- Regression

It works based on **similarity (distance)**.

➡ “Similar data points have similar outputs”

---

## 2. How KNN Works?

Steps:

1. Choose value of K (number of neighbors)
2. Calculate distance between new point and all training data
3. Select K nearest points
4. 
- Classification → Majority vote
- Regression → Average value

---

## 3. Distance Metrics (Important 🔥)

### Euclidean Distance (most common)

Distance = √[(x1−x2)² + (y1−y2)²]

---

### Manhattan Distance

Distance = |x1−x2| + |y1−y2|

---

### Minkowski Distance

General form (combines both)

---

## 4. Choosing K Value

- Small K → sensitive to noise (overfitting)
- Large K → smoother but may underfit

Common choice:

➡ K = √(number of samples)

---

## 5. Example (Classification)

Dataset:

Points labeled Red (R) and Blue (B)

New point → check nearest neighbors

If majority = Red → classify as Red

---

## 6. KNN for Regression

Instead of voting:

➡ Take average of K nearest values

Example:

Neighbors values = 10, 12, 14

Prediction = (10 + 12 + 14) / 3 = 12

---

## 7. Important Concepts

### Lazy Learning

KNN does not train model explicitly.

➡ Stores entire dataset

---

### Feature Scaling (Very Important ⚠️)

KNN depends on distance → scale features

Example:

Use StandardScaler or MinMaxScaler

---

## 8. Python Code (Important 🔥)

## 8.1 KNN Classification

```python
from sklearn.neighbors import KNeighborsClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report

# Sample data
X = [[1],[2],[3],[4],[5]]
y = [0,0,1,1,1]

# Split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Model
model = KNeighborsClassifier(n_neighbors=3)
model.fit(X_train, y_train)

# Predict
y_pred = model.predict(X_test)

print(classification_report(y_test, y_pred))
```

---

## 8.2 KNN Regression

```python
from sklearn.neighbors import KNeighborsRegressor

# Sample data
X = [[1],[2],[3],[4],[5]]
y = [2,4,6,8,10]

# Model
model = KNeighborsRegressor(n_neighbors=2)
model.fit(X, y)

# Predict
print(model.predict([[6]]))
```

---

## 8.3 With Feature Scaling

```python
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import make_pipeline
from sklearn.neighbors import KNeighborsClassifier

model = make_pipeline(StandardScaler(), KNeighborsClassifier(n_neighbors=3))
model.fit(X_train, y_train)
```

---

## 9. Advantages

- Simple and easy
- No training phase
- Works well for small datasets

---

## 10. Limitations

- Slow for large datasets
- Sensitive to irrelevant features
- Requires feature scaling

---

## 11. Key Concepts Summary

KNN → distance-based algorithm

K → number of neighbors

Classification → majority vote

Regression → average value

Needs → feature scaling

Goal → find similar data points 🚀


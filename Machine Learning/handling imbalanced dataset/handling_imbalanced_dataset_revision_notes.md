# Handling Imbalanced Dataset – Revision Notes (with Code)

## 1. What is Imbalanced Dataset?
An **imbalanced dataset** is when one class has **much more data than the other**.

Example:

Spam Detection:
- Spam emails = 100
- Normal emails = 900

➡ Model becomes biased toward majority class.

---

## 2. Why is it a Problem?

Model may show **high accuracy but poor performance**.

Example:

If model predicts all as "Normal":

Accuracy = 90% ❌ (misleading)

But it fails to detect spam.

---

## 3. Key Idea

➡ Balance the dataset or adjust learning

---

# 4. Methods to Handle Imbalance

## 4.1 Undersampling

Reduce majority class size.

Example:

Normal = 900 → reduce to 100

Pros:
- Faster training

Cons:
- Loss of data

---

### Code (Undersampling)

```python
from sklearn.utils import resample

# Separate classes
majority = df[df['target'] == 0]
minority = df[df['target'] == 1]

# Downsample majority
majority_downsampled = resample(majority,
                               replace=False,
                               n_samples=len(minority),
                               random_state=42)

# Combine
df_balanced = pd.concat([majority_downsampled, minority])
```

---

## 4.2 Oversampling

Increase minority class size.

Example:

Spam = 100 → increase to 900

Pros:
- No data loss

Cons:
- Overfitting risk

---

### Code (Oversampling)

```python
from sklearn.utils import resample

majority = df[df['target'] == 0]
minority = df[df['target'] == 1]

# Upsample minority
minority_upsampled = resample(minority,
                             replace=True,
                             n_samples=len(majority),
                             random_state=42)

# Combine
df_balanced = pd.concat([majority, minority_upsampled])
```

---

## 4.3 SMOTE (Synthetic Data)

SMOTE creates **new synthetic samples** instead of copying.

Better than simple oversampling.

---

### Code (SMOTE)

```python
from imblearn.over_sampling import SMOTE

X = df.drop('target', axis=1)
y = df['target']

smote = SMOTE(random_state=42)
X_resampled, y_resampled = smote.fit_resample(X, y)
```

---

## 4.4 Class Weights

Give more importance to minority class.

---

### Code (Logistic Regression with class_weight)

```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression(class_weight='balanced')
model.fit(X, y)
```

---

## 4.5 Evaluation Metrics for Imbalanced Data

Do NOT rely on accuracy.

Use:

- Precision
- Recall
- F1 Score
- Confusion Matrix

---

# 5. Example Workflow

```python
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report
from imblearn.over_sampling import SMOTE
from sklearn.linear_model import LogisticRegression

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Apply SMOTE
smote = SMOTE()
X_train_res, y_train_res = smote.fit_resample(X_train, y_train)

# Train model
model = LogisticRegression()
model.fit(X_train_res, y_train_res)

# Predict
y_pred = model.predict(X_test)

# Evaluate
print(classification_report(y_test, y_pred))
```

---

# 6. Key Concepts Summary

Imbalanced Data → unequal class distribution

Problem → misleading accuracy

Solutions:
- Undersampling
- Oversampling
- SMOTE
- Class weights

Best practice → use **F1, Recall, Precision** instead of accuracy 🚀


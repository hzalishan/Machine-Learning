# Cost Function, SSE, Lasso and Ridge Regression – Revision Notes

## 1. What is a Cost Function?
A **Cost Function** measures how far the model's predictions are from the actual values.

In machine learning we train a model to make predictions. The cost function tells us **how bad the model is performing**.

Goal of training:

➡ **Minimize the cost function**

Lower cost = better model.

---

## 2. Important Terms

### Actual Value (y)
The **true value** in the dataset.

Example:
Real house price = 300k

### Predicted Value (ŷ)
The value predicted by the model.

Example:
Predicted price = 280k

### Error (Residual)
Difference between actual and predicted value.

Formula:

error = y − ŷ

Example:

Actual price = 300
Predicted price = 280

Error = 20

---

# 3. SSE (Sum of Squared Errors)

SSE is one of the most common cost functions used in **Linear Regression**.

Formula:

SSE = Σ (yi − ŷi)²

Where:

- Σ = summation
- yi = actual value
- ŷi = predicted value
- (yi − ŷi) = error

The errors are **squared and added together**.

---

## Why Do We Square the Errors?

1. Negative errors become positive
2. Large errors get penalized more
3. Helps optimization algorithms work better

---

## Example of SSE

Actual values:

10, 20, 30

Predicted values:

12, 18, 25

Step 1: Calculate errors

10 - 12 = -2

20 - 18 = 2

30 - 25 = 5

Step 2: Square errors

(-2)² = 4

2² = 4

5² = 25

Step 3: Add them

SSE = 4 + 4 + 25

SSE = **33**

This value represents the **total prediction error of the model**.

---

# 4. Problem: Overfitting

When a model becomes too complex, it may start memorizing training data instead of learning patterns.

This is called **Overfitting**.

To solve this problem we use **Regularization techniques**.

Two important methods:

• Ridge Regression

• Lasso Regression

---

# 5. Ridge Regression

Ridge Regression is a **regularized version of linear regression** that adds a penalty to large coefficients.

New cost function:

Cost = SSE + λ Σ (βj²)

Where:

- SSE = Sum of Squared Errors
- λ (lambda) = regularization parameter
- βj = model coefficients

---

## Meaning of Each Term

### λ (Lambda)
Controls how strong the penalty is.

If λ = 0

➡ Ridge becomes **normal linear regression**

If λ is very large

➡ coefficients become very small.

---

### β (Beta Coefficients)
These represent the **importance of each feature**.

Example model:

Price = 50 + 3(size) + 8(location)

Here:

β1 = 3

β2 = 8

Ridge regression **reduces large coefficients** to prevent overfitting.

---

## Example

Suppose model learns:

Price = 50 + 100(size) + 120(location)

These large coefficients may cause overfitting.

Ridge might shrink them to:

Price = 50 + 40(size) + 55(location)

This makes the model **more stable**.

---

# 6. Lasso Regression

Lasso regression is another regularization method.

It adds **absolute value penalty** to the cost function.

Cost function:

Cost = SSE + λ Σ |βj|

---

## Difference From Ridge

Ridge uses:

β²

Lasso uses:

|β|

This small difference causes an important effect.

---

## Feature Selection

Lasso can reduce some coefficients **exactly to zero**.

This means the model **removes unimportant features automatically**.

Example:

Original model:

Price = 50 + 3(size) + 4(age) + 8(location)

After Lasso:

Price = 50 + 3(size) + 8(location)

The feature **age** was removed.

---

# 7. Ridge vs Lasso

| Feature | Ridge Regression | Lasso Regression |
|-------|-------|-------|
| Penalty | β² | |β| |
| Feature Selection | No | Yes |
| Coefficients | Shrinks them | Can become zero |
| Best for | Many small features | Feature selection |

---

# 8. Simple Intuition

Normal Regression:

Model focuses only on **reducing error**.

Ridge / Lasso:

Model tries to **reduce error AND keep coefficients small**.

This prevents overfitting.

---

# 9. Key Concepts Summary

Cost Function → measures model error

SSE → Sum of squared prediction errors

Regularization → technique to prevent overfitting

Ridge Regression → adds squared penalty (β²)

Lasso Regression → adds absolute penalty (|β|)

Lasso can perform **feature selection**.


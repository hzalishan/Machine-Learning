# Polynomial Regression – Quick Revision Notes

## 1. What is Polynomial Regression?
Polynomial Regression is an extension of Linear Regression used when the **relationship between input (X) and output (Y) is nonlinear**.

Instead of fitting a straight line, the model fits a **curved line (polynomial curve)** to the data.

Example:
- Population growth
- Temperature change during a day
- Learning curves

---

## 2. Why Polynomial Regression?
Sometimes data is **not linear**.

Example pattern:

- Age vs Income
- Experience vs Productivity

Income might increase rapidly at first and then slow down.

A straight line cannot capture this pattern, but a **curve can**.

---

## 3. Polynomial Equation

General polynomial equation:

ŷ = b0 + b1x + b2x² + b3x³ + ... + bnxⁿ

Where:

- ŷ = predicted value
- b0 = intercept
- b1, b2, b3 = coefficients
- x = feature
- x², x³ = polynomial features

Even though powers are added, the model is still **linear in parameters**.

---

## 4. Example (Quadratic Model)

Polynomial degree = 2

ŷ = b0 + b1x + b2x²

Example:

ŷ = 2 + 3x + 0.5x²

If x = 4

ŷ = 2 + 3(4) + 0.5(16)

ŷ = 2 + 12 + 8

ŷ = 22

---

## 5. Polynomial Features

Original feature:

x

Polynomial transformation:

x → [x, x², x³, ...]

Example:

x = 3

Features become:

[3, 9, 27]

These features are then used in **Linear Regression model**.

---

## 6. Degree of Polynomial

Degree determines **curve complexity**.

Degree 1 → Linear Regression

Degree 2 → Parabola

Degree 3 → Cubic curve

Higher degree → more flexible curve

But very high degree may cause **overfitting**.

---

## 7. Training the Model

Steps:

1. Start with dataset (X, Y)
2. Create polynomial features
3. Apply Linear Regression
4. Fit the curve

Example in concept:

X → [x]

Transform

X → [x, x²]

Model learns coefficients:

ŷ = b0 + b1x + b2x²

---

## 8. Cost Function

Polynomial regression uses the **same cost function as Linear Regression**.

Mean Squared Error:

J = (1/n) Σ (yi − ŷi)²

Goal:

Minimize prediction error.

---

## 9. Overfitting Problem

High degree polynomial may fit **training data perfectly** but fail on new data.

Example:

Degree 10 curve passing through every point.

Result:

Low training error
High test error

Solution:

- Choose optimal degree
- Use cross validation

---

## 10. Underfitting vs Overfitting

Underfitting:

Model too simple
Example: Degree 1 for curved data

Overfitting:

Model too complex
Example: Degree 15

Goal:

Find **balance between bias and variance**.

---

## 11. Visual Intuition

Linear regression:

Straight line

Polynomial regression:

Curved line that follows pattern of data.

---

## 12. Applications

- Population growth prediction
- Stock market trend curves
- Biological growth patterns
- Disease spread modeling
- Sales trend prediction

---

## 13. Advantages

- Can model nonlinear relationships
- More flexible than linear regression
- Easy to implement

---

## 14. Limitations

- Sensitive to outliers
- High degree causes overfitting
- Poor extrapolation outside data range

---

## 15. Key Concepts Summary

Polynomial Regression = Linear Regression + Polynomial Features

Polynomial Equation:

ŷ = b0 + b1x + b2x² + ...

Degree controls **curve complexity**.

Too low degree → underfitting

Too high degree → overfitting

Goal → best curve with minimum error.

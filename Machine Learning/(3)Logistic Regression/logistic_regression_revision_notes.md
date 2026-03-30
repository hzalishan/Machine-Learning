# Logistic Regression (with Polynomial Features) – Revision Notes

## 1. What is Logistic Regression?
Logistic Regression is a **supervised machine learning algorithm used for classification problems**.

Unlike Linear Regression which predicts **continuous values**, Logistic Regression predicts **probabilities**.

Example problems:

- Email → Spam or Not Spam
- Student → Pass or Fail
- Patient → Disease or No Disease

Output range:

0 ≤ prediction ≤ 1

This value represents **probability**.

Example:

0.8 → 80% chance of class 1

---

# 2. Logistic Regression Model

The basic logistic regression model:

z = a0 + a1x

Where:

- a0 = intercept (bias)
- a1 = coefficient (weight)
- x = feature
- z = linear combination

But instead of using z directly, logistic regression passes it through the **Sigmoid Function**.

---

# 3. Sigmoid Function

The **sigmoid function** converts any value into a number between **0 and 1**.

Formula:

σ(z) = 1 / (1 + e^(-z))

Where:

- z = a0 + a1x
- e = Euler's constant (≈ 2.718)

Output:

0 to 1

This makes it perfect for **probability prediction**.

---

# 4. Example of Sigmoid Function

Suppose:

a0 = -4

a1 = 0.8

Feature value:

x = 6

Step 1: Calculate z

z = a0 + a1x

z = -4 + 0.8(6)

z = -4 + 4.8

z = 0.8

Step 2: Apply sigmoid

σ(z) = 1 / (1 + e^(-0.8))

σ(z) ≈ 1 / (1 + 0.449)

σ(z) ≈ 0.69

Interpretation:

Probability of class = **69%**

---

# 5. Decision Boundary

Logistic regression converts probability into class label.

Typical rule:

If probability ≥ 0.5 → Class 1

If probability < 0.5 → Class 0

Example:

0.69 → Class 1

0.30 → Class 0

---

# 6. Logistic Regression Cost Function

Unlike linear regression, logistic regression uses **Log Loss (Binary Cross Entropy)**.

Formula:

J(a0,a1) = -(1/n) Σ [ y log(ŷ) + (1-y) log(1-ŷ) ]

Where:

- y = actual label
- ŷ = predicted probability
- n = number of samples

Goal:

➡ **Minimize this cost**.

---

# 7. Polynomial Logistic Regression

Sometimes the relationship between feature and class is **nonlinear**.

Example dataset may look like a **curve instead of straight line**.

To solve this we use **Polynomial Features**.

Example transformation:

Original feature:

x

Polynomial features:

x , x² , x³

New model becomes:

z = a0 + a1x + a2x²

Then sigmoid is applied:

ŷ = 1 / (1 + e^-(a0 + a1x + a2x²))

This allows logistic regression to **learn curved decision boundaries**.

---

# 8. Example of Polynomial Logistic Model

Suppose:

a0 = -3

a1 = 1

a2 = -0.2

Feature:

x = 4

Step 1: Compute polynomial z

z = a0 + a1x + a2x²

z = -3 + 1(4) + (-0.2)(16)

z = -3 + 4 - 3.2

z = -2.2

Step 2: Apply sigmoid

σ(z) = 1 / (1 + e^(-(-2.2)))

σ(z) = 1 / (1 + e^(2.2))

σ(z) ≈ 1 / (1 + 9.03)

σ(z) ≈ 0.099

Probability ≈ **9.9%**

Prediction → Class 0

---

# 9. Key Terms Explained

### Intercept (a0)
Baseline value when x = 0.

### Coefficient (a1, a2)
Shows how strongly each feature affects prediction.

### Sigmoid Function
Transforms linear output into probability.

### Decision Boundary
Threshold that separates classes.

### Polynomial Features
Higher powers of input used to capture nonlinear patterns.

---

# 10. Key Concepts Summary

Logistic Regression → classification algorithm

Output → probability (0–1)

Sigmoid Function:

σ(z) = 1 / (1 + e^-z)

Linear part:

z = a0 + a1x

Polynomial version:

z = a0 + a1x + a2x²

Polynomial logistic regression allows **non‑linear decision boundaries**.


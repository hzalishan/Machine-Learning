# Gradient Descent – Revision Notes (with Code)

## 1. What is Gradient Descent?
Gradient Descent is an **optimization algorithm** used to minimize the cost function.

Simple idea:

➡ Start with random values → slowly move toward minimum error

---

## 2. Real Life Intuition

Imagine you are standing on a mountain:

- You want to reach the **lowest point (minimum)**
- You take small steps in the direction of **steepest descent**

That is Gradient Descent.

---

## 3. Mathematical Idea

We update parameters using derivatives.

For linear regression:

ŷ = b0 + b1x

Cost function (MSE):

J = (1/n) Σ (y − ŷ)^2

---

## 4. Update Rules

b0 = b0 − α ∂J/∂b0

b1 = b1 − α ∂J/∂b1

Where:

- α (alpha) = learning rate
- ∂J = derivative (slope)

---

## 5. Learning Rate (α)

- Small α → slow learning
- Large α → may overshoot
- Good α → fast and stable convergence

---

## 6. Types of Gradient Descent

1. Batch Gradient Descent
2. Stochastic Gradient Descent (SGD)
3. Mini-Batch Gradient Descent

---

## 7. Convergence

Gradient Descent stops when:

- Cost stops decreasing
- Updates become very small

---

# 8. Python Code (Only Gradient Descent 🔥)

## 8.1 Simple Implementation (from scratch)

```python
import numpy as np

# Sample data
X = np.array([1,2,3,4,5])
Y = np.array([2,4,6,8,10])

# Initialize parameters
b0 = 0
b1 = 0

# Hyperparameters
alpha = 0.01  # learning rate
epochs = 1000
n = len(X)

# Gradient Descent loop
for i in range(epochs):
    y_pred = b0 + b1 * X
    
    # Compute gradients
    db0 = (-2/n) * np.sum(Y - y_pred)
    db1 = (-2/n) * np.sum((Y - y_pred) * X)
    
    # Update parameters
    b0 = b0 - alpha * db0
    b1 = b1 - alpha * db1

print("Intercept (b0):", b0)
print("Slope (b1):", b1)
```

---

## 8.2 Output Interpretation

For this dataset (Y = 2X):

b0 ≈ 0  
b1 ≈ 2

Model learned:

ŷ = 2x

---

## 9. Key Concepts Summary

Gradient Descent → minimizes cost function

Uses → derivatives (slopes)

Update rule → parameter − learning_rate × gradient

Learning rate → controls step size

Goal → reach **minimum error point**


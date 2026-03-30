# Beta (β) and Beta Square (β²) in Ridge and Lasso Regression

## 1. What is Beta (β)?
Beta (β) is the coefficient or weight of a feature in a regression model. It shows how much a feature affects the prediction.

Example equation:

y = β0 + β1x

β0 = intercept
β1 = coefficient (beta)

Example:
Price = 50,000 + 2000 × Size

Here:
β0 = 50,000
β1 = 2000

Meaning:
If size increases by 1 unit, price increases by 2000.

In multiple linear regression:

y = β0 + β1x1 + β2x2 + β3x3

Each beta represents the importance of a feature.

β1 → effect of x1
β2 → effect of x2
β3 → effect of x3


## 2. What is Beta Square (β²)?
Beta square means multiplying beta by itself.

β² = β × β

Examples:

β = 3  →  β² = 9
β = -4 →  β² = 16

Squaring removes the negative sign and makes the value positive.

This is used in Ridge Regression to penalize large coefficients.


## 3. Ridge Regression

Ridge regression adds a penalty to the normal regression error.

Normal cost function:

Cost = MSE

Ridge cost function:

Cost = MSE + λ(β1² + β2² + β3² ...)

λ (lambda) controls the strength of the penalty.

Effects:

• Prevents overfitting
• Reduces large coefficients
• Keeps all features in the model

Important point:
Ridge makes coefficients small but usually does not make them zero.


## 4. Lasso Regression

Lasso uses absolute values of coefficients instead of squares.

Cost = MSE + λ(|β1| + |β2| + |β3|)

|β| means absolute value.

Examples:

| -3 | = 3
| 5 |  = 5

Effects:

• Some coefficients become exactly zero
• Irrelevant features are removed
• Works as feature selection


## 5. Ridge vs Lasso

Linear Regression
No penalty

Ridge Regression
Penalty = β²

Lasso Regression
Penalty = |β|


## 6. Key Difference

Ridge:
Shrinks coefficients but keeps them in the model.

Lasso:
Shrinks coefficients and can remove features by making coefficients zero.


## 7. Simple Memory Trick

Ridge → Square penalty → Small coefficients

Lasso → Absolute penalty → Some coefficients become zero


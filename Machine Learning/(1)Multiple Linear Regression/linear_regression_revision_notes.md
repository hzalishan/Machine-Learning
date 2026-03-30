# Linear Regression – Quick Revision Notes

## 1. What is Linear Regression?
Linear Regression is a supervised machine learning algorithm used to predict a continuous value by modeling the relationship between independent variables (features) and a dependent variable (target).

Example: Predicting house price using size, number of rooms, and location.

---

## 2. Types of Linear Regression

### Simple Linear Regression
Uses only one independent variable.

Equation:

y = m x + b

Where:
- y = predicted value
- x = input feature
- m = slope (coefficient)
- b = intercept (baseline value)

Example:
salary = 20000 + 5000 × experience

Meaning:
- Even with 0 years experience, salary = 20000
- Each extra year adds 5000

---

### Multiple Linear Regression
Uses multiple independent variables.

Equation:

y = b0 + b1x1 + b2x2 + ... + bnxn

Where:
- y = predicted value
- b0 = intercept
- b1, b2 ... = coefficients
- x1, x2 ... = features

Example:

BP = 80 − 1.5(dose) + 0.7(age) + 0.5(weight)

Interpretation:
- 80 = baseline BP
- Dose decreases BP
- Age slightly increases BP
- Weight increases BP

---

## 3. Goal of Linear Regression
Find the best fitting line that minimizes prediction error.

This line is called the Best Fit Line.

---

## 4. Prediction Formula

ŷ = b0 + b1x1 + b2x2 + ... + bnxn

Example:

ŷ = 50 + 3x

If x = 10

ŷ = 50 + 3(10) = 80

---

## 5. Residual (Error)

Residual = Actual value − Predicted value

error = y − ŷ

Example:
Actual price = 300k  
Predicted = 280k  

Residual = 20k

---

## 6. Cost Function (Mean Squared Error)

J = (1/n) Σ (yi − ŷi)^2

Where:
- yi = actual value
- ŷi = predicted value
- n = number of samples

Goal: minimize this value.

---

## 7. Gradient Descent

Used to find optimal parameters.

Update rules:

m = m − α ∂J/∂m  
b = b − α ∂J/∂b

Where:
α = learning rate

---

## 8. Assumptions of Linear Regression

1. Linearity
2. Independence of observations
3. Homoscedasticity (constant error variance)
4. Normal distribution of errors
5. No multicollinearity

---

## 9. Evaluation Metrics

### MAE
MAE = (1/n) Σ |y − ŷ|

### MSE
MSE = (1/n) Σ (y − ŷ)^2

### RMSE
RMSE = √MSE

### R² Score

R² = 1 − (SSres / SStot)

Where:

SSres = Σ(y − ŷ)^2  
SStot = Σ(y − ȳ)^2

Interpretation:

R² = 0.85 → Model explains 85% variance.

---

## 10. Overfitting vs Underfitting

Underfitting:
Model too simple → high training error.

Overfitting:
Model learns noise → low training error but poor test performance.

---

## 11. Applications

- House price prediction
- Stock trend prediction
- Sales forecasting
- Weather prediction
- Medical dosage prediction

---

## 12. Key Concepts Summary

Feature (X): Input variable  
Target (Y): Predicted variable  

Intercept (b0): Baseline value  

Coefficient (b1,b2..): Feature impact  

Residual: Prediction error  

Cost Function: Total model error  

Gradient Descent: Optimization method


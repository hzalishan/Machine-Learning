# Cost Function – Quick Revision Notes

## 1. What is a Cost Function?
A **Cost Function** measures how wrong a machine learning model's predictions are compared to the actual values.

In simple words:

Cost Function = **Model Error**

It tells us **how well or how poorly the model is performing**.

Goal of training a model:

➡ **Minimize the cost function**

---

## 2. Why Do We Need a Cost Function?
When a model makes predictions, they are usually **not perfectly correct**.

Example:

Actual house price = 300k  
Predicted price = 280k

Error = 20k

The cost function **combines all errors from the dataset** into a single value.

This value tells us how good the model is.

---

## 3. Error vs Cost

**Error**

Difference for **one data point**.

Error formula:

error = y − ŷ

Where:

- y = actual value
- ŷ = predicted value

**Cost**

Average error over **entire dataset**.

---

## 4. Mean Squared Error (Most Common Cost Function)

Linear regression usually uses **Mean Squared Error (MSE)**.

Formula:

J(θ) = (1/n) Σ (yi − ŷi)²

Where:

- yi = actual value
- ŷi = predicted value
- n = number of samples
- Σ = summation

J(θ) represents the **cost**.

---

## 5. Why Squared Error?
We square the error because:

1. Negative and positive errors become positive
2. Large errors get **penalized more**
3. Makes optimization mathematically easier

Example:

Errors: -2 , 3

Squared errors:

4 , 9

---

## 6. Cost Function in Linear Regression

Prediction equation:

ŷ = b0 + b1x

Cost function:

J(b0,b1) = (1/n) Σ (yi − ŷi)²

The algorithm searches for values of **b0 and b1** that **minimize J**.

This produces the **best fit line**.

---

## 7. Optimization (How Cost is Minimized)

Machine learning algorithms minimize cost using **Gradient Descent**.

Idea:

1. Start with random parameters
2. Calculate cost
3. Adjust parameters
4. Reduce cost step by step

Until cost becomes minimal.

---

## 8. Visual Intuition

Imagine a **bowl-shaped curve**.

Top of bowl → high error  
Bottom of bowl → minimum error

Gradient Descent moves parameters toward the **bottom of the bowl**.

---

## 9. Cost vs Loss

Sometimes the terms are used interchangeably.

**Loss Function**

Error for **one data sample**.

**Cost Function**

Average loss over **entire dataset**.

---

## 10. Other Cost Functions

### Mean Absolute Error (MAE)

MAE = (1/n) Σ |y − ŷ|

Measures average absolute difference.

---

### Root Mean Squared Error (RMSE)

RMSE = √MSE

Gives error in **original unit**.

---

## 11. Real Life Example

Suppose a model predicts student marks.

Actual marks:

80, 70, 90

Predicted marks:

75, 72, 85

Errors:

5, -2, 5

Squared errors:

25, 4, 25

MSE:

(25 + 4 + 25) / 3 = 18

Cost = **18**

---

## 12. Key Concepts Summary

Cost Function → measures model error

Goal → minimize cost

Most common cost function → **Mean Squared Error (MSE)**

Formula:

J(θ) = (1/n) Σ (yi − ŷi)²

Lower cost → better model

Cost minimized using → **Gradient Descent**


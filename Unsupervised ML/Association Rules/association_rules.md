# 📘 Association Rules - Complete Revision Guide

## 🔹 What are Association Rules?

Association Rules are a **data mining technique** used to discover relationships between items in large datasets.

👉 It answers questions like:

- "If a customer buys X, what else are they likely to buy?"

This is widely used in **market basket analysis**.

---

## 🔹 Basic Idea

Association rules find patterns in the form:

👉 **X → Y**

Where:

- X = antecedent (if part)
- Y = consequent (then part)

Example: 👉 {Bread, Butter} → {Jam}

Meaning: Customers who buy Bread & Butter also tend to buy Jam.

---

## 🔹 Key Terms (Very Important)

### 1️⃣ Support

Support tells how frequently an itemset appears in dataset.

👉 Formula: Support(X) = (Transactions containing X) / (Total Transactions)

---

### 2️⃣ Confidence

Confidence tells how often rule is correct.

👉 Formula: Confidence(X → Y) = Support(X ∪ Y) / Support(X)

---

### 3️⃣ Lift

Lift measures how strong a rule is compared to random chance.

👉 Formula: Lift(X → Y) = Confidence(X → Y) / Support(Y)

---

## 🔹 Interpretation of Lift

| Lift Value | Meaning           |
| ---------- | ----------------- |
| = 1        | No relation       |
| > 1        | Positive relation |
| < 1        | Negative relation |

---

## 🔹 Example (Simple)

Dataset:

| Transaction | Items                     |
| ----------- | ------------------------- |
| T1          | Bread, Milk               |
| T2          | Bread, Diaper, Beer, Eggs |
| T3          | Milk, Diaper, Beer, Coke  |
| T4          | Bread, Milk, Diaper, Beer |
| T5          | Bread, Milk, Diaper, Coke |

Rule: 👉 {Diaper} → {Beer}

- Support = how many transactions contain both
- Confidence = probability of Beer given Diaper

---

## 🔹 Why Association Rules are Useful?

- Understand customer behavior
- Product recommendation
- Cross-selling strategies
- Store layout optimization

---

## 🔹 Real World Applications

- Amazon product recommendations
- Supermarket basket analysis
- Netflix recommendations
- E-commerce personalization

---

## 🔹 Types of Association Rules

### 1️⃣ Single Dimensional

Only one attribute

Example: 👉 Buy Bread → Buy Milk

---

### 2️⃣ Multi-Dimensional

Multiple attributes involved

Example: 👉 Age 20-30 & Buy Phone → Buy Earphones

---

### 3️⃣ Boolean Rules

Only presence/absence

---

### 4️⃣ Quantitative Rules

Include numerical values

Example: 👉 Income > 50k → Buy Car

---

## 🔹 Important Properties

- Association ≠ Causation ❗
- Just because items occur together doesn't mean one causes the other

---

## 🔹 Python Example (Basic Idea)

```python
import pandas as pd

# Sample transactions
transactions = [
    ['Bread', 'Milk'],
    ['Bread', 'Diaper', 'Beer', 'Eggs'],
    ['Milk', 'Diaper', 'Beer', 'Coke'],
    ['Bread', 'Milk', 'Diaper', 'Beer'],
    ['Bread', 'Milk', 'Diaper', 'Coke']
]

# Convert to DataFrame (dummy encoding)
from mlxtend.preprocessing import TransactionEncoder
te = TransactionEncoder()
te_array = te.fit(transactions).transform(transactions)
df = pd.DataFrame(te_array, columns=te.columns_)

print(df.head())
```

👉 Note: Algorithms (like Apriori, FP-Growth) will be added later.

---

## 🔹 Advantages

- Easy to understand
- Useful for recommendation systems
- Works well with large datasets

---

## 🔹 Disadvantages

- Can generate too many rules
- Needs filtering (support, confidence)
- Computationally expensive

---

## 🔹 Important Interview Points

- X → Y format
- Support, Confidence, Lift
- Used in market basket analysis
- Does not imply causation

---

## 🔹 Final Summary

Association Rules help us:

- Discover hidden patterns in data
- Understand relationships between items
- Build recommendation systems

👉 Foundation for algorithms like **Apriori and FP-Growth** (we will cover later).

---

**End of Notes ✅**


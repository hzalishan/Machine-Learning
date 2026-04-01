# 📘 Apriori Algorithm - Complete Revision Guide

## 🔹 What is Apriori Algorithm?

Apriori is a **data mining algorithm** used to find **frequent itemsets** and generate **association rules** from a dataset.

It is mostly used in **Market Basket Analysis**.

👉 Example: If customers buy **Bread**, they also buy **Milk**.

So Apriori helps us find rules like:

👉 **Bread → Milk**

---

## 🔹 Why the Name “Apriori”?

Apriori means **"prior knowledge"**.

The algorithm uses this idea:

> If an itemset is frequent, then all of its subsets must also be frequent.

This is called the **Apriori Property**.

Example: If {Bread, Milk} is frequent → then {Bread} and {Milk} must also be frequent.

This property helps **reduce search space** and makes the algorithm faster.

---

## 🔹 Key Terms (Revision)

Before Apriori, remember these:

| Term       | Meaning                   |
| ---------- | ------------------------- |
| Support    | How often item appears    |
| Confidence | How often rule is correct |
| Lift       | Strength of rule          |

---

## 🔹 How Apriori Algorithm Works (Step-by-Step)

### Step 1: Set Minimum Support

We first set a **minimum support threshold**.

Example: Min Support = 40%

---

### Step 2: Find Frequent 1-Itemsets

Count support of each item and keep only frequent ones.

Example:

| Item   | Support |
| ------ | ------- |
| Bread  | 4       |
| Milk   | 4       |
| Butter | 2       |

Remove items below min support.

---

### Step 3: Generate Candidate 2-Itemsets

Make combinations from frequent 1-itemsets.

Example: {Bread, Milk} {Bread, Butter} {Milk, Butter}

---

### Step 4: Apply Support Again

Keep only frequent 2-itemsets.

---

### Step 5: Generate 3-Itemsets

Repeat process until no more frequent itemsets found.

---

### Step 6: Generate Association Rules

Now compute:

- Confidence
- Lift

And keep strong rules.

---

## 🔹 Simple Example

Transactions:

| TID | Items               |
| --- | ------------------- |
| T1  | Bread, Milk         |
| T2  | Bread, Butter       |
| T3  | Milk, Butter        |
| T4  | Bread, Milk, Butter |

### Frequent Itemsets:

- {Bread}
- {Milk}
- {Butter}
- {Bread, Milk}

### Rules Generated:

- Bread → Milk
- Milk → Bread

---

## 🔹 Important Concept: Candidate Generation

Apriori works like this:

| Step | Itemsets            |
| ---- | ------------------- |
| L1   | Frequent 1-itemsets |
| L2   | Frequent 2-itemsets |
| L3   | Frequent 3-itemsets |

It stops when no frequent itemsets are found.

---

## 🔹 Python Implementation (Apriori)

```python
import pandas as pd
from mlxtend.frequent_patterns import apriori, association_rules
from mlxtend.preprocessing import TransactionEncoder

# Transactions
transactions = [
    ['Bread', 'Milk'],
    ['Bread', 'Diaper', 'Beer', 'Eggs'],
    ['Milk', 'Diaper', 'Beer', 'Coke'],
    ['Bread', 'Milk', 'Diaper', 'Beer'],
    ['Bread', 'Milk', 'Diaper', 'Coke']
]

# Convert to DataFrame
te = TransactionEncoder()
te_array = te.fit(transactions).transform(transactions)
df = pd.DataFrame(te_array, columns=te.columns_)

# Apply Apriori
frequent_items = apriori(df, min_support=0.4, use_colnames=True)

# Generate Rules
rules = association_rules(frequent_items, metric="confidence", min_threshold=0.6)

print(frequent_items)
print(rules)
```

---

## 🔹 Output Explanation

- **frequent\_items** → Frequent itemsets
- **rules** → Association rules
- Metrics include:
  - support
  - confidence
  - lift

---

## 🔹 Advantages of Apriori

- Easy to understand
- Easy to implement
- Good for learning

---

## 🔹 Disadvantages of Apriori

- Slow for large datasets
- Generates too many candidate itemsets
- High computational cost

👉 That is why **FP-Growth** is used in real-world instead of Apriori.

---

## 🔹 Apriori vs FP-Growth

| Feature              | Apriori | FP-Growth |
| -------------------- | ------- | --------- |
| Speed                | Slow    | Fast      |
| Candidate Generation | Yes     | No        |
| Memory               | High    | Low       |

---

## 🔹 Real World Applications

- Market basket analysis
- Recommendation systems
- Product bundling
- Customer behavior analysis

---

## 🔹 Important Interview Points

- Apriori uses **Apriori Property**
- Works on **Support threshold**
- Generates **Frequent Itemsets first**
- Then generates **Association Rules**
- Slow for large datasets

---

## 🔹 Final Summary

Apriori Algorithm:

- Finds frequent itemsets
- Uses Apriori property
- Generates association rules
- Uses support and confidence

👉 Very important algorithm in **Data Mining**.

---

**End of Notes ✅**


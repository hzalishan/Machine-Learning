# 📘 FP-Growth Algorithm - Complete Revision Guide

## 🔹 What is FP-Growth Algorithm?
FP-Growth stands for **Frequent Pattern Growth Algorithm**.

It is a **data mining algorithm** used to find **frequent itemsets** and generate **association rules**, just like Apriori, but it is **much faster and more efficient**.

👉 FP-Growth is an improved version of Apriori.

---

## 🔹 Why FP-Growth is Better than Apriori?

Apriori problem:
- Generates too many candidate itemsets
- Multiple database scans
- Slow for large datasets

FP-Growth solution:
- Does **NOT generate candidate itemsets**
- Uses a special tree called **FP-Tree**
- Requires only **2 database scans**
- Much faster

---

## 🔹 Key Concept: FP-Tree (Very Important)

FP-Growth uses a data structure called:

👉 **FP-Tree (Frequent Pattern Tree)**

This tree stores:
- Items
- Frequency (support)
- Item relationships

So instead of generating combinations like Apriori, FP-Growth stores data in a **tree structure**.

---

## 🔹 How FP-Growth Works (Step-by-Step)

### Step 1: Scan Database
Find frequency (support) of each item.

Remove items below minimum support.

---

### Step 2: Sort Items by Frequency
Arrange items in **descending order of support**.

Example:
| Item | Support |
|------|--------|
| Bread | 5 |
| Milk | 4 |
| Butter | 3 |

Order → Bread, Milk, Butter

---

### Step 3: Build FP-Tree
Insert transactions into the tree in sorted order.

Transactions like:
- Bread, Milk
- Bread, Butter
- Bread, Milk, Butter

Will form a compact tree.

---

### Step 4: Generate Frequent Patterns
Start from **least frequent item** and build **conditional pattern base** and **conditional FP-tree**.

This process is called **pattern growth**.

---

### Step 5: Generate Association Rules
After finding frequent itemsets, generate rules using:
- Support
- Confidence
- Lift

---

## 🔹 Simple Example

Transactions:

| TID | Items |
|----|------|
| T1 | Bread, Milk |
| T2 | Bread, Butter |
| T3 | Milk, Butter |
| T4 | Bread, Milk, Butter |

FP-Growth will:
1. Count frequency
2. Build FP-Tree
3. Extract frequent itemsets
4. Generate rules

---

## 🔹 Apriori vs FP-Growth

| Feature | Apriori | FP-Growth |
|--------|--------|-----------|
| Candidate Generation | Yes | No |
| Database Scan | Many | 2 |
| Speed | Slow | Fast |
| Memory | High | Low |
| Method | Breadth First | Depth First |

---

## 🔹 Python Implementation (FP-Growth)

```python
import pandas as pd
from mlxtend.frequent_patterns import fpgrowth, association_rules
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

# Apply FP-Growth
frequent_items = fpgrowth(df, min_support=0.4, use_colnames=True)

# Generate Rules
rules = association_rules(frequent_items, metric="confidence", min_threshold=0.6)

print(frequent_items)
print(rules)
```

---

## 🔹 Advantages of FP-Growth

- Faster than Apriori
- No candidate generation
- Efficient for large datasets
- Uses compact tree structure

---

## 🔹 Disadvantages of FP-Growth

- FP-Tree can be complex
- Harder to implement from scratch

---

## 🔹 Real World Applications

- Market basket analysis
- Recommendation systems
- Customer behavior analysis
- Fraud detection

---

## 🔹 Important Interview Points

- FP-Growth uses **FP-Tree**
- No candidate generation
- Faster than Apriori
- Uses pattern growth approach
- Only 2 database scans

---

## 🔹 Final Summary

FP-Growth Algorithm:
- Finds frequent itemsets
- Uses FP-Tree
- Faster than Apriori
- No candidate generation
- Used in large datasets

👉 FP-Growth is **preferred in real-world applications** over Apriori.

---

**End of Notes ✅**


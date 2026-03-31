# 📘 K-Means Clustering - Complete Revision Guide

## 🔹 What is K-Means?

K-Means is an **unsupervised machine learning algorithm** used to group data into clusters.

👉 It tries to divide data into **K groups (clusters)** where:

- Data points inside a cluster are similar
- Data points in different clusters are different

---

## 🔹 Key Idea

K-Means works by:

1. Choosing K (number of clusters)
2. Randomly initializing K centroids
3. Assigning each data point to the nearest centroid
4. Updating centroids based on mean of assigned points
5. Repeating until convergence

---

## 🔹 Step-by-Step Working

### Step 1: Choose K

Decide how many clusters you want

### Step 2: Initialize Centroids

Randomly pick K points as centroids

### Step 3: Assign Points

Each point is assigned to the nearest centroid (using distance, usually Euclidean)

### Step 4: Update Centroids

Compute new centroid = mean of all points in that cluster

### Step 5: Repeat

Repeat steps 3 & 4 until centroids stop changing

---

## 🔹 Mathematical Intuition

K-Means minimizes: 👉 **Within-Cluster Sum of Squares (WCSS)**

Formula:

WCSS = Σ (distance between point and its centroid)^2

---

## 🔹 Python Implementation (Basic)

```python
from sklearn.cluster import KMeans
import numpy as np

# Sample data
X = np.array([
    [1, 2], [1, 4], [1, 0],
    [10, 2], [10, 4], [10, 0]
])

# Model
kmeans = KMeans(n_clusters=2, random_state=42)
kmeans.fit(X)

# Results
print("Centroids:\n", kmeans.cluster_centers_)
print("Labels:", kmeans.labels_)
```

---

## 🔹 Visualization Example

```python
import matplotlib.pyplot as plt

plt.scatter(X[:, 0], X[:, 1], c=kmeans.labels_)
plt.scatter(kmeans.cluster_centers_[:, 0], kmeans.cluster_centers_[:, 1], marker='X')
plt.show()
```

---

## 🔹 Choosing Optimal K (Elbow Method)

👉 We run K-Means for multiple K values and compute WCSS

### Idea:

- Plot K vs WCSS
- Choose point where curve bends ("elbow")

### Code:

```python
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt

wcss = []

for k in range(1, 10):
    kmeans = KMeans(n_clusters=k, random_state=42)
    kmeans.fit(X)
    wcss.append(kmeans.inertia_)

plt.plot(range(1, 10), wcss)
plt.xlabel("Number of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()
```

---

## 🔹 Advantages

- Simple and fast
- Works well on large datasets
- Easy to implement

---

## 🔹 Disadvantages

- Need to choose K manually
- Sensitive to initial centroids
- Not good for non-spherical clusters
- Affected by outliers

---

## 🔹 Real World Applications

- Customer segmentation
- Image compression
- Recommendation systems
- Document clustering

---

## 🔹 Important Interview Points

- K-Means is unsupervised
- Uses distance (usually Euclidean)
- Minimizes WCSS
- Elbow method for choosing K

---

## 🔹 Advanced Tip

👉 Use **k-means++ initialization** for better centroid selection:

```python
kmeans = KMeans(n_clusters=3, init='k-means++', random_state=42)
```

---

## 🔹 Final Summary

K-Means is a powerful clustering algorithm that:

- Groups similar data
- Is fast and scalable
- Requires careful selection of K

👉 Very commonly used in real-world ML problems.

---

**End of Notes ✅**


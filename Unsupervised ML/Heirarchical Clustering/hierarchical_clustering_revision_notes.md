# Hierarchical Clustering – Detailed Notes (with Code)

---

# 1. What is Hierarchical Clustering?

Hierarchical Clustering is an **unsupervised machine learning algorithm** used to group similar data points into clusters.

➡ No labels required  
➡ Builds a hierarchy (tree structure)

It does NOT require pre-defining number of clusters (unlike K-Means).

---

# 2. Types of Hierarchical Clustering

## 2.1 Agglomerative Clustering (Bottom-Up) 🔥

- Start with each data point as its own cluster
- Merge closest clusters step-by-step
- Continue until all points form one cluster

➡ Most commonly used

---

## 2.2 Divisive Clustering (Top-Down)

- Start with all data in one cluster
- Split into smaller clusters
- Continue until each point is separate

➡ Less commonly used (complex)

---

# 3. How Agglomerative Clustering Works?

Step-by-step:

1. Treat each data point as a cluster
2. Compute distance between all clusters
3. Merge the two closest clusters
4. Update distance matrix
5. Repeat until one cluster remains

---

# 4. Distance Metrics

Used to calculate similarity between data points.

### Euclidean Distance

Distance = √[(x1−x2)² + (y1−y2)²]

### Manhattan Distance

Distance = |x1−x2| + |y1−y2|

---

# 5. Linkage Methods (VERY IMPORTANT 🔥)

Defines how distance between clusters is calculated.

## 5.1 Single Linkage

Distance = minimum distance between points of two clusters

➡ Can form chain-like clusters

---

## 5.2 Complete Linkage

Distance = maximum distance between points

➡ Produces tight clusters

---

## 5.3 Average Linkage

Distance = average of all distances

➡ Balanced approach

---

## 5.4 Ward Method (Most Important 🔥)

Minimizes variance within clusters

➡ Produces compact and well-separated clusters

---

# 6. Dendrogram (Core Concept 🔥)

A **dendrogram** is a tree diagram that shows how clusters are merged.

### Axes:

- X-axis → data points
- Y-axis → distance between clusters

---

## 6.1 How to Read Dendrogram?

- Each horizontal line = merge
- Height = distance between clusters

---

## 6.2 Choosing Number of Clusters

➡ Cut dendrogram at point where vertical distance is largest

This gives optimal number of clusters.

---

# 7. Example Intuition

Points:

A, B, C, D

Steps:

- A + B → Cluster 1
- C + D → Cluster 2
- Merge Cluster 1 & 2 → Final cluster

---

# 8. Python Code (Important 🔥)

## 8.1 Plot Dendrogram

```python
import scipy.cluster.hierarchy as sch
import matplotlib.pyplot as plt

# Plot dendrogram
plt.figure()
sch.dendrogram(sch.linkage(X, method='ward'))
plt.show()
```

---

## 8.2 Agglomerative Clustering Model

```python
from sklearn.cluster import AgglomerativeClustering

model = AgglomerativeClustering(n_clusters=3, linkage='ward')
y_pred = model.fit_predict(X)

print(y_pred)
```

---

# 9. Advantages

- No need to define clusters initially
- Easy visualization using dendrogram
- Works well for small datasets

---

# 10. Limitations

- Computationally expensive (slow for large data)
- Cannot undo merges (greedy algorithm)

---

# 11. Key Concepts Summary

Hierarchical Clustering → builds tree of clusters  

Agglomerative → bottom-up approach  
Divisive → top-down approach  

Linkage → defines cluster distance  
Dendrogram → helps choose clusters  

Goal → group similar data points effectively 🚀


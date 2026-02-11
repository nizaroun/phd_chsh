# 09 Clustering (Regroupement)

## 1. Definition (Définition)

**Clustering** is an **Unsupervised Learning** (*Apprentissage non supervisé*) technique that groups unlabeled data points into clusters such that:
-   Points in the same cluster are **similar** (Introduction-cluster similarity).
-   Points in different clusters are **dissimilar** (Inter-cluster similarity).

### Types of Clustering
1.  **Hard Clustering**: Each point belongs to exactly one cluster.
2.  **Soft (Fuzzy) Clustering**: A point can belong to multiple clusters with a degree of membership (e.g., Fuzzy C-Means).

---

## 2. K-Means Clustering

A **partitioning** method that divides data into $K$ non-overlapping clusters.

### Algorithm
1.  Initialize **K** centroids randomly.
2.  **Assignment**: Assign each point to the nearest centroid.
3.  **Update**: Calculate new centroids (mean of points in the cluster).
4.  Repeat 2-3 until centroids stop moving (convergence).

### Objective Function (WCSS)
Minimizes the **Within-Cluster Sum of Squares**:
$$WCSS = \sum_{k=1}^{K} \sum_{x_i \in C_k} ||x_i - \mu_k||^2$$

> [!TIP] Choosing K (The Elbow Method)
> Plot WCSS vs. $K$. Look for the "elbow" where the reduction in WCSS slows down.

---

## 3. Hierarchical Clustering (Clustering Hiérarchique)

Builds a hierarchy of clusters (dendrogram).

### Types
-   **Agglomerative** (Bottom-Up): Start with $N$ clusters, merge closest pairs.
-   **Divisive** (Top-Down): Start with 1 cluster, split recursively.

### Linkage Methods (Mesures de distance)
How to measure distance between two clusters $A$ and $B$?
1.  **Single Linkage**: Min distance between points in A and B (can result in "chaining").
2.  **Complete Linkage**: Max distance.
3.  **Average Linkage**: Average distance.
4.  **Ward's Method**: Minimize variance increase on merge.

---

## 4. DBSCAN (Density-Based Spatial Clustering)

Groups points that are closely packed together.

### Parameters
-   **Eps ($\epsilon$)**: Radius of neighborhood.
-   **MinPts**: Min points in $\epsilon$-radius to form a dense region.

### Point Types
-   **Core Point**: Has $\ge MinPts$ neighbors within $\epsilon$.
-   **Border Point**: Reachable from a Core Point but has $< MinPts$ neighbors.
-   **Noise**: Not reachable from any Core Point (Outlier).

---

## 5. Other Algorithms
-   **GMM (Gaussian Mixture Models)**: Probabilistic model using soft clustering.
-   **Mean-Shift**: Mode seeking algorithm.
-   **BIRCH**: For very large datasets.

---

## 6. Evaluation (Validation)

### Silhouette Score
Measures how similar a point is to its own cluster compared to other clusters.
$$s(i) = \frac{b(i) - a(i)}{\max(a(i), b(i))}$$
> [!CHECK] Interpretation
> -   **+1**: Well separated (Good).
> -   **0**: Overlapping.
> -   **-1**: Wrong cluster.

---

## 7. Applications
-   **Customer Segmentation**: Grouping customers by purchasing behavior.
-   **Image Segmentation**: Grouping pixels by color/texture.
-   **Anomaly Detection**: Identifying noise/outliers (DBSCAN).
-   **Genetics**: Grouping genes with similar expression patterns.

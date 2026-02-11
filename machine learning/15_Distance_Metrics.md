# 08 Distance Metrics (Mesures de Distance)

In Machine Learning, **Distance Metrics** quantify the similarity or dissimilarity between two data points. The choice of metric is critical for distance-based algorithms like **KNN**, **K-Means**, and **Hierarchical Clustering**.

---

## 1. Euclidean Distance (Distance Euclidienne)

The "straight-line" distance between two points in Euclidean space. Corresponds to the L2 Norm.

$$d(p, q) = \sqrt{\sum_{i=1}^{n} (p_i - q_i)^2}$$

> [!TIP] Use Case
> General purpose metric for **continuous numerical data** (e.g., physical attributes like height, weight).
>
> **Caveat**: Sensitive to the scale of features. **Always normalize** data before using.

---

## 2. Manhattan Distance (Distance de Manhattan)

Also known as **L1 Norm** or "TaxiCab" distance. It is the sum of absolute differences.

$$d(p, q) = \sum_{i=1}^{n} |p_i - q_i|$$

> [!TIP] Use Case
> High-dimensional data where Euclidean distance becomes less meaningful (curse of dimensionality), or grid-like conceptual data.
>
> **Property**: More **robust to outliers** than Euclidean distance.

---

## 3. Minkowski Distance (Distance de Minkowski)

A generalization of both Euclidean and Manhattan distances.

$$d(p, q) = \left( \sum_{i=1}^{n} |p_i - q_i|^p \right)^{\frac{1}{p}}$$

> [!NOTE] Parameter p
> -   **p = 1**: Manhattan Distance.
> -   **p = 2**: Euclidean Distance.
> -   **p = $\infty$**: Chebyshev Distance.

---

## 4. Chebyshev Distance (Distance de Chebyshev)

The maximum distance along any coordinate dimension. Known as the "Chessboard distance".

$$d(p, q) = \max_i(|p_i - q_i|)$$

---

## 5. Cosine Distance/Similarity (Distance/Similitude Cosinus)

Measures the cosine of the angle between two vectors. It measures **orientation**, not magnitude.

$$CosineSimilarity = \frac{A \cdot B}{||A|| \cdot ||B||}$$

> [!IMPORTANT] Use Case
> **Text Mining**, **Document Similarity**.
> In text analysis, two documents can be similar even if one is much longer than the other (frequency count vs angle).

---

## 6. Hamming Distance (Distance de Hamming)

The number of positions at which corresponding symbols are different between two strings of equal length.

$$d(p, q) = \sum_{i=1}^{n} 1_{p_i \neq q_i}$$

> [!TIP] Use Case
> **Categorical Data**, **Binary Data**, **Error Correction**.
> *Example*: "10**1**1**1**01" vs "10**0**1**0**01" -> distance is 2.

---

## 7. Jaccard Distance/Index (Distance/Indice de Jaccard)

Measures similarity between finite sample sets (Intersection over Union).

$$J(A, B) = \frac{|A \cap B|}{|A \cup B|}$$

> [!TIP] Use Case
> **Object Detection** (IoU), **Comparing sets** (e.g., items bought by two customers).

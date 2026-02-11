# 04 K-Nearest Neighbors (K-Plus Proches Voisins - KNN)

## 1. Definition (Définition)

**K-Nearest Neighbors (KNN)** is a **lazy learning** (*apprentissage paresseux*) algorithm used for classification and regression. It makes predictions based on the $k$ training examples closest to the new instance.

> [!NOTE] Characteristics
> -   **Non-parametric**: Makes no assumptions about the underlying data distribution.
> -   **Lazy**: Does not learn a model during training. All computation happens at prediction time.

---

## 2. Algorithm Steps (Étapes)

1.  Choose the number of neighbors, **k**.
2.  Choose a **distance metric** (e.g., Euclidean).
3.  For a new sample $x_{new}$:
    -   Calculate the distance between $x_{new}$ and every point in the training set.
    -   Select the **k** points with the smallest distances.
    -   **Classification**: Assign the majority class among the $k$ neighbors. *(Optional: Weighted voting by inverse distance)*.
    -   **Regression**: Assign the average value of the $k$ neighbors.

---

## 3. Choosing K (Choix de K)

> [!TIP] K Tradeoff
> -   **Small K (e.g., K=1)**: High Variance. Risk of **Overfitting**. Sensitive to noise.
> -   **Large K**: High Bias. Risk of **Underfitting**. Smooth decision boundary.
> -   **Heuristic**: Start with $k = \sqrt{N}$. Use odd numbers for binary classification.

---

## 4. Distance Metrics (Mesures de distance)

The choice of distance is critical.

-   **Euclidean Distance**: Most common for continuous variables.
    $$d(p, q) = \sqrt{\sum (p_i - q_i)^2}$$
-   **Manhattan Distance**: Good for high dimensions.
    $$d(p, q) = \sum |p_i - q_i|$$

> [!NOTE] Reference
> See **08_Distance_Metrics** for a detailed list (Minkowski, Hamming, Cosine, Jaccard).

---

## 5. Pros & Cons

| Advantages | Disadvantages |
| :--- | :--- |
| **Simple**: Very easy to understand and implement. | **Slow**: Computionally expensive at prediction time ($O(N)$). |
| **No Assumptions**: Works well for non-linear data. | **Memory**: Must store the entire training dataset. |
| **Versatile**: Works for classification and regression. | **Curse of Dimensionality**: Performance degrades in high dimensions. |
| | > [!WARNING] Scaling <br> **Feature Scaling** is mandatory. Features with large ranges will dominate distance calculations. |

---

## 6. Applications

-   **Image/Handwriting Recognition**: Classifying digits (MNIST) based on pixel similarity.
-   **Recommender Systems**: Finding similar users or items.
-   **Finance**: Credit scoring (finding similar past customers).
-   **Biology**: Gene expression classification.

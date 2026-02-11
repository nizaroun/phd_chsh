# 11 Principal Component Analysis (ACP) (Analyse en Composantes Principales)

## 1. Core Concept (Concept Principal)

**Principal Component Analysis (PCA)** is an **unsupervised learning** (*apprentissage non supervisé*) technique used for **dimensionality reduction** (*réduction de dimension*).

> [!TIP] Goal
> Transform a set of correlated variables into a smaller set of **uncorrelated** variables called **Principal Components** (*Composantes Principales*), while maximizing the retained **variance**.

---

## 2. The Algorithm (L'Algorithme)

1.  **Standardization** (*Centrage et Réduction*):
    $$z = \frac{x_i - \mu}{\sigma}$$
    > [!WARNING] Crucial Step
    > If you skip this, variables with large units (e.g., Salary) will dominate variables with small units (e.g., Age).

2.  **Covariance Matrix** (*Matrice de Covariance*):
    Compute $\Sigma$ to understand how variables vary together.
    $$\Sigma = \frac{1}{n-1} X^T X$$

3.  **Eigendecomposition** (*Décomposition en Valeurs Propres*):
    Solve $det(\Sigma - \lambda I) = 0$.
    -   **Eigenvalues ($\lambda$)**: The *amount* of variance explained.
    -   **Eigenvectors ($v$)**: The *direction* of the new axis.

4.  **Selection**:
    Sort $\lambda$ in descending order. Keep the top $k$ components.
    > [!NOTE] Selection Criteria
    > -   **Kaiser's Criterion**: $\lambda > 1$.
    > -   **Scree Plot** (*Éboulis*): Keep until the "elbow".
    > -   **Explained Variance**: Keep 90-95% of total variance.

5.  **Projection**:
    $$X_{new} = X \cdot W$$

---

## 3. Key Concepts

### Explained Variance Ratio (*Taux de Variance Expliquée*)
How much information does the $i$-th component hold?
$$Ratio = \frac{\lambda_i}{\sum \lambda_j}$$

### Reconstruction Error (*Erreur de Reconstruction*)
PCA minimizes the squared distance between the original data point and its projection.

---

## 4. Pros & Cons

| Advantages | Disadvantages |
| :--- | :--- |
| **Dimensionality Reduction**: Removes noise, speeds up algorithms. | **Information Loss**: Some variance is inevitably lost. |
| **Visualization**: Allows visualizing high-dimensional data in 2D/3D. | **Interpretability**: Principal Components are linear combinations of original features (hard to interpret). |
| **Uncorrelated**: Removes multicollinearity. | **Linear**: Fails to capture non-linear relationships (use Kernel PCA or t-SNE). |

---

## 5. Vocabulary Cheat Sheet

| English | French | Definition |
| :--- | :--- | :--- |
| **Orthogonal** | *Orthogonal* | Perpendicular ($v_1 \cdot v_2 = 0$). |
| **Loadings** | *Saturations* | Correlation between original features and the PC. |
| **Eigenvalue** | *Valeur Propre* | Magnitude of variance. |
| **Eigenvector** | *Vecteur Propre* | Direction of axis. |

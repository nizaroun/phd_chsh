# 10 Support Vector Machine (SVM) (Machine à Vecteurs de Support)

## 1. Core Definition (Définition)

**Support Vector Machine (SVM)** is a supervised learning algorithm used for classification and regression.

> [!TIP] Goal
> Find the optimal **Hyperplane** (*Hyperplan*) that separates classes with the **Maximum Margin** (*Marge Maximale*).

*   **Support Vectors** (*Vecteurs de Support*): The data points closest to the hyperplane. They are the *only* points that determine the boundary.

---

## 2. Mathematical Formulation (*Formulation Mathématique*)

### A. The Primal Problem (*Problème Primal*)
$$
\min_{w,b} \frac{1}{2}||w||^2
$$
**Subject to**: $y_i(w^T x_i + b) \geq 1$

### B. The Dual Problem (*Problème Dual*)
Instead of solving for $w$ and $b$ directly, we solve for Lagrange multipliers $\alpha$.

$$
L(\alpha) = \sum_{i=1}^{n} \alpha_i - \frac{1}{2} \sum_{i=1}^{n} \sum_{j=1}^{n} \alpha_i \alpha_j y_i y_j (x_i \cdot x_j)
$$

> [!IMPORTANT] Exam Memorization
> The dual form depends only on the **dot product** $(x_i \cdot x_j)$. This allows the use of the **Kernel Trick**.

---

## 3. The Kernel Trick (*Astuce du Noyau*)

What if data is not linearly separable? We map it to a higher-dimensional space using a **Kernel Function** $K(x, y)$ without actually computing the coordinates.

$$K(x_i, x_j) = \phi(x_i) \cdot \phi(x_j)$$

> [!NOTE] Common Kernels
> -   **Linear**: $K(x, y) = x^T y$
> -   **Polynomial**: $K(x, y) = (x^T y + c)^d$
> -   **RBF (Radial Basis Function)**: $K(x, y) = \exp(-\gamma ||x - y||^2)$ (Infinite dimensions!)

---

## 4. Soft Margin & C Parameter (*Marge Souple*)

Used for non-linearly separable data (noise/outliers). We allow some misclassification.

$$
\min \frac{1}{2}||w||^2 + C \sum \xi_i
$$

> [!WARNING] Hyperparameter C
> -   **High C**: Strict. Hard Margin. Low bias, High variance (*Risk of Overfitting*).
> -   **Low C**: Loose. Soft Margin. High bias, Low variance (*Wider margin*).

---

## 5. Pros & Cons

| Advantages | Disadvantages |
| :--- | :--- |
| **High Accuracy**: Works very well in high-dimensional spaces. | **Slow**: Training time scales with $O(N^2)$ or $O(N^3)$, bad for large datasets. |
| **Efficient**: Uses only a subset of training points (Support Vectors). | **Noise**: Sensitive to noise and outliers (unless soft margin is tuned). |
| **Versatile**: Different kernels for different data structures. | **No Probabilities**: Does not directly provide probability estimates (unlike Logistic Regression). |

---

## 6. SVM vs Neural Networks

> [!SUMMARY] Comparison
> -   **Optimization**: SVM is **Convex** (Global Minimum). NN is **Non-Convex** (Local Minimum).
> -   **Data Size**: SVM is good for Small/Medium data. NN needs Massive data.
> -   **Interpretability**: SVM is better (via Support Vectors).

# 03 Logistic Regression (Régression Logistique)

## 1. Definition (Définition)

**Logistic Regression** (*Régression Logistique*) is a **classification** algorithm (despite its name) used to predict the probability that an instance belongs to a specific class (usually binary: 0 or 1).

$$0 \leq h_\theta(x) \leq 1$$

It uses the **Sigmoid Function** (or Logistic Function) to map predictions to probabilities.

---

## 2. Hypothesis Representation (Représentation de l'hypothèse)

$$h_\theta(x) = g(\theta^T x)$$

Where $g(z)$ is the **Sigmoid function** (*Fonction Sigmoïde*):

$$g(z) = \frac{1}{1 + e^{-z}}$$

**Interpretation**:
-   $h_\theta(x)$ = estimated probability that $y=1$ on input $x$.
-   **Decision Boundary** (*Frontière de décision*):
    -   If $h_\theta(x) \geq 0.5 \rightarrow$ Predict $y=1$
    -   If $h_\theta(x) < 0.5 \rightarrow$ Predict $y=0$

---

## 3. Cost Function (Fonction Coût - Log Loss)

We cannot use MSE (Mean Squared Error) because the hypothesis is non-linear (sigmoid), leading to a non-convex function with many local optima. Instead, we use **Log Loss** (*Entropie croisée*).

$$J(\theta) = - \frac{1}{m} \sum_{i=1}^{m} [ y^{(i)} \log(h_\theta(x^{(i)})) + (1 - y^{(i)}) \log(1 - h_\theta(x^{(i)})) ]$$

-   If $y=1$: Cost is $- \log(h_\theta(x))$. Cost $\rightarrow 0$ as prediction $\rightarrow 1$.
-   If $y=0$: Cost is $- \log(1 - h_\theta(x))$. Cost $\rightarrow 0$ as prediction $\rightarrow 0$.

This function is **convex**, ensuring Gradient Descent finds the global minimum.

---

## 4. Optimization (Descente de Gradient)

To minimize $J(\theta)$, we use Gradient Descent.

**Update Rule**:
$$\theta_j := \theta_j - \alpha \frac{\partial}{\partial \theta_j} J(\theta)$$

> [!IMPORTANT] Derivative of Sigmoid
> A key property that makes the math work is the derivative of the sigmoid function:
> $$g'(z) = g(z)(1 - g(z))$$

Using this property, the partial derivative becomes:
$$ \frac{\partial}{\partial \theta_j} J(\theta) = \frac{1}{m} \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)}) x_j^{(i)} $$

*Note: It looks exactly like Linear Regression, but $h_\theta(x)$ is different!*

---

## 5. Multiclass Classification (Classification Multi-classes)

Logistic Regression is naturally binary. For $K > 2$ classes:

### One-vs-Rest (OvR) / One-vs-All
-   Train $N$ separate binary classifiers.
-   Classifier $i$: distinguishing Class $i$ from all others.
-   Prediction: Pick class $i$ that maximizes $h_\theta^{(i)}(x)$.

### One-vs-One (OvO)
-   Train $N(N-1)/2$ classifiers (every pair of classes).
-   Final class selected by **Majority Vote**.

### Softmax Regression (Multinomial Logistic Regression)
-   Generalization of Logistic Regression for multi-class problems.
-   Outputs probabilities for each class that sum to 1.

$$P(y=k|x) = \frac{e^{z_k}}{\sum_{j=1}^{K} e^{z_j}}$$

---

## 6. Regularization (Régularisation)

To prevent **Overfitting** (*Sur-apprentissage*), we add a penalty to the cost function.

### L2 Regularization (Ridge)
Adds squared magnitude of coefficients. Keeps all features but reduces magnitude of weights.

$$J(\theta) + \lambda \sum_{j=1}^{n} \theta_j^2$$

### L1 Regularization (Lasso)
Adds absolute value of magnitude of coefficients. Can reduce weights to zero, performing **feature selection**.

$$J(\theta) + \lambda \sum_{j=1}^{n} |\theta_j|$$

-   $\lambda$: Regularization parameter. High $\lambda$ $\rightarrow$ High bias (Underfitting). Low $\lambda$ $\rightarrow$ High variance (Overfitting).

---

## 7. Imbalanced Data (Données Déséquilibrées)

When one class is dominant (e.g., 99% benign, 1% fraud).
*   **Problem**: Model tends to predict majority class always (High Accuracy, Low Recall).
*   **Solutions**:
    1.  **Undersampling**: Remove examples from majority class.
    2.  **Oversampling**: Duplicate examples from minority class.
    3.  **SMOTE**: Generate synthetic examples for minority class.
    4.  **Cost-Sensitive Learning**: Penalize errors on minority class more heavily.

---

## 8. Pros & Cons

| Advantages | Disadvantages |
| :--- | :--- |
| **Probabilistic**: Outputs probabilities, not just classes. | **Linear Decision Boundary**: Cannot solve non-linear problems (unless feature engineering/polynomials used). |
| **Efficient**: Very fast to train and predict. | **Outliers**: Sensitive to outliers. |
| **Interpretable**: Weights ($\theta$) indicate feature importance. | **Feature Engineering**: Requires careful feature selection. |

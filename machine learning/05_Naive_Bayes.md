# 05 Naive Bayes (Classification Naïve Bayes)

## 1. Definition (Définition)

**Naive Bayes** is a probabilistic classifier based on **Bayes' Theorem** with a strong (naive) independence assumption.

> [!TIP] Best Use Case
> It is particularly effective for **text classification** (*classification de texte*) and high-dimensional data (e.g., spam filtering).

---

## 2. Bayes' Theorem (Théorème de Bayes)

Describes the probability of an event, based on prior knowledge of conditions that might be related to the event.

$$P(C|X) = \frac{P(X|C) P(C)}{P(X)}$$

-   **$P(C|X)$**: **Posterior Probability** (*Probabilité a posteriori*).
-   **$P(C)$**: **Prior Probability** (*Probabilité a priori*).
-   **$P(X|C)$**: **Likelihood** (*Vraisemblance*).
-   **$P(X)$**: **Evidence** (*Probabilité marginale*).

---

## 3. The "Naive" Assumption (L'hypothèse naïve)

The algorithm assumes that all features $x_1, x_2, ..., x_n$ are **mutually independent** given the class $C$.

$$P(X|C) \approx \prod_{i=1}^{n} P(x_i | C)$$

> [!WARNING] Reality Check
> This assumption rarely holds in real life (e.g., words in a sentence are correlated), but the algorithm still performs surprisingly well.

**Decision Rule (MAP - Maximum A Posteriori)**:
$$\hat{y} = \arg\max_{c \in C} P(c) \prod_{i=1}^{n} P(x_i|c)$$

---

## 4. Handling Numerical Predictors (Prédicteurs Numériques)

If features are continuous ($X \in \mathbb{R}$), we have two main approaches:

1.  **Discretization** (*Binning*): Convert continuous values into buckets (Low, Medium, High).
2.  **Gaussian Assumption**: Assume data follows a **Normal Distribution**.
    $$P(x_i|C) = \frac{1}{\sqrt{2\pi\sigma_C^2}} \exp\left(-\frac{(x_i-\mu_C)^2}{2\sigma_C^2}\right)$$

---

## 5. Types of Naive Bayes Classifiers

1.  **Gaussian Naive Bayes**:
    -   Used for continuous features (as shown above).
2.  **Multinomial Naive Bayes**:
    -   Used for **discrete counts** (e.g., word frequencies).
3.  **Bernoulli Naive Bayes**:
    -   Used for **binary features** (e.g., word presence/absence).

---

## 6. Laplace Smoothing (Lissage de Laplace)

> [!IMPORTANT] Zero Frequency Problem
> If a word $x_i$ never appears in class $C$ during training, $P(x_i|C) = 0$. This zeros out the entire probability product.

**Solution**: Add a small constant $\alpha$ (usually 1) to all counts.

$$P(x_i|C) = \frac{count(x_i, C) + \alpha}{count(C) + \alpha \cdot d}$$

---

## 7. Pros & Cons

| Advantages | Disadvantages |
| :--- | :--- |
| **Fast**: Extremely fast to train and predict (linear time). | **Independence Assumption**: Naive. |
| **Small Data**: Performs well with less training data. | **Zero Frequency**: Needs smoothing. |
| **Multiclass**: Handles multiclass naturally. | |

---

## 8. Applications

-   **Spam Filtering**: Classifying emails (Spam / Ham).
-   **Sentiment Analysis**: Positive / Negative reviews.
-   **Fraud Detection**: Anomaly detection in bank transactions.
-   **Medical Diagnosis**: Predicting disease based on symptoms.

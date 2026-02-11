# 13 Unsupervised Learning Overview (Apprentissage Non Supervisé)

## 1. Definition (Définition)

**Unsupervised Learning** (*Apprentissage Non Supervisé*) is a type of machine learning where the algorithm learns patterns from **unlabeled data** (*données non étiquetées*).

> [!NOTE] Goal
> The system tries to learn without a teacher. There is no correct answer ($Y$) to predict. It finds hidden structures in the input ($X$).

---

## 2. Main Tasks (Tâches Principales)

### A. Clustering (Regroupement)
Grouping distinct data points so that points in the same group are more similar to each other than to those in other groups.
*   **Algorithms**: K-Means, DBSCAN, Hierarchical Clustering.
*   **Use Cases**: Customer segmentation, Image compression.
*   *(See Note 07 for details)*

### B. Dimensionality Reduction (Réduction de Dimension)
Reducing the number of random variables under consideration.
*   **Algorithms**: PCA, t-SNE, Autoencoders.
*   **Use Cases**: Visualization, Noise reduction, Speeding up training.
*   *(See Note 11 for details)*

### C. Association Rule Mining (Règles d'Association)
Discovering interesting relations between variables in large databases.
*   **Algorithms**: Apriori, Eclat, FP-Growth.
*   **Use Cases**: Market Basket Analysis (*Analyse du panier d'achat*).

---

## 3. Supervised vs Unsupervised

| Feature | Supervised | Unsupervised |
| :--- | :--- | :--- |
| **Input Data** | Labeled ($X, Y$) | Unlabeled ($X$) |
| **Goal** | Predict output | Find structure |
| **Feedback** | Direct feedback (Error) | No feedback |
| **Complexity** | Easier to evaluate | Hard to evaluate (Subjective) |

---

## 4. Association Rules (Règles d'Association)

> [!TIP] Example
> "People who buy **Diapers** also tend to buy **Beer**".
> Rule: $\{Diapers\} \rightarrow \{Beer\}$

### Key Metrics
1.  **Support** (*Support*): How popular an itemset is.
    $$Support(A) = \frac{\text{Transactions containing } A}{\text{Total Transactions}}$$

2.  **Confidence** (*Confiance*): Likelihood of $B$ given $A$.
    $$Confidence(A \rightarrow B) = \frac{Support(A \cup B)}{Support(A)}$$

3.  **Lift** (*Lift*): The rise in probability of having $B$ on the condition that $A$ occurs.
    $$Lift(A \rightarrow B) = \frac{Support(A \cup B)}{Support(A) \times Support(B)}$$
    -   **Lift > 1**: Positive correlation (A and B appear together more than expected).
    -   **Lift = 1**: Independent.
    -   **Lift < 1**: Negative correlation (A and B appear together less than expected).

---

## 5. Challenges

> [!WARNING] Evaluation
> Validating the results is difficult because there is no ground truth. "Is this cluster meaningful?" is often a domain-expert question, not a mathematical one.

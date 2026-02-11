# 11 Association Rules (Règles d'Association)

## 1. Definition (Définition)

**Association Rule Mining** is a rule-based machine learning method for discovering interesting relations between variables in large databases.

> [!TIP] Example
> "People who buy **Bread** also tend to buy **Butter**".
> Rule: $\{Bread\} \rightarrow \{Butter\}$

---

## 2. Key Metrics (Métriques Clés)

Given a rule $A \rightarrow B$:

### A. Support (*Support*)
How popular an itemset is.
$$Support(A) = \frac{\text{Transactions containing } A}{\text{Total Transactions}}$$

> [!NOTE] Usage
> Used to filter out infrequent items (pruning).

### B. Confidence (*Confiance*)
Likelihood of $B$ given $A$.
$$Confidence(A \rightarrow B) = \frac{Support(A \cup B)}{Support(A)}$$

> [!WARNING] Limitation
> High confidence can be misleading if $B$ is very popular overall (e.g., everyone buys bread).

### C. Lift (*Lift*)
The most important metric. It measures how much more likely $A$ and $B$ are to occur together than if they were independent.

$$Lift(A \rightarrow B) = \frac{Support(A \cup B)}{Support(A) \times Support(B)}$$

> [!CHECK] Interpretation
> -   **Lift > 1**: Positive correlation (A and B appear together **more** than expected).
> -   **Lift = 1**: Independent.
> -   **Lift < 1**: Negative correlation (Substitute products).

---

## 3. Apriori Algorithm (Algorithme Apriori)

Used to find frequent itemsets efficiently.

> [!TIP] Apriori Principle
> If an itemset is frequent, then all of its subsets must also be frequent.
> *Conversely*: If an itemset is infrequent, all its supersets are infrequent.

### Steps
1.  **Generate** candidate itemsets of size $k=1$.
2.  **Prune** those with Support < MinSupport.
3.  **Join** remaining itemsets to form candidates of size $k+1$.
4.  **Repeat** until no more candidates can be formed.
5.  **Generate Rules** from frequent itemsets where Confidence > MinConfidence.

---

## 4. Pros & Cons

| Advantages | Disadvantages |
| :--- | :--- |
| **Interpretable**: Simple if-then rules. | **Computation**: Exponential search space ($2^d$ combinations). |
| **No Labels**: Unsupervised. | **Correlations**: Finds correlation, not causality. |
| **Actionable**: Directly useful for marketing/sales. | **Redundancy**: Can generate too many similar rules. |

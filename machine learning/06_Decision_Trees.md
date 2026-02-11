# 06 Decision Trees (Arbres de Décision)

## 1. Definition (Définition)

**Decision Tree** (*Arbre de Décision*) is a supervised learning algorithm used for both **classification** and **regression**. It recursively splits the data into subsets based on the value of input features.

> [!NOTE] Structure
> -   **Root Node** (*Racine*): The entire dataset.
> -   **Internal Nodes** (*Nœuds internes*): Tests on attributes (e.g., "Is Age > 30?").
> -   **Branches** (*Branches*): Outcomes of the test (e.g., "Yes", "No").
> -   **Leaf Nodes** (*Feuilles*): Final prediction.

---

## 2. Splitting Criteria (Critères de division)

How do we decide which attribute to split on? We want the split that results in the most **homogeneous** (pure) child nodes.

### A. Entropy (*Entropie*)
Measures the impurity or randomness in a dataset $S$.
$$H(S) = - \sum_{i=1}^{c} p_i \log_2(p_i)$$
> [!TIP] Values
> -   **H(S) = 0**: Perfectly pure (all elements belong to one class).
> -   **H(S) = 1**: Maximal impurity (for binary class, 50/50 split).

### B. Information Gain (*Gain d'information*)
Used by **ID3** and **C4.5** algorithms. It measures the reduction in entropy expected from splitting on attribute $A$.
$$IG(S, A) = H(S) - \sum_{v \in Values(A)} \frac{|S_v|}{|S|} H(S_v)$$
> [!NOTE] Selection Rule
> We choose the attribute $A$ with the **highest Information Gain**.

### C. Gini Impurity (*Indice de Gini*)
Used by **CART** (Classification and Regression Trees). A measure of how often a randomly chosen element would be incorrectly labeled.
$$Gini(S) = 1 - \sum_{i=1}^{c} p_i^2$$
> [!TIP] Computation
> Gini is computationally **faster** than Entropy (no log calculation) but usually produces similar trees.

---

## 3. Step-by-Step Calculation Example

> [!IMPORTANT] Exam Scenario
> You are often given a small table and asked to calculate the Information Gain for a specific attribute.

**Dataset**: 14 Days. Target: **Play Tennis** (Yes/No).
-   **Total**: 9 Yes, 5 No.

### Step 1: Calculate Global Entropy ($H(S)$)
$$p_{yes} = \frac{9}{14}, \quad p_{no} = \frac{5}{14}$$
$$H(S) = - [\frac{9}{14} \log_2(\frac{9}{14}) + \frac{5}{14} \log_2(\frac{5}{14})] \approx \mathbf{0.940}$$

### Step 2: Calculate Entropy for Attribute "Wind"
Attribute **Wind** has 2 values: **Weak** and **Strong**.

1.  **Wind = Weak** (8 samples):
    -   6 Yes, 2 No.
    -   $H(Weak) = - [\frac{6}{8} \log_2(\frac{6}{8}) + \frac{2}{8} \log_2(\frac{2}{8})] \approx \mathbf{0.811}$

2.  **Wind = Strong** (6 samples):
    -   3 Yes, 3 No.
    -   $H(Strong) = - [\frac{3}{6} \log_2(\frac{3}{6}) + \frac{3}{6} \log_2(\frac{3}{6})] = \mathbf{1.00}$ (Max impurity)

### Step 3: Calculate Weighted Entropy
Sum of entropies weighted by the probability of each branch.
$$H(S | Wind) = \frac{8}{14} \times 0.811 + \frac{6}{14} \times 1.00 \approx \mathbf{0.892}$$

### Step 4: Calculate Information Gain ($IG$)
$$IG(S, Wind) = H(S) - H(S | Wind)$$
$$IG(S, Wind) = 0.940 - 0.892 = \mathbf{0.048}$$

*(Repeat for other attributes like Outlook, Humidity, Temp. Pick the one with the highest IG).*

---

## 4. Gini Calculation Example

Same dataset: 9 Yes, 5 No.

$$Gini(S) = 1 - [(\frac{9}{14})^2 + (\frac{5}{14})^2]$$
$$Gini(S) = 1 - [0.413 + 0.128] = 1 - 0.541 = \mathbf{0.459}$$

If we split on **Wind**:
1.  **Weak (6Y, 2N)**: $Gini(Weak) = 1 - [(\frac{6}{8})^2 + (\frac{2}{8})^2] = 0.375$
2.  **Strong (3Y, 3N)**: $Gini(Strong) = 1 - [0.5^2 + 0.5^2] = 0.5$

**Weighted Gini**:
$$Gini_{split} = \frac{8}{14}(0.375) + \frac{6}{14}(0.5) \approx \mathbf{0.428}$$

**Gini Gain**: $0.459 - 0.428 = \mathbf{0.031}$.

---

## 5. Overfitting & Pruning (Sur-apprentissage & Élagage)

> [!WARNING] Overfitting Risk
> Decision trees are prone to **Overfitting**: they can create overly complex trees that memorize the training data.

### Pre-Pruning (*Pré-élagage*)
Halt the tree construction early.
-   Max Depth (*Profondeur max*).
-   Min Samples per Leaf (*Min échantillons par feuille*).

### Post-Pruning (*Post-élagage*)
Build the full tree, then remove branches that do not provide significant predictive power.

---

## 6. Pros & Cons

| Advantages | Disadvantages |
| :--- | :--- |
| **Interpretable**: Easy to visualize and explain ("White Box"). | **High Variance**: Small changes in data can lead to very different trees. |
| **No Feature Scaling**: Can handle numerical and categorical data without normalization. | **Overfitting**: Easily overfits without pruning. |
| **Non-linear**: can model complex boundaries. | **Biased**: Can be biased towards dominant classes. |

---

## 7. Ensemble Methods (Méthodes d'Ensemble)

> [!SUMMARY] Solution
> To overcome the limitations (variance) of single trees:
> -   **Random Forest**: Builds many trees on random subsets and averages predictions.
> -   **Gradient Boosting**: Builds trees sequentially to correct errors.

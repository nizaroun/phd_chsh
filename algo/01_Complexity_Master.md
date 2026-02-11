# 01_Complexity_Master: Asymptotic Analysis

> [!abstract] **Résumé:**
> Analyzing the efficiency of algorithms (*efficacité des algorithmes*) as input size $n \to \infty$. Focus on **Time Complexity** (*Complexité Temporelle*) and **Space Complexity** (*Complexité Spatiale*).

---

## 1. Asymptotic Definitions (Définitions Asymptotiques)

| Notation | Definition | Intuition |
| :--- | :--- | :--- |
| **$O(g(n))$** | $\exists c, n_0 > 0 : 0 \le f(n) \le c \cdot g(n), \forall n \ge n_0$ | **Upper Bound** (*Borne Supérieure*) - Worst Case (*Pire Cas*). |
| **$\Omega(g(n))$** | $\exists c, n_0 > 0 : 0 \le c \cdot g(n) \le f(n), \forall n \ge n_0$ | **Lower Bound** (*Borne Inférieure*) - Best Case (*Meilleur Cas*). |
| **$\Theta(g(n))$** | $O(g(n)) \cap \Omega(g(n))$ | **Tight Bound** (*Borne Exacte*). |

> [!example] **Example (Exemple):**
> $f(n) = 3n^2 + 10n + 5$
> - $f(n) \in O(n^2)$ (and also $O(n^3)$)
> - $f(n) \in \Omega(n^2)$ (and also $\Omega(n)$)
> - $f(n) \in \Theta(n^2)$

---

## 2. Master Theorem (Théorème Maître)

For recurrences (*récurrences*) of the form:
$$T(n) = a T(n/b) + f(n)$$
where $a \ge 1, b > 1$. Let $k = \log_b a$.

| Case | Condition on $f(n)$ | Solution $T(n)$ |
| :--- | :--- | :--- |
| **1** | $f(n) = O(n^{k - \epsilon})$ for $\epsilon > 0$ | $\Theta(n^{\log_b a})$ |
| **2** | $f(n) = \Theta(n^k)$ | $\Theta(n^{\log_b a} \log n)$ |
| **3** | $f(n) = \Omega(n^{k + \epsilon})$ & regularity* | $\Theta(f(n))$ |

> (*) **Regularity Condition (Condition de Régularité):** $a f(n/b) \le c f(n)$ for some $c < 1$.

---

## 3. Classic Recurrences (Récurrences Classiques)

| Algorithm | Recurrence | Complexity |
| :--- | :--- | :--- |
| **Binary Search** (*Dichotomie*) | $T(n) = T(n/2) + O(1)$ | $O(\log n)$ |
| **Merge Sort** (*Tri Fusion*) | $T(n) = 2T(n/2) + O(n)$ | $O(n \log n)$ |
| **Towers of Hanoi** (*Tours de Hanoï*) | $T(n) = 2T(n-1) + O(1)$ | $O(2^n)$ |
| **Stooge Sort** | $T(n) = 3T(2n/3) + O(1)$ | $O(n^{2.709})$ |

### Strassen's Matrix Multiplication (*Multiplication Matricielle*)
Standard method is $O(n^3)$. Strassen uses divide & conquer (*diviser pour régner*) with 7 multiplications (instead of 8):
$$ T(n) = 7T(n/2) + O(n^2) $$
**Master Theorem Application:**
- $a=7, b=2 \implies \log_2 7 \approx 2.807$
- $f(n) = n^2 = O(n^{2.807 - \epsilon})$ -> **Case 1**
- **Result:** $T(n) = \Theta(n^{\log_2 7}) \approx O(n^{2.81})$

---

> [!question] **Exam Tip (Conseil d'Examen):**
> If solving $T(n) = T(n-1) + n$, this is an **arithmetic sum** (*somme arithmétique*): $\sum_{i=1}^n i = \frac{n(n+1)}{2} = \Theta(n^2)$.
> If solving $T(n) = T(n-1) + 1$, this is linear (*linéaire*): $T(n) = n$.

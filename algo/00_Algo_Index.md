# 00_Algo_Index: Map of Content (MOC)

> [!INFO] **Objectif:** Préparation Concours Doctorat - *Algorithmique Avancée & Complexité*
> **Université:** Sétif 1 (UFAS1)

---

## 🗺️ Navigation Principale

The core modules for the exam, broken down by topic:

- **[[01_Complexity_Master]]** ➡️ *Start Here*
    - $O, \Omega, \Theta$ definitions.
    - **Théorème Maître** (Master Theorem).
    - Solving Recurrences (Substitution, Iteration).

- **[[02_Linear_Structures]]** ➡️ *Pointer Mastery*
    - `struct`, `malloc`, `free`.
    - Linked Lists (Simple/Double/Circular).
    - Stacks (*Piles*) & Queues (*Files*).

- **[[03_Sorting_Heaps]]** ➡️ *Divide & Conquer*
    - Binary Trees (*Arbres Binaires*).
    - Heaps (*Tas*) & HeapSort (*Tri par Tas*).
    - MergeSort (*Tri Fusion*) & QuickSort (*Tri Rapide*).

- **[[04_Graphs_Advanced]]** ➡️ *Graph Theory*
    - BFS/DFS Traversals (*Parcours*).
    - Shortest Path (Dijkstra, Floyd-Warshall).
    - MST (Kruskal, Prim).
    - P vs NP (*Complexité*).

---

## ✅ Checklist de Révision (Exam Day)

### 1. Complexité & Récurrences
- [ ] Memorize the **Master Theorem** cases for $T(n) = aT(n/b) + f(n)$.
- [ ] Know the limit definitions: $\lim_{n \to \infty} \frac{f(n)}{g(n)}$.
- [ ] Stirling's approximation for $n!$: $\ln(n!) \approx n \ln n$.

### 2. Structures de Données (C Implementation)
- [ ] Write `struct Node` for List, Tree, Graph from scratch.
- [ ] Handle **Edge Cases**: Empty list (`head == NULL`), single element.
- [ ] Always check `malloc` return value.

### 3. Algorithmes Classiques
- [ ] **QuickSort:** Worst case $O(n^2)$ vs Average $O(n \log n)$.
- [ ] **BFS vs DFS:** Queue vs Stack implementation.
- [ ] **Dijkstra:** Priority Queue usage ($O(E \log V)$).
- [ ] **Dynamic Programming:** Identify "Sub-problems" & "Optimal Substructure".

---

> [!TIP] **Last Minute Reminder**
> "Diviser pour Régner" solutions often have $T(n) = aT(n/b) + O(n)$.
> "Programmation Dynamique" is about **Table Filling** (Memoization).

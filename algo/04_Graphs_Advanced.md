# 04_Graphs_Advanced: Graph Theory & DP

> [!abstract] **Résumé:**
> Algorithms for traversing graphs (*parcours de graphes*), finding shortest paths (*plus courts chemins*), and Dynamic Programming (*Programmation Dynamique*).

---

## 1. Graph Traversals (Parcours de Graphes)

### BFS (Breadth-First Search / *Parcours en Largeur*)
- **Data Structure:** Queue (*File*).
- **Use Case:** Shortest path in unweighted graphs (*graphes non pondérés*).
- **Complexity:** $O(V + E)$ (Adjacency List).

### DFS (Depth-First Search / *Parcours en Profondeur*)
- **Data Structure:** Stack (*Pile*) or Recursion (*Récursivité*).
- **Use Case:** Cycle detection (*détection de cycle*), Topological Sort (*Tri Topologique*).
- **Complexity:** $O(V + E)$.

```c
// DFS Recursive (DFS Récursif)
void DFS(int u, int visited[], Graph* G) {
    visited[u] = 1;
    printf("%d ", u);
    Node* temp = G->adjLists[u];
    while (temp) {
        int v = temp->val;
        if (!visited[v])
            DFS(v, visited, G);
        temp = temp->next;
    }
}
```

---

## 2. Shortest Path (Plus Court Chemin)

### Dijkstra's Algorithm (Algorithme de Dijkstra)
- **Type:** Greedy (*Glouton*).
- **Constraint:** No negative weights (*pas de poids négatifs*).
- **Logic:** Expand node with smallest distance from Priority Queue (*File de Priorité*).
- **Complexity:** $O(E \log V)$ or $O(E + V \log V)$.

### Floyd-Warshall Algorithm (Algorithme de Floyd-Warshall)
- **Type:** Dynamic Programming (*Programmation Dynamique*).
- **Logic:** All-pairs shortest path (*toutes les paires*).
- **Recurrence:**
  $$D_{ij}^{(k)} = \min(D_{ij}^{(k-1)}, D_{ik}^{(k-1)} + D_{kj}^{(k-1)})$$
- **Complexity:** $O(V^3)$.

---

## 3. MST (Arbre Couvrant Minimum / ACM)

### Kruskal's Algorithm
- **Logic:** Sort edges by weight (*trier les arêtes par poids*). Add edge if it doesn't form a cycle (use Union-Find).
- **Complexity:** $O(E \log E)$.

### Prim's Algorithm
- **Logic:** Grow tree from a starting node. Add cheapest edge connecting tree to outside (*arête la moins chère*).
- **Complexity:** $O(E \log V)$.

---

## 4. Dynamic Programming (Programmation Dynamique)
**Paradigm:** Break down problem into overlapping subproblems (*sous-problèmes chevauchants*) + Memoization/Tabulation.

### 0/1 Knapsack Problem (Problème du Sac à Dos)
- **Goal:** Maximize value $V$ without exceeding weight $W$.
- **Recurrence:**
  $$K[i][w] = \max(K[i-1][w], \text{val}[i] + K[i-1][w - \text{wt}[i]])$$
- **Complexity:** $O(N \cdot W)$ (Pseudo-polynomial).

| item | weight | value |
| :--- | :--- | :--- |
| **Row Logic** | keep previous best | max(keep, new + leftover capacity) |

---

## 5. Complexity Classes (Classes de Complexité)
- **P:** Solvable in polynomial time (*temps polynomial*).
- **NP:** Verifiable in polynomial time (*vérifiable en temps polynomial*).
- **NP-Complete (NP-Complet):** The hardest problems in NP (e.g., SAT, TSP). If one is solved in P, all are.
- **NP-Hard (NP-Difficile):** At least as hard as NP-Complete, but not necessarily in NP.

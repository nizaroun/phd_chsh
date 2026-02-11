# 03_Sorting_Heaps: Divide & Conquer + Trees

> [!abstract] **Résumé:**
> Mastering recursive sorting algorithms (*algorithmes de tri récursifs*) and heap data structures (*structures de tas*).

---

## 1. Heaps (Tas) - Priority Queue
A **Binary Heap** (*Tas Binaire*) is a complete binary tree (*arbre binaire complet*) satisfying the **Heap Property** (*Propriété de Tas*).

- **Max-Heap** (*Tas-Max*): Parent $\ge$ Children ($A[i] \ge A[2i]$ & $A[i] \ge A[2i+1]$).
- **Min-Heap** (*Tas-Min*): Parent $\le$ Children.

### Array Representation (Représentation par Tableau)
For a node at index $i$ (1-based index):
- **Left Child** (*Fils Gauche*): $2i$
- **Right Child** (*Fils Droit*): $2i + 1$
- **Parent** (*Père*): $\lfloor i/2 \rfloor$

### Key Operations (Opérations Clés)
| Operation | Complexity | Description |
| :--- | :--- | :--- |
| `heapify` (entasser) | $O(\log n)$ | Maintain heap property downwards (*Maintenir la propriété vers le bas*). |
| `build_heap` (construire) | $O(n)$ | Convert array to heap (*Convertir tableau en tas*). |
| `heap_sort` (tri par tas) | $O(n \log n)$ | Extract max repeatedly (*Extraire le max de fois répétées*). |

```c
// Max-Heapify (Entasser Max)
void heapify(int arr[], int n, int i) {
    int largest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;

    if (left < n && arr[left] > arr[largest])
        largest = left;
    if (right < n && arr[right] > arr[largest])
        largest = right;

    if (largest != i) {
        swap(&arr[i], &arr[largest]); 
        heapify(arr, n, largest); // Recursion (Récursivité)
    }
}
```

---

## 2. QuickSort (Tri Rapide)
**Divide & Conquer** (*Diviser pour Régner*). Sorts in-place (*tri sur place*).
- **Key Idea:** Pick a **pivot** (*pivot*), partition array so elements < pivot are left, > pivot are right.

### Partition Schemes (Schémas de Partition)
- **Lomuto:** Simpler, uses last element as pivot.
- **Hoare:** More efficient, two pointers moving inwards.

| Complexity | Time | Space | Notes |
| :--- | :--- | :--- | :--- |
| **Best/Average** | $O(n \log n)$ | $O(\log n)$ | Balanced partitions (*Partitions équilibrées*). |
| **Worst Case** | $O(n^2)$ | $O(n)$ | Pivot is min/max (sorted array). |

```c
// Lomuto Partition (Partition de Lomuto)
int partition(int arr[], int low, int high) {
    int pivot = arr[high]; // Pivot at end (Pivot à la fin)
    int i = (low - 1); 

    for (int j = low; j <= high - 1; j++) {
        if (arr[j] < pivot) {
            i++; 
            swap(&arr[i], &arr[j]);
        }
    }
    swap(&arr[i + 1], &arr[high]);
    return (i + 1);
}
```

---

## 3. MergeSort (Tri Fusion)
**Divide & Conquer** (*Diviser pour Régner*). Stable sort (*tri stable*).
- **Key Idea:** Split array in half, sort recursively, then **merge** (*fusionner*) sorted halves.

| Complexity | Time | Space | Notes |
| :--- | :--- | :--- | :--- |
| **All Cases** | $O(n \log n)$ | $O(n)$ | Consistently fast, but uses extra memory (*Mémoire supplémentaire*). |

> [!important] **Comparison (Comparaison):**
> - **QuickSort** is faster in practice (cache locality), but unstable (*instable*).
> - **MergeSort** is stable and guarantees $O(n \log n)$ but needs $O(n)$ space.

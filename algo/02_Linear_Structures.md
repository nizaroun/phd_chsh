# 02_Linear_Structures: Pointer Mastery

> [!abstract] **Résumé:**
> In-depth guide to dynamic memory (*mémoire dynamique*) and linked structures. Mastering pointers (*pointeurs*) is critical for C exams.

---

## 1. Memory Management (Gestion de la Mémoire)

### Core Functions (Fonctions Principales)
- `malloc(size_t size)`: Allocates a block of memory (*block mémoire*). Returns `void*`.
- `free(void* ptr)`: Deallocates memory (*désalloue la mémoire*).
- `sizeof(type)`: Returns size in bytes (*taille en octets*).

```c
typedef struct Node {
    int val;
    struct Node* next; // Pointer to next node (Pointeur vers le suivant)
} Node;

// Allocation Routine (Routine d'Allocation)
Node* createNode(int v) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    if (!newNode) {
        printf("Erreur d'allocation\n");
        return NULL;
    }
    newNode->val = v;
    newNode->next = NULL;
    return newNode;
}
```

---

## 2. Linked Lists (Listes Chaînées)

### A. Singly Linked List (Liste Simplement Chaînée)
- **Structure:** Each node points to the next (*chaque nœud pointe vers le suivant*).
- **End:** Last node points to `NULL`.
- **Traversal:** One direction only (*un seul sens*).

### B. Doubly Linked List (Liste Doublement Chaînée)
- **Structure:** `prev` pointer (to previous) and `next` pointer (to next).
- **Advantage:** Can traverse backwards (*parcours arrière*); easier deletion given a node pointer.
- **Memory:** Uses more memory per node (*plus de mémoire par nœud*).

```c
typedef struct DNode {
    int val;
    struct DNode* prev; // Use 'prev'
    struct DNode* next;
} DNode;
```

### C. Circular Linked List (Liste Circulaire)
- **Structure:** Last node points back to `head` instead of `NULL`.
- **Use Case:** Round-robin scheduling (*ordonnancement*), buffering.
- **Traversal:** Watch out for infinite loops (*boucles infinies*)! Stop when `curr == head`.

---

## 3. Stacks (Piles) & Queues (Files)

### Stack (Pile) - LIFO
**Last In, First Out** (*Dernier Entré, Premier Sorti*).
- **Operations:** `push` (*empiler*), `pop` (*dépiler*).
- **Implementation:** Insert/Delete at `head` of a Linked List ($O(1)$).

```c
void push(Node** top, int v) {
    Node* newNode = createNode(v);
    newNode->next = *top;
    *top = newNode;
}

int pop(Node** top) {
    if (*top == NULL) return -1; // Underflow
    Node* temp = *top;
    int res = temp->val;
    *top = (*top)->next;
    free(temp);
    return res;
}
```

### Queue (File) - FIFO
**First In, First Out** (*Premier Entré, Premier Sorti*).
- **Operations:** `enqueue` (*enfiler*), `dequeue` (*défiler*).
- **Implementation:** Maintains `head` (for dequeue) and `tail` (for enqueue).

```c
typedef struct {
    Node *front, *rear;
} Queue;

// Enqueue: Add to Rear (Ajouter à la Queue)
void enqueue(Queue* q, int v) {
    Node* temp = createNode(v);
    if (q->rear == NULL) { // Empty Queue (File Vide)
        q->front = q->rear = temp;
        return;
    }
    q->rear->next = temp;
    q->rear = temp;
}

// Dequeue: Remove from Front (Retirer de la Tête)
int dequeue(Queue* q) {
    if (q->front == NULL) return -1; // Empty
    Node* temp = q->front;
    int res = temp->val;
    q->front = q->front->next;
    if (q->front == NULL) q->rear = NULL; // Queue became empty
    free(temp);
    return res;
}
```

---

## 4. Key Algorithms (Algorithmes Clés)

### Reversing a List (Inverser une Liste)
> [!important] **Classic Exam Question**
> Requires 3 pointers: `prev`, `curr`, `next`.

```c
Node* reverse(Node* head) {
    Node *prev = NULL, *curr = head, *next = NULL;
    while (curr != NULL) {
        next = curr->next; // 1. Save next
        curr->next = prev; // 2. Reverse link
        prev = curr;       // 3. Advance prev
        curr = next;       // 4. Advance curr
    }
    return prev; // New head
}
```

### Cycle Detection (Détection de Cycle)
**Floyd's Tortoise and Hare** (*Algorithme du Lièvre et de la Tortue*).
- `slow` moves 1 step. `fast` moves 2 steps.
- If they meet $\rightarrow$ Cycle exists.
- If `fast` hits `NULL` $\rightarrow$ No cycle.

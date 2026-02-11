# 12 Convolutional Neural Networks (CNN) (Réseaux de Neurones à Convolution)

## 1. Core Definition (Définition)

A **CNN** is a deep learning architecture specialized for processing **grid-structured data** (images, time-series).

> [!TIP] Key Properties
> 1.  **Local Connectivity** (*Connectivité locale*): Neurons only see a small patch of the input.
> 2.  **Parameter Sharing** (*Partage de poids*): The same filter is used across the whole image.
> 3.  **Translation Invariance**: Detects objects regardless of position.

---

## 2. Architecture Layers (Couches)

### A. Convolution Layer (*Couche de Convolution*)
Applies **Filters/Kernels** (*Filtres/Noyaux*) to extract features (edges, textures).

> [!NOTE] Output Size Formula
> $$H_{out} = \lfloor \frac{H_{in} - F + 2P}{S} \rfloor + 1$$
> -   $F$: Filter size.
> -   $P$: Padding.
> -   $S$: Stride.

### B. Pooling Layer (*Couche de Pooling*)
Performs **Downsampling** (*Sous-échantillonnage*) to reduce dimensionality.
-   **Max Pooling**: Takes max value (most common).
-   **Average Pooling**: Takes average.

> [!IMPORTANT] Params
> Pooling has **0 learnable parameters**.

### C. Fully Connected Layer (*Dense*)
Traditional MLP layers at the end for classification.

---

## 3. Advanced Concepts

### Batch Normalization
Normalizes layer inputs to mean 0 and variance 1.
> [!TIP] Benefit
> Accelerates training and adds slight regularization.

### Global Average Pooling (GAP)
Replaces Flattening. Takes the average of each feature map.
> [!CHECK] Pro
> Drastically reduces parameters before the dense layer, preventing overfitting.

---

## 4. Parameter Counting (Comptage de Paramètres)

You must know this for the exam!

### Conv Layer
$$Params = K \times ((F \times F \times C_{in}) + 1)$$
-   $K$: Number of filters.
-   $1$: Bias term.

### Dense Layer
$$Params = (N_{in} + 1) \times N_{out}$$

---

## 5. Pros & Cons

| Advantages | Disadvantages |
| :--- | :--- |
| **Spatial Hierarchy**: Learns low-level features (edges) to high-level (faces). | **Computation**: Very expensive to train (needs GPU). |
| **Efficient**: Far fewer parameters than MLP for image data. | **Data Hungry**: Needs massive datasets to generalize well. |
| **Invariance**: Robust to translation. | **Black Box**: Hard to interpret what exactly it "sees". |

---

## 6. Typical Pipeline

$$Input \rightarrow [Conv \rightarrow BatchNorm \rightarrow ReLU \rightarrow Pool] \times N \rightarrow Flatten/GAP \rightarrow Dense \rightarrow Softmax$$

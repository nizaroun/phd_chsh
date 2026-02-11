# 13 Neural Networks (Réseaux de Neurones) & Backpropagation

## 1. Core Definition (Définition)

A **Multi-Layer Perceptron (MLP)** (*Perceptron Multicouche*) is a feedforward artificial neural network that generates a set of outputs from a set of inputs. An MLP is characterized by several layers of input nodes connected as a directed graph between the input and output layers.

> [!NOTE] Architecture
> -   **Input Layer** (*Couche d'entrée*): Receives the raw signal ($x$).
> -   **Hidden Layers** (*Couches cachées*): Perform the computation.
> -   **Output Layer** (*Couche de sortie*): Makes the final prediction ($o$ or $\hat{y}$).

---

## 2. Forward Propagation (Propagation Avant)

The process of calculating the output from the input.

For a single neuron $j$:
1.  **Weighted Sum** (*Somme pondérée*):
    $$z_j = \sum_{i} (w_{ij} \cdot x_i) + b_j$$
2.  **Activation** (*Activation*):
    $$o_j = \sigma(z_j)$$

> [!TIP] Activation Functions
> $\sigma(z)$ introduces non-linearity (Sigmoid, ReLU, Tanh). See **16_Activation_Functions** for details.

---

## 3. Backpropagation (Rétropropagation)

The heart of training. We want to update weights ($w$) to minimize the **Error ($E$)** (Loss Function).

**Gradient Descent Rule**:
$$w_{new} = w_{old} - \eta \cdot \frac{\partial E}{\partial w}$$
-   $\eta$: Learning Rate (*Taux d'apprentissage*).

### The Chain Rule (Règle de la chaîne)
To find $\frac{\partial E}{\partial w}$, we use the chain rule:

$$\frac{\partial E}{\partial w} = \text{Delta}(\delta) \times \text{Input}$$

-   **Input**: Signal coming into the weight.
-   **Delta ($\delta$)**: "Blame" or error signal of the target neuron.

---

## 4. Calculating Delta ($\delta$)

### A. Output Layer ($\delta_k$)
We know the Target ($t_k$), so we can compute error directly.
$$\delta_k = (o_k - t_k) \times \sigma'(z_k)$$
*(Assuming MSE Cost + generic activation)*

> [!IMPORTANT] Target
> Only the output layer has a "Target" value to compare against.

### B. Hidden Layer ($\delta_j$)
We don't have a target. We sum the "blame" backpropagated from the Next Layer.
$$\delta_j = \left( \sum_{k} \delta_k \cdot w_{jk} \right) \times \sigma'(z_j)$$

> [!NOTE] Interpretation
> The error of a hidden neuron is the weighted sum of the errors of the neurons it connects to.

---

## 5. Summary Algorithm

1.  **Initialize** weights randomly.
2.  **Forward Pass**: Compute outputs $o$ for all neurons.
3.  **Calculate Error**: Compute Loss $E$.
4.  **Backward Pass**:
    -   Compute $\delta_k$ for Output Layer.
    -   Compute $\delta_j$ for Hidden Layers (propagating backwards).
5.  **Update Weights**: $w \leftarrow w - \eta \cdot \delta \cdot \text{input}$.
6.  **Repeat** until convergence.

---

## 6. Pros & Cons

| Advantages | Disadvantages |
| :--- | :--- |
| **Universal Approximator**: Can learn any function (given enough neurons). | **Black Box**: Hard to interpret weights. |
| **Non-Linear**: Handles complex, non-linear relationships. | **Data Hungry**: Requires a lot of data. |
| **Feature Learning**: Automatically learns features (no need for manual feature engineering). | **Computation**: Slow to train (CPU/GPU intensive). |
| | **Overfitting**: Prone to memorizing data matching (require Regularization/Dropout). |

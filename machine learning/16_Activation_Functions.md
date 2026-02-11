# 09 Activation Functions (Fonctions d'Activation)

## 1. Definition (Définition)

In **Neural Networks**, an **Activation Function** (*Fonction d'Activation*) defines the output of a neuron given an input or set of inputs.

> [!IMPORTANT] Purpose
> It introduces **non-linearity** (*non-linéarité*) into the network. Without non-linear activation functions, a Neural Network, no matter how deep, behaves exactly like a single-layer Linear Regression model.

$$y = Activation(\sum (w_i x_i) + b)$$

---

## 2. Sigmoid Function (Fonction Sigmoïde)

$$f(x) = \frac{1}{1 + e^{-x}}$$

-   **Range**: (0, 1)
-   **Use Case**: **Binary Classification** (output layer). Predicting probability.

> [!WARNING] Vanishing Gradient
> Sigmoid suffers from the **Vanishing Gradient Problem**: gradients become very small for large positive/negative inputs, halting learning in deep networks.

---

## 3. Tanh Function (Tangente Hyperbolique)

$$f(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$$

-   **Range**: (-1, 1)
-   **Use Case**: Hidden layers in simple networks.

> [!NOTE] Improvement
> Tanh is **zero-centered**, making optimization easier than Sigmoid, but it still finds the Vanishing Gradient problem.

---

## 4. ReLU (Rectified Linear Unit)

The most popular activation function for modern Deep Learning.

$$f(x) = \max(0, x)$$

-   **Range**: [0, $\infty$)
-   **Use Case**: <ins>Default choice</ins> for **Hidden Layers** (CNNs, MLPs).

> [!TIP] Pros
> -   **Computationally Efficient**: Just a simple comparison.
> -   **No Vanishing Gradient** (for positive inputs).

> [!WARNING] Cons
> **Dying ReLU Problem**: Neurons can "die" if they output 0 for all data (gradient becomes 0 forever).

---

## 5. Leaky ReLU

Variant of ReLU to fix the "Dying ReLU" problem.

$$f(x) = \max(\alpha x, x)$$
Usually $\alpha = 0.01$.

> [!NOTE] Fix
> Allows a small, non-zero gradient for negative inputs.

---

## 6. Softmax Function

$$f(x_i) = \frac{e^{x_i}}{\sum_{j} e^{x_j}}$$

-   **Range**: (0, 1), sum of all outputs is 1.

> [!TIP] Use Case
> **Multi-Class Classification** (output layer). It converts raw scores (logits) into a probability distribution.

---

## 7. Short Summary: When to use which?

| Function | Layer | Task |
| :--- | :--- | :--- |
| **Sigmoid** | Output | **Binary Classification** (Yes/No) |
| **Softmax** | Output | **Multi-Class Classification** (Cat/Dog/Bird) |
| **Linear** | Output | **Regression** (Predicting House Price) |
| **ReLU** | Hidden | **Convolutional Neural Networks (CNN)**, General Deep Learning |
| **Tanh** | Hidden | **Recurrent Neural Networks (RNN)** |

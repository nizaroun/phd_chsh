# 🧠 Convolutional Neural Networks (CNN) --- PhD Cheat Sheet

## 1. What is a CNN?

A **Convolutional Neural Network (CNN)** is a neural network designed to
process **grid-structured data** (images, signals) using: - Local
connectivity - Weight sharing - Hierarchical feature extraction

------------------------------------------------------------------------

## 2. Input Representation

An image is represented as a 3D tensor:

$$
X \in \mathbb{R}^{H \times W \times C}
$$

Where: - $$H$$: height - $$W$$: width - $$C$$: number of channels (1 =
grayscale, 3 = RGB)

------------------------------------------------------------------------

## 3. Convolution Layer

### 3.1 Filter / Kernel

A convolution filter has size:

$$
F \times F \times C_{in}
$$

-   Each filter produces **one feature map**
-   Number of output channels = number of filters

------------------------------------------------------------------------

### 3.2 Convolution Operation

At each spatial position:

$$
y = \sum_{c=1}^{C_{in}} W_c * X_c + b
$$

------------------------------------------------------------------------

### 3.3 Output Size Formula

For height and width:

$$
H_{out} = \frac{H_{in} - F + 2P}{S} + 1
$$

Where: - $$F$$: filter size - $$P$$: padding - $$S$$: stride

Output tensor:

$$
H_{out} \times W_{out} \times C_{out}
$$

------------------------------------------------------------------------

### 3.4 Padding Types

-   **Valid**: $$P = 0$$
-   **Same**: output size equals input size

------------------------------------------------------------------------

## 4. Activation Function (ReLU)

### Definition

$$
\text{ReLU}(x) = \max(0, x)
$$

-   Introduces non-linearity
-   Prevents vanishing gradients
-   Does **not** change tensor size

------------------------------------------------------------------------

## 5. Pooling Layer

### Purpose

-   Reduces spatial dimensions
-   Improves translation invariance
-   Reduces overfitting

------------------------------------------------------------------------

### Max Pooling

For pool size $$K \times K$$ and stride $$S$$:

$$
H_{out} = \frac{H_{in}}{S}
$$

-   Channels unchanged
-   No trainable parameters

------------------------------------------------------------------------

## 6. Flatten Layer

Transforms a 3D tensor into 1D:

$$
H \times W \times C \rightarrow H \cdot W \cdot C
$$

------------------------------------------------------------------------

## 7. Fully Connected (Dense) Layer

### Operation

$$
y = Wx + b
$$

### Parameters

$$
(\text{inputs} + 1) \times \text{outputs}
$$

------------------------------------------------------------------------

## 8. Softmax (Output Layer)

Used for multi-class classification:

$$
\text{Softmax}(z_i) = \frac{e^{z_i}}{\sum_{j} e^{z_j}}
$$

Properties: - Outputs probabilities - Sum equals 1

------------------------------------------------------------------------

## 9. Trainable Parameters (EXAM CRITICAL)

### Convolution Layer

$$
(F \times F \times C_{in} + 1) \times C_{out}
$$

------------------------------------------------------------------------

### Pooling Layer

$$
0
$$

------------------------------------------------------------------------

### Dense Layer

$$
(\text{inputs} + 1) \times \text{outputs}
$$

------------------------------------------------------------------------

## 10. CNN vs MLP

  CNN                  MLP
  -------------------- -----------------
  Local connectivity   Fully connected
  Weight sharing       No sharing
  Few parameters       Many parameters
  Spatial awareness    No spatial info

------------------------------------------------------------------------

## 11. Why CNNs Work Well for Images

-   Exploit spatial locality
-   Learn hierarchical features
-   Translation invariant
-   Parameter efficient

------------------------------------------------------------------------

## 12. Overfitting in CNNs

### Solutions:

-   Dropout
-   Data augmentation
-   Regularization (L2)
-   Early stopping

------------------------------------------------------------------------

## 13. Typical CNN Pipeline

$$
\text{Input} \rightarrow \text{Conv} \rightarrow \text{ReLU} \rightarrow \text{Pool}
\rightarrow \text{Conv} \rightarrow \text{ReLU} \rightarrow \text{Flatten}
\rightarrow \text{Dense} \rightarrow \text{Softmax}
$$

------------------------------------------------------------------------

## 14. Common Exam Traps

-   Output depth = number of filters (NOT input channels)
-   Input channels appear in **parameter count**, not output shape
-   Pooling has NO parameters
-   ReLU does not change dimensions

------------------------------------------------------------------------

## 15. Key Sentence (Oral Exam Gold)

> In CNNs, the input channel dimension is consumed inside each filter,
> and the output depth is equal to the number of filters.

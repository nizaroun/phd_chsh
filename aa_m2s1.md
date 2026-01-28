
# Recommender Systems

## Rating Matrix
$$
R \in \mathbb{R}^{n_u \times n_i}
$$

## RMSE
$$
RMSE = \sqrt{\frac{1}{|R|} \sum_{(u,i)} (r_{ui} - \hat r_{ui})^2}
$$

---

# Regularisation

## L2 (Ridge)
$$
J(\theta) = \frac{1}{2m}\sum (h_\theta(x)-y)^2 + \frac{\lambda}{2m}\sum \theta_j^2
$$

## L1 (Lasso)
$$
J(\theta) = \frac{1}{2m}\sum (h_\theta(x)-y)^2 + \lambda\sum |\theta_j|
$$

---

# Support Vector Machines

## Decision Function
$$
f(x)=w^Tx+b
$$

## Soft Margin
$$
\min \frac{1}{2}\|w\|^2 + C\sum \xi_i
$$

---

# Ensemble Learning

## AdaBoost
$$
G(x)=\text{sign}\left(\sum_m \alpha_m G_m(x)\right)
$$

---

# Deep Learning

## Neuron
$$
z=w^Tx+b
$$

$$
\hat y=f(z)
$$

---

# CNN

## Convolution
$$
(f*h)(i,j)=\sum f(i-m,j-n)h(m,n)
$$

---

# Reinforcement Learning

## Bellman Equation
$$
Q^*(s,a)=\mathbb{E}[r+\gamma\max_{a'}Q^*(s',a')]
$$

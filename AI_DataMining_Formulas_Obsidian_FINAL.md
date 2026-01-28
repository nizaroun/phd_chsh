
# Cours #1 — Introduction au Machine Learning

## Notations générales
$$
X = (x_1, x_2, \dots, x_n)
$$

$$
y \in \mathcal{Y}
$$

$$
\mathcal{D} = \{(x^{(i)}, y^{(i)})\}_{i=1}^{m}
$$

---

# Cours #2 — Régression Linéaire

## Modèle linéaire simple
$$
f(x) = ax + b
$$

## Modèle linéaire multiple
$$
f(x) = \mathbf{w}^T \mathbf{x} + b
$$

## Erreur quadratique
$$
e^{(i)} = f(x^{(i)}) - y^{(i)}
$$

## Fonction coût : Mean Squared Error (MSE)
$$
J(\mathbf{w}) = \frac{1}{2m} \sum_{i=1}^{m} (f(x^{(i)}) - y^{(i)})^2
$$

## Forme vectorielle
$$
J(\mathbf{w}) = \frac{1}{2m} \|X\mathbf{w} - \mathbf{y}\|^2
$$

---

# Cours #3 — Régression Logistique

## Fonction sigmoïde
$$
\sigma(z) = \frac{1}{1 + e^{-z}}
$$

## Hypothèse
$$
h_\theta(x) = \sigma(\theta^T x)
$$

## Fonction coût (Log-loss)
$$
J(\theta) = -\frac{1}{m}\sum_{i=1}^{m}
\left[y^{(i)}\log(h_\theta(x^{(i)})) + (1-y^{(i)})\log(1-h_\theta(x^{(i)}))\right]
$$

## Règle de décision
$$
\hat{y} =
\begin{cases}
1 & \text{si } h_\theta(x) \ge 0.5 \\
0 & \text{sinon}
\end{cases}
$$

---

# Cours #4 — Arbres de Décision

## Entropie
$$
H(S) = -\sum_{i=1}^{c} p_i \log_2(p_i)
$$

## Entropie conditionnelle
$$
H(S|A) = \sum_{v \in Values(A)} \frac{|S_v|}{|S|} H(S_v)
$$

## Gain d'information
$$
IG(S,A) = H(S) - H(S|A)
$$

## Indice de Gini
$$
Gini(S) = 1 - \sum_{i=1}^{c} p_i^2
$$

---

# Cours #5 — Naïve Bayes

## Théorème de Bayes
$$
P(C|X) = \frac{P(X|C)P(C)}{P(X)}
$$

## Hypothèse d’indépendance conditionnelle
$$
P(X|C) = \prod_{i=1}^{n} P(x_i|C)
$$

## Règle MAP
$$
\hat{C} = \arg\max_C P(C)\prod_{i=1}^{n} P(x_i|C)
$$

## Naïve Bayes Gaussien
$$
P(x_i|C) =
\frac{1}{\sqrt{2\pi\sigma_C^2}}
\exp\left(-\frac{(x_i-\mu_C)^2}{2\sigma_C^2}\right)
$$

---

# Cours #6 — K-Nearest Neighbors (KNN)

## Distance euclidienne
$$
d(x,y) = \sqrt{\sum_{i=1}^{n}(x_i-y_i)^2}
$$

## Distance Manhattan
$$
d(x,y) = \sum_{i=1}^{n}|x_i-y_i|
$$

## Distance Minkowski
$$
d(x,y) = \left(\sum_{i=1}^{n}|x_i-y_i|^p\right)^{1/p}
$$

## Similarité cosinus
$$
\cos(\theta) = \frac{x \cdot y}{\|x\|\|y\|}
$$

## Vote majoritaire
$$
\hat{y} = \arg\max_c \sum_{i \in N_k(x)} \mathbb{1}(y_i = c)
$$

---

# Cours #7 — Clustering

## Fonction objectif K-means
$$
J = \sum_{k=1}^{K} \sum_{x_i \in C_k} \|x_i - \mu_k\|^2
$$

## Mise à jour des centroïdes
$$
\mu_k = \frac{1}{|C_k|}\sum_{x_i \in C_k} x_i
$$

## Liaison simple (Single-link)
$$
d(C_i,C_j) = \min_{x \in C_i, y \in C_j} d(x,y)
$$

## Liaison complète (Complete-link)
$$
d(C_i,C_j) = \max_{x \in C_i, y \in C_j} d(x,y)
$$

## Liaison moyenne (Average-link)
$$
d(C_i,C_j) = \frac{1}{|C_i||C_j|}
\sum_{x \in C_i}\sum_{y \in C_j} d(x,y)
$$

---

# Évaluation des Modèles (Classification)

## Matrice de confusion
$$
\begin{array}{c|cc}
 & \text{Prédit +} & \text{Prédit -} \\ \hline
\text{Réel +} & TP & FN \\
\text{Réel -} & FP & TN
\end{array}
$$

## Accuracy
$$
Accuracy = \frac{TP + TN}{TP + TN + FP + FN}
$$

## Precision
$$
Precision = \frac{TP}{TP + FP}
$$

## Recall (Sensitivity)
$$
Recall = \frac{TP}{TP + FN}
$$

## Specificity
$$
Specificity = \frac{TN}{TN + FP}
$$

## F1-score
$$
F1 = 2 \cdot \frac{Precision \cdot Recall}{Precision + Recall}
$$

## Taux d'erreur
$$
Error = 1 - Accuracy
$$

---

# Évaluation des Modèles (Régression)

## Mean Absolute Error (MAE)
$$
MAE = \frac{1}{m} \sum_{i=1}^{m} |y^{(i)} - \hat{y}^{(i)}|
$$

## Mean Squared Error (MSE)
$$
MSE = \frac{1}{m} \sum_{i=1}^{m} (y^{(i)} - \hat{y}^{(i)})^2
$$

## Root Mean Squared Error (RMSE)
$$
RMSE = \sqrt{MSE}
$$

## Coefficient de détermination
$$
R^2 = 1 - \frac{\sum (y_i - \hat{y}_i)^2}{\sum (y_i - \bar{y})^2}
$$

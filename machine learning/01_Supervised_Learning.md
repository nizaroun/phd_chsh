# 01 Supervised Classification Overview (Vue d'ensemble de la classification supervisée)

## 1. Core Definition (Définition)

> [!NOTE] Definition
> **Supervised Classification** (*Classification Supervisée*) is a machine learning task where the goal is to learn a mapping function (*fonction de décision*) $f$ from input variables $X$ to discrete output variables $Y$.

$$f : \mathcal{X} \rightarrow \mathcal{Y}$$

- **Input ($X$)**: Features (*Variables explicatives*, *Caractéristiques*)
- **Output ($Y$)**: Class labels (*Étiquettes*, *Classes*)

### Types of Classification
-   **Binary** (*Binaire*): $|Y| = 2$ (e.g., Spam vs Ham).
-   **Multi-class** (*Multi-classe*): $|Y| > 2$ (e.g., Cat vs Dog vs Bird).

---

## 2. Learning Process (Processus d'apprentissage)

1.  **Training** (*Entraînement*): The algorithm learns the parameters of the model using the training data.
2.  **Validation**: Hyperparameters are tuned using a validation set to prevent overfitting (*sur-apprentissage*).
3.  **Testing** (*Test*): The final model is evaluated on unseen data to estimate its generalization error (*erreur de généralisation*).

---

## 3. Evaluation Metrics (Mesures d'évaluation)

The **Confusion Matrix** (*Matrice de Confusion*) is the foundation for most metrics in binary classification.

|                    | **Predicted Positive** ($\hat{y}=1$) | **Predicted Negative** ($\hat{y}=0$) |
| :----------------- | :------------------------------: | :------------------------------: |
| **Actual Positive** ($y=1$) |     **TP** (True Positive / *Vrai Positif*)      |      **FN** (False Negative / *Faux Négatif*)       |
| **Actual Negative** ($y=0$) |     **FP** (False Positive / *Faux Positif*)      |      **TN** (True Negative / *Vrai Négatif*)       |

### Key Metrics

#### A. Accuracy (*Exactitude / Taux de reconnaissance*)
The ratio of correctly predicted observations to the total observations.
$$Accuracy = \frac{TP + TN}{TP + TN + FP + FN}$$

**Error Rate** (*Taux d'erreur*):
$$Error = 1 - Accuracy$$

> [!WARNING] When to avoid
> Avoid **Accuracy** on **imbalanced datasets** (*données déséquilibrées*).

#### B. Precision (*Précision*)
The ratio of correctly predicted positive observations to the total predicted positives.
$$Precision = \frac{TP}{TP + FP}$$
> [!TIP] Goal
> Minimize **False Positives** (e.g., Spam detection).

#### C. Recall / Sensitivity (*Rappel / Sensibilité*)
The ratio of correctly predicted positive observations to the all observations in actual class.
$$Recall = \frac{TP}{TP + FN}$$
> [!TIP] Goal
> Minimize **False Negatives** (e.g., Cancer detection).

#### D. F1-Score (*F-Mesure*)
The weighted average of Precision and Recall.
$$F_1 = 2 \times \frac{Precision \times Recall}{Precision + Recall}$$

#### E. Specificity (*Spécificité*)
The ability of the classifier to find all the negative samples.
$$Specificity = \frac{TN}{TN + FP}$$

---

## 4. Exam Cheat Sheet (Résumé pour l'examen)

| Goal (*Objectif*) | Metric to Choose (*Métrique*) |
| :--- | :--- |
| **Balanced Data** (*Données équilibrées*) | **Accuracy** |
| **Minimize False Positives** (*Minimiser Faux Positifs*) | **Precision** |
| **Minimize False Negatives** (*Minimiser Faux Négatifs*) | **Recall** |
| **Imbalanced Data** (*Données déséquilibrées*) | **F1-Score** |

---

## 5. Validation Strategies (Stratégies de validation)

1.  **Hold-Out**: Split data once (e.g., 80% train, 20% test). Fast but high variance.
2.  **k-Fold Cross-Validation** (*Validation croisée*): Split data into $k$ subsets. Train on $k-1$, test on 1. Repeat $k$ times. Average the results. Reduces variance.
3.  **Leave-One-Out (LOOCV)**: $k = N$. Extreme case of k-fold. Very computationally expensive.

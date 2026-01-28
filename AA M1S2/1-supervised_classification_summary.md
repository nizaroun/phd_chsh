# Supervised Classification – Summary (Résumé)

## Core Definition (Définition)
Supervised classification (**classification supervisée**) learns a decision function:

$f̂ : X → Y$

using labeled data (**données étiquetées**).

---

## Training Data (Données d’apprentissage)
- Dataset:
$$
X = {(x_i, y_i) | i = 1..N}
$$
- $x_i$: feature vector (**vecteur de caractéristiques**)
- $y_i$: class label (**étiquette de classe**)
- $Y$: discrete label set (**ensemble discret**)

### Types of classification
- $|Y| = 1$ → One-class (**mono-classe**)
- $|Y| = 2$ → Binary (**binaire**)
- $|Y| > 2$ → Multi-class (**multi-classe**)

---

## Learning Process (Processus d’apprentissage)
1. **Training (Entraînement)** – learn model parameters  
2. **Validation (Validation / tuning)** – choose hyperparameters  
3. **Testing (Test)** – evaluate generalization  

---

## Evaluation Metrics (Mesures d’évaluation)

### Accuracy / Recognition Rate  
$$
Accuracy = \frac{1}{N} Σ L(y_i, f̂(x_i))
$$


### Confusion Matrix (Matrice de confusion)
- TP / CP: True Positive (**Vrai Positif**)
- TN / CN: True Negative (**Vrai Négatif**)
- FP: False Positive (**Faux Positif**)
- FN: False Negative (**Faux Négatif**)

### Error Rate (Taux d’erreur)
$$
Error = 100 − Accuracy
$$

###  Accuracy
$$
Accuracy = \frac{CP+CN}{CP + FP + CN + FN}
$$
### Precision
$$
Precision = \frac{CP}{CP + FP}
$$

### Recall / Sensitivity (Rappel / Sensibilité)
$$
Recall = \frac{CP}{CP + FN}
$$

### Specificity (Spécificité)
$$
Specificity = \frac{CN}{CN + FP}
$$

### F-score (F-mesure)


$$
F =2 × \frac{(Precision × Recall)}{(Precision + Recall)}
$$

---

## Validation Strategies (Stratégies de validation)
- **Hold-Out** – single train/test split
- **k-Fold Cross-Validation (validation croisée)**  
- **Leave-One-Out** – special case where  $k = N$

---

## Key Takeaway (À retenir)
> Supervised classification relies on high-quality labeled data, proper validation, and confusion-based metrics to ensure good generalization.


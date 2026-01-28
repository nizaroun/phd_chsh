# Régression Logistique – Résumé (Cours #3)

## Définition
La **régression logistique** (*logistic regression*) est un algorithme d’**apprentissage supervisé** (*supervised learning*) utilisé principalement pour la **classification binaire** (*binary classification*).

Elle prédit une **probabilité** (*probability*) comprise entre 0 et 1, puis applique un **seuil de décision** (*decision threshold*) pour attribuer une classe.

---

## Classification vs Régression
- **Classification** (*classification*) : variable cible **discrète** (*discrete target*)
- **Régression** (*regression*) : variable cible **continue** (*continuous target*)

La régression logistique est un **modèle de classification**, malgré son nom.

---

## Modèle linéaire (*Linear model*)

$$z = \theta^T x$$

- $(x$) : variables explicatives (*features*)
- $(\theta$) : poids du modèle (*weights*)

---

## Fonction sigmoïde (*Sigmoid function*)

La fonction sigmoïde transforme une valeur réelle en probabilité :

$$\sigma(z) = \frac{1}{1 + e^{-z}}$$

Propriétés :
- $(0 < \sigma(z) < 1$)
- $(\sigma(z) \ge 0.5 \Rightarrow y = 1$)
- $(\sigma(z) < 0.5 \Rightarrow y = 0$)

---

## Fonction de décision (*Decision boundary*)

- Seuil classique : **0.5**
- Peut être :
  - **linéaire** (*linear decision boundary*)
  - **non linéaire** (*non-linear decision boundary*)

---

## Fonction de perte (*Loss function*)

La régression logistique utilise la **log-loss** (*logarithmic loss / cross-entropy*) :


$$J(\theta) = -\frac{1}{m} \sum_{i=1}^{m}
\Big[
y^{(i)} \log(h_\theta(x^{(i)})) +
(1 - y^{(i)}) \log(1 - h_\theta(x^{(i)}))
\Big]$$

- Fonction **convexe** (*convex*)
- Pénalise fortement les mauvaises prédictions

---

## Optimisation – Descente de gradient (*Gradient Descent*)

Mise à jour des paramètres :


$$\theta := \theta - \alpha \nabla J(\theta)$$


- $(\alpha)$ : taux d’apprentissage (*learning rate*)
- Même forme que pour la régression linéaire

---

## Apprentissage multi-classes (*Multiclass classification*)

La régression logistique est **binaire par nature**, mais peut être étendue avec :

### One-vs-Rest (OvR)
- $(N$) classes → $(N$) classifieurs binaires
- Classe finale = probabilité maximale

### One-vs-One (OvO)
- $(N(N-1)/2$) classifieurs
- Vote majoritaire

---

## Classification multi-label (*Multi-label classification*)

- Un exemple peut appartenir à **plusieurs classes**
- Différent du multi-classe
- Nécessite des versions spécialisées des algorithmes

---

## Données déséquilibrées (*Imbalanced data*)

Problème :
- Classe majoritaire dominante
- Mauvaises performances sur la classe minoritaire

Solutions :
- **Sous-échantillonnage** (*undersampling*)
- **Sur-échantillonnage** (*oversampling*)
- **SMOTE**
- **Algorithmes sensibles au coût** (*cost-sensitive learning*)

---

## Métriques d’évaluation (*Evaluation metrics*)

- **Accuracy** (*exactitude*)
- **Precision** (*précision*)
- **Recall / Sensitivity** (*rappel / sensibilité*)
- **Specificity** (*spécificité*)
- **F1-score**
- **ROC Curve & AUC**

---

## Régularisation (*Regularization*)

Objectif : éviter le **sur-apprentissage** (*overfitting*)

### L1 – Lasso

$$\lambda \sum |\theta_j|$$

- Favorise la **sélection de variables**

### L2 – Ridge

$$\lambda \sum \theta_j^2$$
- Réduit les poids sans les annuler

---

## Avantages (*Advantages*)

- Simple et interprétable
- Donne des probabilités
- Rapide à entraîner
- Très utilisé en pratique

---

## Inconvénients (*Disadvantages*)

- Hypothèse de frontière linéaire
- Sensible aux valeurs aberrantes (*outliers*)
- Performances limitées sur données complexes

---

## À retenir (*Key takeaway*)

> La régression logistique est un algorithme fondamental de classification binaire, basé sur la fonction sigmoïde et optimisé par descente de gradient, extensible au multi-classe et robuste grâce à la régularisation.

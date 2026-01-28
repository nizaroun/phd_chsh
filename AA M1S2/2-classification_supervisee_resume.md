# Classification supervisée – Résumé

## Définition
La **classification supervisée** (*supervised classification*) consiste à apprendre une **fonction de décision** (*decision function*) :

$$
f̂ : X → Y
$$

à partir de **données étiquetées** (*labeled data*).

---

## Données d’apprentissage (*Training data*)

- Ensemble de données :
$$
X = {(x_i, y_i) | i = 1..N}
$$

- $x_i$ : vecteur de caractéristiques (*feature vector*)
- $y_i$ : étiquette de classe (*class label*)
- $Y$ : ensemble des classes discret (*discrete label set*)
- $N$ : nombre d’exemples (*number of samples*)

---

## Types de classification (*Classification types*)

- $|Y| = 1$ → **Classification mono-classe** (*one-class classification*)
- $|Y| = 2$ → **Classification binaire** (*binary classification*)
- $|Y| > 2$ → **Classification multi-classe** (*multi-class classification*)

---

## Processus d’apprentissage (*Learning process*)

1. **Entraînement** (*training*)  
   → apprentissage des paramètres du modèle  

2. **Validation / Tuning** (*validation / hyperparameter tuning*)  
   → choix des meilleurs paramètres  

3. **Test / Évaluation** (*testing / evaluation*)  
   → estimation de la capacité de généralisation (*generalization ability*)

---

## Mesures d’évaluation (*Evaluation metrics*)

### Taux de reconnaissance / Précision (*Accuracy*)

$$
Accuracy = (1/N) Σ L(y_i, f̂(x_i))
$$

où la **fonction de perte** (*loss function*) est :

$$
L = 1 si y_i = f̂(x_i)
L = 0 sinon
$$

---

### Matrice de confusion (*Confusion matrix*)

- **CP** : Vrai Positif (*True Positive*)
- **CN** : Vrai Négatif (*True Negative*)
- **FP** : Faux Positif (*False Positive*)
- **FN** : Faux Négatif (*False Negative*)

---

### Taux d’erreur (*Error rate*)

$$
Taux d’erreur = 100 − Accuracy
$$

---

### Sensibilité / Rappel (*Sensitivity / Recall*)

$$
Sv = \frac{CP}{CP + FN}
$$

---

### Spécificité (*Specificity*)


$$
Sp = \frac{CN}{CN + FP}
$$

---

### F-mesure / Moyenne harmonique (*F-score / Harmonic mean*)


$$
F =2 × \frac{(Sv × Sp)}{(Sv + Sp)}
$$

---

## Méthodes de validation (*Validation strategies*)

- **Hold-Out** (*simple train/test split*)
- **Validation croisée k-plis** (*k-fold cross-validation*)
- **Leave-One-Out** (*leave-one-out cross-validation*, $k = N$ )

---

## À retenir (Key takeaway)

> La classification supervisée repose sur des **données étiquetées de qualité**, des **mesures d’évaluation adaptées** et des **méthodes de validation rigoureuses** afin d’assurer une bonne **généralisation** (*generalization*).


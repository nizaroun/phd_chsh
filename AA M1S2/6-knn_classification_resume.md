# Classification k-plus proches voisins (k-NN) – Résumé (Cours #6)

## Définition
La **classification k-plus proches voisins** (*k-Nearest Neighbors, k-NN*) est un algorithme d’**apprentissage supervisé** (*supervised learning*) utilisé pour la **classification** (*classification*) et la **régression** (*regression*).

C’est un algorithme :
- **non paramétrique** (*non-parametric*)
- à **apprentissage paresseux** (*lazy learning*)

---

## Principe général (*General principle*)

Un nouvel exemple est classé selon la **majorité des classes** (*majority vote*) parmi ses **k voisins les plus proches** (*k nearest neighbors*) dans l’espace des attributs.

> « Dis-moi qui sont tes voisins, je te dirai qui tu es »

---

## Caractéristiques principales (*Key characteristics*)

- Aucun modèle explicite n’est appris (*no explicit model*)
- Toutes les données sont stockées (*instance-based learning*)
- L’apprentissage est rapide
- La prédiction est coûteuse (*expensive at prediction time*)

---

## Algorithme k-NN (*k-NN algorithm steps*)

1. Diviser les données en **entraînement** (*training*) et **test** (*test*)
2. Choisir le nombre de voisins **k**
3. Choisir une **mesure de distance** (*distance metric*)
4. Calculer la distance entre le point test et tous les points d’entraînement
5. Sélectionner les **k plus proches voisins**
6. Attribuer la classe par **vote majoritaire** (*majority voting*)

---

## Mesures de distance (*Distance measures*)

### Distance euclidienne (*Euclidean distance – L2 norm*)

$$d(p,q) = \sqrt{\sum_{i=1}^{n} (p_i - q_i)^2}$$

Utilisée surtout pour les **données numériques** (*numerical data*).

---

### Autres distances courantes (*Other distance metrics*)

- **Distance de Manhattan** (*Manhattan / L1 distance*)
- **Distance de Minkowski** (*Minkowski distance*)
- **Distance de Hamming** (*Hamming distance*) – données binaires
- **Distance cosinus** (*Cosine distance*) – texte, documents
- **Distance de Jaccard** (*Jaccard distance*)

---

## Choix du paramètre k (*Choosing k*)

- Petit k → sensible au bruit (*noise sensitive*, sur-apprentissage)
- Grand k → frontière trop lisse (*underfitting*)
- Valeur courante : **k = 5**
- k optimal trouvé par **validation croisée** (*cross-validation*)

---

## Facteurs influençant la performance (*Performance factors*)

1. La **distance** utilisée (*distance metric*)
2. La **règle de décision** (*decision rule*)
3. Le **nombre de voisins k** (*number of neighbors*)

---

## Avantages (*Advantages*)

- Simple à comprendre et implémenter
- Pas d’hypothèse sur la distribution des données
- Efficace avec beaucoup de données
- Applicable aux données non linéaires

---

## Inconvénients (*Disadvantages*)

- Coût mémoire élevé
- Prédiction lente
- Sensible à la **malédiction de la dimension** (*curse of dimensionality*)
- Sensible au choix de k
- Sensible au bruit

---

## Applications (*Applications*)

- Reconnaissance d’images (*image recognition*)
- Reconnaissance de l’écriture (*handwriting recognition*)
- Finance (scoring crédit)
- Santé (expression génétique)
- Analyse de similarité (*similarity search*)

---

## À retenir (*Key takeaway*)

> k-NN est un algorithme simple et intuitif basé sur la similarité, efficace pour des jeux de données de taille modérée, mais coûteux en calcul et sensible à la dimensionnalité.

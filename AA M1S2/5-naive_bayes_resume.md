# Classification Naïve Bayes – Résumé (Cours #5)

## Définition
La **classification Naïve Bayes** (*Naive Bayes classification*) est un algorithme d’**apprentissage supervisé** (*supervised learning*) basé sur le **théorème de Bayes** (*Bayes’ theorem*).  
C’est un **classifieur probabiliste** (*probabilistic classifier*) qui repose sur une hypothèse forte d’**indépendance conditionnelle des attributs** (*conditional independence assumption*).

---

## Théorème de Bayes (*Bayes’ theorem*)


$$P(C|X) = \frac{P(X|C) P(C)}{P(X)}$$

- $(P(C|X)$) : probabilité a posteriori (*posterior probability*)
- $(P(C)$) : probabilité a priori (*prior probability*)
- $(P(X|C)$) : vraisemblance (*likelihood*)
- $(P(X)$) : probabilité marginale (*marginal probability*)

---

## Hypothèse d’indépendance conditionnelle  
(*Conditional independence assumption*)


$$P(X|C) = \prod_{i=1}^{n} P(x_i|C)$$


Les attributs sont supposés **indépendants entre eux** sachant la classe.

---

## Règle de décision MAP  
(*Maximum A Posteriori rule*)

$$\hat{y} = \arg\max_{c \in C} P(c) \prod_{i=1}^{n} P(x_i|c)$$


On choisit la classe ayant la **probabilité a posteriori maximale**.

---

## Types de classifieurs Naïve Bayes  
(*Types of Naive Bayes classifiers*)

- **Multinomial Naïve Bayes**  
  → données de comptage (*word frequencies*), NLP

- **Bernoulli Naïve Bayes**  
  → données binaires (*binary features*)

- **Gaussian Naïve Bayes**  
  → variables continues supposées normales (*normal distribution*)

---

## Problème de fréquence nulle  
(*Zero-frequency problem*)

Si une valeur n’apparaît jamais dans l’ensemble d’apprentissage :

$$P(x_i|C) = 0$$

➡️ Toute la probabilité devient nulle.

---

## Lissage de Laplace  
(*Laplace smoothing*)

Permet d’éviter les probabilités nulles :


$$\hat{\theta}_i = \frac{x_i + \alpha}{N + \alpha d}$$

- $\alpha$ : paramètre de lissage (*smoothing parameter*), souvent 1  
- $(d$) : nombre de valeurs possibles (*number of categories*)

---

## Prédicteurs numériques  
(*Numerical predictors*)

Deux approches :
- **Discrétisation / binning** (*binning*)
- Hypothèse de **distribution normale** (*Gaussian assumption*) :

$$f(x) = \frac{1}{\sqrt{2\pi}\sigma} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$$


---

## Applications (*Applications*)

- Filtrage de spam (*spam filtering*)
- Classification de texte (*text classification*)
- Analyse de sentiment (*sentiment analysis*)
- Détection de fraude (*fraud detection*)
- Diagnostic médical (*medical diagnosis*)
- Prédiction météo (*weather prediction*)

---

## Avantages (*Advantages*)

- Simple et rapide
- Peu de données nécessaires
- Très scalable
- Fonctionne bien en haute dimension
- Supporte multi-classe

---

## Inconvénients (*Disadvantages*)

- Hypothèse d’indépendance irréaliste
- Sensible aux attributs dépendants
- Ignore l’ordre des mots (NLP)
- Problème de fréquence nulle sans lissage

---

## À retenir (*Key takeaway*)

> Naïve Bayes est un classifieur probabiliste simple et efficace, particulièrement adapté aux données textuelles, malgré son hypothèse d’indépendance souvent irréaliste.

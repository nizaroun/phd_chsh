# Régression linéaire – Résumé (Cours #2)

## Définition
La **régression linéaire** (*linear regression*) est une méthode d’**apprentissage supervisé** (*supervised learning*) utilisée pour prédire une **variable continue** (*continuous target*).

---

## Les 4 étapes de l’apprentissage supervisé (*Supervised learning steps*)

1. **Dataset** (*dataset*):  
   $$
   (x, y)
   $$
   - $x$ : features (*independent variables*)
   - $y$ : target (*dependent variable*)

2. **Modèle** (*model*):  
   → fonction mathématique à apprendre (*function to learn*)

3. **Fonction coût** (*cost function*):  
   → mesure l’erreur (*error*) entre prédictions et valeurs réelles

4. **Algorithme d’apprentissage** (*learning algorithm*):  
   → minimise la fonction coût

---

## Régression linéaire simple (*Simple linear regression*)

### Dataset
- $m$ exemples (*samples*)
- $n = 1$ feature

Exemple :  
> Prix d’un appartement (*apartment price*) en fonction de sa surface (*surface area*)

---

## Modèle linéaire (*Linear model*)


$$f(x) = a x + b$$


- $a$ : pente (*slope / weight*)
- $b$ : biais (*bias / intercept*)

---

## Fonction coût : Erreur Quadratique Moyenne  
(*Mean Squared Error – MSE*)


$$J(a,b) = \frac{1}{2m} \sum_{i=1}^{m} (f(x^{(i)}) - y^{(i)})^2$$


---

## Algorithme d’apprentissage (*Learning algorithm*)

### Descente de gradient (*Gradient Descent*)


$$a := a - \alpha \frac{\partial J}{\partial a}$$

$$b := b - \alpha \frac{\partial J}{\partial b}$$


- $α$ : taux d’apprentissage (*learning rate*)

---

## Forme matricielle (*Matrix form*)

### Matrice des données

$$X \in \mathbb{R}^{m \times (n+1)}$$


### Vecteurs

$$\theta =
\begin{pmatrix}
a \\
b
\end{pmatrix}$$

$$F = X \theta$$

---

## Fonction coût matricielle (*Vectorized cost function*)


$$J(\theta) = \frac{1}{2m} (X\theta - Y)^T (X\theta - Y)$$


---

## Gradient matriciel (*Gradient vector*)


$$\nabla J(\theta) = \frac{1}{m} X^T (X\theta - Y)$$


---

## Mise à jour des paramètres (*Update rule*)


$$\theta := \theta - \alpha \nabla J(\theta)$$


---

## À retenir (*Key takeaway*)

> La régression linéaire apprend une relation linéaire entre les données en minimisant l’erreur quadratique moyenne grâce à la descente de gradient, avec une implémentation efficace en forme matricielle.

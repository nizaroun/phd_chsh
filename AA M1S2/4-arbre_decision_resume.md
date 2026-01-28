# Arbre de décision – Résumé (Cours #4)

## Définition
Un **arbre de décision** (*decision tree*) est un algorithme d’**apprentissage supervisé** (*supervised learning*) utilisé pour la **classification** (*classification*) et la **régression** (*regression*).  
Il représente les décisions sous forme d’une **structure arborescente** (*tree structure*).

---

## Structure d’un arbre de décision (*Decision tree structure*)

- **Nœud racine** (*root node*)  
- **Nœud de décision** (*decision node*)  
- **Branche** (*branch*)  
- **Feuille** (*leaf node*)  
- **Sous-arbre** (*subtree*)  
- **Élagage** (*pruning*)

---

## Fonctionnement de l’algorithme (*How it works*)

1. Démarrer avec le **dataset S** (*training set*)
2. Sélectionner le **meilleur attribut** (*best attribute*)
3. Diviser les données (*splitting*)
4. Créer des nœuds de décision
5. Répéter jusqu’aux feuilles

---

## Mesures de sélection d’attributs  
(*Attribute Selection Measures – ASM*)

### Entropie (*Entropy*)
$$
Entropy(S) = − Σ pᵢ log₂(pᵢ)
$$

---

### Gain d’information (*Information Gain*)
$$
IG(S, A) = Entropy(S) − Σ (|Sᵥ| / |S|) Entropy(Sᵥ)
$$

---

### Indice de Gini (*Gini Index*)
$$
Gini = 1 − Σ pᵢ²
$$

---

### Gain Ratio (*Gain ratio*)
→ Correction du biais du gain d’information

---

### Réduction de variance (*Reduction in variance*)
→ Utilisée pour la régression

---

### Khi-deux (*Chi-Square*)
→ Test de dépendance statistique

---

## Algorithmes d’arbres de décision (*Decision tree algorithms*)

- **ID3**
- **C4.5**
- **CART**
- **CHAID**
- **MARS**

---

## Avantages (*Advantages*)
- Interprétable
- Peu de prétraitement
- Gère les valeurs manquantes

---

## Inconvénients (*Disadvantages*)
- Sensible au bruit
- Sur-apprentissage possible
- Coût de calcul élevé

---

## À retenir (*Key takeaway*)

> Les arbres de décision utilisent des règles **if–else** basées sur les attributs les plus informatifs pour effectuer des prédictions.

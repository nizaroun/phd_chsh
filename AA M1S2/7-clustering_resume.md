# Clustering – Résumé (Cours #7)

## Définition
Le **clustering** (*clustering*) est une méthode d’**apprentissage non supervisé** (*unsupervised learning*) qui consiste à regrouper des données **non étiquetées** (*unlabeled data*) en **groupes homogènes** (*clusters*) selon leur similarité.

Objectif :
- **Forte similarité intra-cluster** (*high intra-cluster similarity*)
- **Faible similarité inter-cluster** (*low inter-cluster similarity*)

---

## Apprentissage non supervisé (*Unsupervised learning*)

- Pas de variable cible (*no target / no labels*)
- Découverte de structures cachées (*hidden patterns*)
- Regroupement, réduction de dimension, détection d’anomalies

### Types principaux
- **Clustering**
- **Association rules** (*association*)

---

## Types de Clustering (*Types of clustering*)

### Hard Clustering
Un point appartient à **un seul cluster**.

### Soft / Fuzzy Clustering
Un point peut appartenir à **plusieurs clusters** avec un degré d’appartenance.

---

## Méthodes de Clustering (*Clustering methods*)

### 1. Partitionnement (*Partitioning clustering*)
- Nombre de clusters fixé (**k**)
- Basé sur des **centroïdes** (*centroids*)
- Exemple : **K-Means**

---

### 2. Clustering basé sur la densité (*Density-based clustering*)
- Basé sur des zones denses
- Gère le bruit (*noise*)
- Clusters de forme arbitraire
- Exemple : **DBSCAN**

---

### 3. Clustering hiérarchique (*Hierarchical clustering*)
- Construction d’une hiérarchie (*dendrogram*)
- Pas besoin de fixer k à l’avance

Types :
- **Agglomératif** (*bottom-up*)
- **Divisif** (*top-down*)

---

### 4. Modèle probabiliste (*Model-based clustering*)
- Basé sur des distributions statistiques
- Exemple : **GMM – Gaussian Mixture Model**

---

## K-Means Clustering

### Principe
Algorithme itératif qui minimise la **variance intra-cluster**.

### Étapes
1. Choisir le nombre de clusters **k**
2. Initialiser les centroïdes
3. Assigner chaque point au centroïde le plus proche
4. Recalculer les centroïdes
5. Répéter jusqu’à convergence

---

### Fonction objectif (*Objective function*)


$$WCSS = \sum_{k=1}^{K} \sum_{x_i \in C_k} ||x_i - \mu_k||^2$$

$$
\text{WCSS}
=
\sum_{P_i \in \text{Cluster}_1} \text{distance}(P_i, C_1)^2
+
\sum_{P_i \in \text{Cluster}_2} \text{distance}(P_i, C_2)^2
+
\sum_{P_i \in \text{Cluster}_3} \text{distance}(P_i, C_3)^2
$$

- **WCSS** : Within-Cluster Sum of Squares
- $(\mu_k$) : centroïde du cluster $k$

---

### Choix du nombre de clusters (*Choosing k*)

#### Elbow Method
- Tracer $WCSS$ en fonction de $k$
- Le « coude » indique le meilleur $k$

#### Silhouette Method
Mesure cohésion vs séparation :


$$s(i) = \frac{b(i) - a(i)}{\max(a(i), b(i))}$$


- $(a(i)$) : distance moyenne intra-cluster
- $(b(i)$) : distance moyenne vers le cluster le plus proche
- $(s \in [-1,1]$)

---

## Clustering Hiérarchique (*Hierarchical clustering*)

### Dendrogramme (*Dendrogram*)
- Représentation graphique des fusions
- Coupe horizontale → clusters finaux

### Mesures de distance (*Linkage*)
- Single linkage
- Complete linkage
- Average linkage
- Ward method

---

## DBSCAN (Density-Based Spatial Clustering of Applications with Noise)

### Hyperparamètres
- **Eps** : rayon de voisinage (*neighborhood radius*)
- **MinPts** : nombre minimum de points

### Types de points
- **Core point** (*point cœur*)
- **Border point** (*point frontière*)
- **Noise / Outlier** (*bruit*)

### Avantages
- Pas besoin de k
- Gère le bruit
- Clusters non convexes

---

## Autres algorithmes de Clustering

- **Mean-Shift**
- **BIRCH**
- **GMM**
- **Ward**
- **EM (Expectation Maximization)**
- **PCA / ACP**
- **LDA**
- **Autoencoders**

---

## Applications (*Applications*)

- Segmentation client (*customer segmentation*)
- Analyse de marché
- Vision par ordinateur (*image segmentation*)
- Détection d’anomalies (*anomaly detection*)
- Bio-informatique
- Systèmes de recommandation

---

## Avantages (*Advantages*)

- Pas besoin de labels
- Découverte de structures cachées
- Très utilisé en exploration de données

---

## Inconvénients (*Disadvantages*)

- Évaluation difficile
- Choix des hyperparamètres critique
- Sensible au bruit et à l’échelle

---

## À retenir (*Key takeaway*)

> Le clustering est un pilier de l’apprentissage non supervisé permettant de découvrir des structures naturelles dans les données, avec des algorithmes adaptés selon la forme, la densité et la taille des données.

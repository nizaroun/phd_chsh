# 14 Data Mining (Fouille de Données)

## 1. Definition (Définition)

**Data Mining** (*Fouille de Données*) is the process of extracting implicit, previously unknown, and potentially useful information from data. It is a step in the broader **KDD Process** (*Knowledge Discovery in Databases*).

---

## 2. The KDD Process (Le Processus KDD)

1.  **Selection**: Selecting relevant data from the database.
2.  **Preprocessing**: Cleaning data (handling missing values, noise).
3.  **Transformation**: Dimensionality reduction, Normalization.
4.  **Data Mining**: Applying algorithms to extract patterns.
5.  **Interpretation/Evaluation**: Visualizing and validating the patterns.

---

## 3. Data Preprocessing (Prétraitement)

"Garbage In, Garbage Out".

### A. Data Cleaning (*Nettoyage*)
-   **Missing Values**: Ignore tuple, fill with mean/median, or use prediction.
-   **Noisy Data**: Binning, Regression, Clustering.

### B. Data Integration (*Intégration*)
-   Combining data from multiple sources (Databases, Files, APIs).
-   Handling Redundancy (Correlation analysis).

### C. Data Reduction (*Réduction*)
-   **Dimensionality Reduction**: PCA.
-   **Numerosity Reduction**: Sampling, Histograms.

### D. Data Transformation (*Transformation*)
-   **Normalization**: Min-Max $[0, 1]$, Z-Score (Standardization).
-   **Discretization**: Converting continuous features to categorical (e.g., Age $\rightarrow$ Young/Old).

---

## 4. Apriori Algorithm (Algorithme Apriori)

Use for **Association Rule Mining**.

> [!NOTE] Principle
> If an itemset is frequent, then all of its subsets must also be frequent. (Anti-monotonicity property).

### Steps
1.  Find all frequent 1-itemsets (Support > MinSupport).
2.  Combine them to form candidate 2-itemsets.
3.  Prune candidates that have infrequent subsets.
4.  Repeat until no more frequent itemsets can be found.
5.  Generate rules from frequent itemsets (Confidence > MinConfidence).

---

## 5. Data Warehouse (Entrepôt de Données)

A centralized repository for storing large amounts of structured data from multiple sources.

### OLTP vs OLAP
| Feature | OLTP (Online Transaction Processing) | OLAP (Online Analytical Processing) |
| :--- | :--- | :--- |
| **Focus** | Daily Operations (Bank ATM) | Decision Support (Business Intelligence) |
| **Data** | Current, detailed | Historical, summarized |
| **Users** | Clerks, DBAs | Managers, Analysts |
| **Access** | Read/Write | Read-Only (mostly) |

---

## 6. ETL (Extract, Transform, Load)
The process of moving data from sources to the Data Warehouse.
1.  **Extract**: Read from source.
2.  **Transform**: Clean, format, aggregate.
3.  **Load**: Write to target warehouse.

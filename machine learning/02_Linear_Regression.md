# 02 Linear Regression (Régression Linéaire)

## 1. Definition (Définition)

**Linear Regression** (*Régression Linéaire*) is a **supervised learning** (*apprentissage supervisé*) algorithm used to predict a **continuous** (*continue*) target variable $y$ based on one or more input features $x$.

**Model Representation**:
$$h_\theta(x) = \theta_0 + \theta_1 x_1 + \theta_2 x_2 + ... + \theta_n x_n = \theta^T x$$

-   $\theta$: Parameters / Weights (*Paramètres / Poids*)
-   $x$: Features (*Variables*)
-   $h_\theta(x)$: Hypothesis / Prediction (*Hypothèse / Prédiction*)

---

## 2. Cost Function (Fonction Coût)

To train the model, we minimize variables the error between predictions and actual values. The most common cost function is **Mean Squared Error (MSE)** (*Erreur Quadratique Moyenne*).

$$J(\theta) = \frac{1}{2m} \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)})^2$$

> [!NOTE] Formula Intuition
> The term $\frac{1}{2}$ exists to make the derivative cleaner (the 2 cancels out with the exponent).

---

## 3. Ordinary Least Squares (OLS) - The Exam Method

Unlike Gradient Descent (iterative), **OLS** (*Moindres Carrés Ordinaires*) finds the **exact analytical solution** directly. This is often asked in "pen and paper" exams for simple regression ($y = ax + b$).

### A. Scalar Formulas (Formules Scalaires)
To find the line $\hat{y} = ax + b$:

1.  **Slope ($a$)**:
    $$a = \frac{S_{xy}}{S_{xx}}$$

2.  **Intercept ($b$)**:
    $$b = \bar{y} - a\bar{x}$$

### B. Intermediate Statistics (Statistiques Intermédiaires)
You must calculate these first:
-   **Means**: $\bar{x} = \frac{1}{m}\sum x_i$, $\quad \bar{y} = \frac{1}{m}\sum y_i$
-   **Variance of X ($S_{xx}$)**:
    $$S_{xx} = \sum_{i=1}^{m} (x^{(i)} - \bar{x})^2$$
-   **Covariance ($S_{xy}$)**:
    $$S_{xy} = \sum_{i=1}^{m} (x^{(i)} - \bar{x})(y^{(i)} - \bar{y})$$

---

## 4. Optimization: Matrix Form (Forme Matricielle)
For general regression (multiple features), we use the **Normal Equation**:

$$\theta = (X^T X)^{-1} X^T y$$

> [!IMPORTANT] Comparison
> | Gradient Descent | Normal Equation (OLS) |
> | :--- | :--- |
> | Needs to choose $\alpha$ | No $\alpha$ needed |
> | Needs many iterations | Calculated in one step |
> | Works well even when $n$ is large | **Slow** if $n$ is very large ($O(n^3)$) |

---

## 5. Performance Metrics (Métriques de performance)

### Decomposition of Variance
**SST = SSR + SSE**
-   **SST ($S_{yy}$)** (*Total Sum of Squares*): Total variability. $\sum (y - \bar{y})^2$
-   **SSR** (*Sum of Squares Regression*): Explained variability. $\sum (\hat{y} - \bar{y})^2$
-   **SSE** (*Sum of Squared Errors*): Unexplained variability (Residuals). $\sum (y - \hat{y})^2$

### Pearson Correlation ($R$)
Measures the strength of linear relationship (-1 to 1).
$$R = \frac{S_{xy}}{\sqrt{S_{xx} \cdot S_{yy}}}$$

### R-Squared ($R^2$, Coefficient of Determination)
Proportion of variance explained by the model (0 to 1).
$$R^2 = \frac{SSR}{SST} = R^2 \text{ (for simple regression)}$$

> [!CHECK] Interpretation
> *   **$R^2 = 0.8$**: 80% of the variation in $Y$ is explained by the model.

### Standard Error of Estimate ($\hat{\sigma}$)
Average distance of data points from the regression line.
$$\hat{\sigma} = \sqrt{\frac{SSE}{m - 2}}$$

---

## 6. Assumptions (Hypothèses)

> [!WARNING] Critical Assumptions
> 1.  **Linearity**: The relationship between X and Y is linear.
> 2.  **Independence**: Observations are independent.
> 3.  **Homoscedasticity**: Constant variance of residuals.
> 4.  **Normality**: Residuals are normally distributed.

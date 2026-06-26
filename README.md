# Causal Inference: Instrumental Variables

Two end-to-end notebooks demonstrating **Instrumental Variables (IV)** — a method for estimating causal effects when the treatment of interest is confounded by unobserved factors. IV works by finding a variable (the *instrument*) that shifts the treatment but has no direct effect on the outcome, allowing us to isolate the causal signal from confounding noise.

---

## Notebooks

### 1. [`IV_College_Proximity_Wages.ipynb`](IV_College_Proximity_Wages.ipynb)
**Does education causally raise wages?**

Uses Card (1995)'s classic design: growing up near a 4-year college (`nearc4`) as an instrument for years of schooling (`educ`), with log hourly wages as the outcome. The notebook walks through naive OLS, the Wald estimator, full 2SLS via `linearmodels`, and diagnostics (partial F-test, Wu-Hausman test). The instrument is borderline strong (F ≈ 16), and the 2SLS estimate (~0.12 log-wage points per year of schooling) is notably larger than OLS — illustrating how IV can correct for measurement error and ability bias simultaneously.

### 2. [`Smoking_Birthweight_Weak_IV.ipynb`](Smoking_Birthweight_Weak_IV.ipynb)
**Does maternal smoking lower infant birth weight — and what happens when your instrument is weak?**

Uses Mullahy (1997)'s dataset with state cigarette prices (`cigprice`) as a proposed instrument for smoking during pregnancy (`cigs`), with birth weight in ounces as the outcome. The first stage fails decisively (partial F < 1), making this a textbook **weak instrument** case. The notebook deliberately runs 2SLS anyway to show the consequences: a sign flip, a standard error ~70× larger than OLS, and an uninformative confidence interval. A swap to cigarette tax (`cigtax`) fares no better. The takeaway is that recognizing and honestly reporting a failed instrument is itself a core IV skill.

---

## Key Concepts Covered

| Concept | Notebook |
|---|---|
| Relevance, exclusion restriction, independence | Both |
| OLS endogeneity bias | Both |
| First stage & partial F-statistic | Both |
| Wald estimator | #1 |
| 2SLS with controls (`linearmodels`) | Both |
| LATE vs. ATE interpretation | #1 |
| Wu-Hausman endogeneity test | #1 |
| Weak instrument pathology | #2 |

## References

- Card, D. (1995). *Using Geographic Variation in College Proximity to Estimate the Return to Schooling.*
- Mullahy, J. (1997). *Instrumental-Variable Estimation of Count Data Models.*
- Angrist, J. & Pischke, J-S. *Mostly Harmless Econometrics*
- Cunningham, S. *Causal Inference: The Mixtape*
- Staiger, D. & Stock, J.H. (1997). *Instrumental Variables Regression with Weak Instruments.* Econometrica.

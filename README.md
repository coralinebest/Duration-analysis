# Duration Analysis: Replication of Lalive, van Ours, and Zweimüller (2006)

This repository contains the code and analysis for the replication of the study **"How Changes in Financial Incentives Affect the Duration of Unemployment"** by Lalive, van Ours, and Zweimüller, published in *The Review of Economic Studies* (2006). The project was developed as part of a Master's level assignment supervised by Christian Schluter.

---

## 🔍 1. Research Objectives

This project aims to:
- Understand the causal impact of changes in unemployment benefit policies on the duration of unemployment.
- Replicate key findings of Lalive et al. (2006) using Difference-in-Differences (DiD), Kaplan-Meier estimators, and Proportional Hazard (PH) models.
- Practice survival analysis and causal inference on large administrative datasets.

## 📚 2. Background

In 1989, Austria modified its unemployment benefit system, changing both the **Replacement Rate (RR)** and the **Potential Benefit Duration (PBD)**. The policy reform affected groups of unemployed individuals differently based on age and previous work experience.

The study leverages this natural experiment using a quasi-experimental setup to estimate the effects of financial incentives on job search behavior.


## 🧹 3. Data Preparation

- Data Source: `fi.dta` (225,821 unemployment spells).
- Processing done using `tidyverse`, `survival`, and base R.
- Focus on relevant variables: spell duration (`dur`), policy group (`type`), censorship indicator (`uncc`), and treatment flags (`tr`, `t39`, `t52`, etc.).

Key steps:
- Censor durations at 104 weeks.
- Generate treatment/control group variables.
- Prepare dataset for survival and PH model analysis.

## 📉 4. Difference-in-Differences (DiD)

- Replicated **Table 4** from the original paper using DiD estimators.
- Estimated treatment effects before/after the reform using group-level average unemployment duration.
- Visual inspection of group means before and after the reform.


## 📈 5. Survival Function & Hazard Estimation

- Replicated **Figure 3**: Kaplan-Meier survival curves for treatment vs. control groups.
- Replicated **Figure 4**: Hazard function estimates using smoothed kernel density (`locpoly` from `KernSmooth`).
- Analyzed heterogeneity in job-finding rates over time.


## ⚙️ 6. Estimating Treatment Effects in a PH Model

- Estimated a **Piecewise Exponential (PWE) Proportional Hazard model**.
- Captured baseline hazard as a function of time intervals (every 4 weeks).
- Included interaction terms to isolate policy effects.
- Model estimated using `survival::survSplit` and `coxph`.

Sample output:
- 15 interval-specific coefficients for baseline hazard.
- Log-likelihood and sample size reported.
- Compared estimates to Appendix Table from original paper.


## 🛠️ Technologies Used

- **R**: Data manipulation, modeling, and visualization.
- **R packages**: `tidyverse`, `survival`, `KernSmooth`, `foreign`, `stargazer`

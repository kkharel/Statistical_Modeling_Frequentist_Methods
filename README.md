# Hypothesis Testing and Causal Inference Guide

## Overview

This Jupyter Notebook, **`Hypothesis_Testing.ipynb`**, is a comprehensive, step-by-step guide to statistical hypothesis testing. It transitions from foundational statistical theory to advanced practical applications, focusing particularly on mean comparison tests and quasi-experimental methods.

It is designed for data scientists, analysts, and researchers seeking a rigorous understanding of how to establish statistical significance and measure causal effects in real-world data.

---

## Key Topics Covered

The notebook is divided into four main sections, demonstrating both the theoretical background and the hands-on code execution for each test.

### 1. Foundational Concepts
* **Core Definitions:** Null Hypothesis ($H_0$), Alternative Hypothesis ($H_1$), One-tailed vs. Two-tailed tests.
* **Errors and Power:** Detailed explanation of Type I ($\alpha$), Type II ($\beta$), and Statistical Power ($1-\beta$). 
* **P-Value:** A precise, intuitive explanation of the p-value concept.
* **Methodology:** A full 8-step process for conducting rigorous hypothesis tests.

### 2. Power and Sample Size Planning
* Demonstrates how to calculate the minimum required **Sample Size** ($n$) using both manual approximations (Z-test) and dedicated statistical library functions (`statsmodels` T-test) to achieve a desired statistical **Power** ($1-\beta$).

### 3. The Standard Statistical Toolkit
Practical, code-driven examples for common testing scenarios:
* **Paired $t$-test:** Analyzing repeated measures (Observational Pre-Post design).
* **Independent $t$-test:** Analyzing two independent groups (Experimental A/B Testing design).
* **Repeated Measures ANOVA:** Analyzing three or more repeated measures, including checks for the **Sphericity** assumption (Mauchly's Test).
* **Chi-Square Test of Independence:** Testing for association between two categorical variables, including post-hoc analysis via Standardized Residuals and Fisher's Exact Test.

### 4. Advanced Causal Inference
The final section covers sophisticated methods for measuring causation when full randomization is not possible:
* **Difference-in-Differences (DiD):** A quasi-experimental technique relying on the **Parallel Trends Assumption** to isolate treatment effects by comparing the change in a treatment group to the change in a control group.
* **Synthetic Control Method (SCM):** An advanced method for creating a statistical counterfactual for a single treated unit (e.g., a state or company) by optimally weighting a pool of control units. 

---

## Known Issues and Recommended Enhancements

As of this version, the notebook is highly focused on mean comparison tests. For a truly "complete guide to statistical modeling," the following areas are currently missing and are recommended for future exploration:

| Missing Topic | Why it Matters | Next Step for Reader |
| :--- | :--- | :--- |
| **Regression-Based Hypothesis Testing** | The notebook is missing the use of Linear (OLS) and Logistic (Logit) Regression to test the significance of coefficients **while controlling for multiple variables (confounders)**. | Explore `statsmodels.formula.api` for multivariate $t$-tests on coefficients. |
| **Multiple Testing Correction** | The notebook does not address the inflation of the **Type I Error** rate that occurs when running many independent tests (common in A/B testing on multiple KPIs). | Study **False Discovery Rate (FDR)** methods like Benjamini-Hochberg (BH). |
| **Bayesian Inference** | The entire notebook is Frequentist (p-value based). It omits the **Bayesian** approach, which uses the **Bayes Factor** and allows for evidence *in favor of* the Null Hypothesis. | Look into libraries like `PyMC` or `bambi` for Bayesian model fitting. |
| **Time Series A/B Testing** | For data that is dependent over time (e.g., weekly sales), standard t-tests are invalid. Specialized methods (e.g., CausalImpact) are needed. | Research **Causal Impact** or **Switchback** designs for time-dependent data. |

---

## Dependencies and How to Run

This notebook requires the following standard libraries:

```bash
numpy
pandas
scipy
statsmodels
matplotlib (for visualizations)

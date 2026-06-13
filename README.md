<<<<<<< HEAD
=======
# ML_linear-regression-capstone
Linear regression capstone project for Medical Insurance predictor
>>>>>>> a86b7292dbbeacc6e99cdea847ace195908b122e
# Medical Insurance Cost Predictor

A supervised machine learning project that predicts annual medical insurance charges based on patient demographics and lifestyle factors, using **linear regression implemented from scratch** with NumPy, validated against scikit-learn.

---

## Problem Statement

Medical insurance costs vary widely across individuals. This project builds a regression model to predict annual charges (in USD) from six patient features: age, sex, BMI, number of children, smoking status, and region. The goal is to understand which factors drive cost the most — and quantify that relationship with a trained linear model.

**Dataset:** [Medical Cost Personal Dataset](https://www.kaggle.com/datasets/mirichoi0218/insurance) — 1,338 records, 7 columns, no missing values.

---

## Key Findings

- **Smoking is the single largest cost driver.** Smokers pay approximately $23,000 more per year on average than non-smokers, all else equal.
- **BMI interacts with smoking status.** A `bmi × smoker` interaction feature captures a non-linear cost spike for obese smokers, improving model R² significantly.
- **Age has a steady linear relationship** with charges — each additional year adds roughly $250–$300 in predicted annual cost.

## Coefficient Summary

         Feature  Coefficient
      bmi_smoker 18608.731140
          smoker -8570.662519
             age  3705.216463
        children   563.530391
region_southwest  -531.739530
region_southeast  -426.716078
region_northwest  -269.379329
             sex  -262.537886
             bmi   122.326119


---

## Model Performance

=======================================================
         FINAL MODEL PERFORMANCE SUMMARY
=======================================================
  Dataset         : Medical Cost Personal (n=1,338)
  Algorithm       : Linear Regression
  Features used   : 9
  Train/Test split: 80% / 20%

  Metric        From Scratch    Scikit-learn
  ----------------------------------------
  MSE          20,914,464.95   20,919,716.75
  RMSE              4,573.23        4,573.81
  R²                  0.8653          0.8653
=======================================================

---

## Project Structure

```
insurance-cost-predictor/
│
├── data/
│   └── insurance.csv          # Raw dataset (download from Kaggle)
│
├── medicalinsurance_cost_predictor.ipynb  # Main notebook (all 5 phases)
│
└── README.md
```

---

## Notebook Overview

The notebook is organized into five sections:

1. **Exploratory Data Analysis** — distribution plots, correlation heatmap, scatter plots colored by smoker status, boxplots by region/sex
2. **Preprocessing & Feature Engineering** — encoding categoricals, standard scaling, train/test split, BMI × smoker interaction feature
3. **Linear Regression from Scratch** — cost function, gradient computation, gradient descent loop, convergence plots, learning rate experiments
4. **Scikit-learn Comparison** — validates from-scratch results, coefficient table sorted by importance, predicted vs actual plot, residual analysis
5. **Business Insights** — plain-English findings, model limitations, suggested next steps

---

## How to Run

**1. Clone the repo**
```bash
git clone https://github.com/apsarvalishaik/ML_linear-regression-capstone.git
cd insurance-cost-predictor
```

**2. Download the dataset**

Download `insurance.csv` from [Kaggle](https://www.kaggle.com/datasets/mirichoi0218/insurance) and place it in the `data/` folder.

**3. Install dependencies**
```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

**4. Launch the notebook**
```bash
jupyter notebook medicalinsurance_cost_predictor.ipynb
```

---

## Dependencies

| Package | Purpose |
|---|---|
| `numpy` | Matrix operations, gradient descent implementation |
| `pandas` | Data loading, manipulation, feature engineering |
| `matplotlib` | Plotting convergence curves, residuals, scatter plots |
| `seaborn` | Correlation heatmap, distribution plots, boxplots |
| `scikit-learn` | Train/test split, StandardScaler, LinearRegression (validation) |

Python 3.8+ recommended.

---

## What I Built From Scratch

The core linear regression implementation (Phase 3) uses only NumPy — no scikit-learn — and follows Andrew Ng's notation from the Machine Learning Specialization:

- `compute_cost(X, y, w, b)` — vectorized MSE cost function
- `compute_gradient(X, y, w, b)` — vectorized gradient computation
- `gradient_descent(X, y, w_init, b_init, alpha, num_iters)` — full training loop with cost history

Results are then verified against `sklearn.linear_model.LinearRegression` to confirm correctness.

---

## Limitations & Next Steps

**Current limitations:**
- Linear regression assumes a linear relationship between features and charges; the actual relationship (especially for smokers) has non-linear components
- The dataset does not include pre-existing conditions, which are major real-world cost drivers
- Regional cost differences are likely driven by local healthcare pricing, not just geography

**Natural extensions:**
- Polynomial features to capture non-linearity
- Ridge / Lasso regression to explore regularization
- Decision tree or gradient boosting for comparison

---

## About

Built as a portfolio capstone project while working through Andrew Ng's [Machine Learning Specialization](https://www.coursera.org/specializations/machine-learning-introduction) (Supervised Learning course). The goal was to reinforce linear regression fundamentals by applying them end-to-end on a real dataset, from EDA through residual analysis and business interpretation.

<!-- TODO: Add a screenshot of your best chart here once the notebook is complete -->
<!-- Example: ![Smoker vs Non-Smoker Cost Distribution](images/smoker_boxplot.png) -->

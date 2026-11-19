# COMP2200/COMP6200 Assignment 1 — Garza Inc & Sons (12-Month Venture Capital Forecast)

A statistical modeling and live investment-committee presentation notebook evaluating **Garza Inc & Sons** over 24 monthly operational observations (`48474967_Garza_Inc_and_Sons.csv`) to project **Payroll**, **Revenue**, and **Negative Media Coverage** 12 months ahead (**Month 36**).

## Repository Contents

- [`assignment1.ipynb`](assignment1.ipynb) — End-to-end executed Jupyter notebook structured into 6 narrative Acts plus a **5-Slide Executive Presentation Deck** with boardroom visuals, Reveal.js/RISE slideshow metadata, and complete statistical diagnostics (`102` cells, `13` figures).
- [`48474967_Garza_Inc_and_Sons.csv`](48474967_Garza_Inc_and_Sons.csv) — 24-month historical dataset (`Months_Since_Launch`, `Payroll`, `Revenue`, `Base_10_Log_Revenue`, `Scandals`, `Media Coverage`).
- `.gitignore` — Excludes Jupyter checkpoints and Python/OS cache files.

## Executive Summary (Month 36 Outlook)

| Metric | Month 24 Actual | Month 36 Forecast | 95% Prediction Interval | Model & Validation |
|---|---|---|---|---|
| **Monthly Payroll** | `$2.99M` | **`$3.74M / mo`** (`+$64.6k/mo`) | `$3.55M – $3.93M` | `HuberRegressor` (`59.8%` lower Val MAE vs. OLS; Rolling CV MAE `$72.0k`, `2.79%` MAPE) |
| **Monthly Revenue** | `$749k` | **`$3.66M / mo`** median (`$3.74M` smeared mean) | `$2.01M – $6.65M` | `LinearRegression` on `Base_10_Log_Revenue` (`+16.74%/mo`; `38.9%` lower Rolling CV USD MAE vs. raw OLS) |
| **Net (Rev − Payroll)** | `-$2.24M` | **`-$84k / mo`** *(breakeven ~M36–37)* | `-$1.92M` (Bear) to `+$3.10M` (Bull) | Narrowing operational deficit approaching breakeven |
| **Media Coverage** | `Negative` (M11–24) | **`99.99%` `Negative`** *(Scandals = 0)* | Insensitive across 95% bounds | `Pipeline(StandardScaler + LogisticRegression)` (`100%` holdout, 5-Fold & LOOCV) |

**VC Verdict:** **Conditional Due Diligence** — strong top-line growth nearing payroll breakeven, contingent on auditing the **Month 11 `$5.97M` payroll spike**, **Month 14 scandal**, customer retention/unit economics, and PR turnaround strategy.

## How to View or Present

- **Direct Notebook Walkthrough:** Open `assignment1.ipynb` in GitHub, JupyterLab, or VS Code (all outputs and charts are pre-rendered).
- **Slide Deck Mode (Reveal.js):**
  ```bash
  jupyter nbconvert assignment1.ipynb --to slides --post serve
  ```
- **Reproduce End-to-End:** Requires Python 3.11+ with `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, and `scipy`.

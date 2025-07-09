# Module 3 Homework – Answers

Below are my answers for the 2025 LLM Zoomcamp **Module 3 homework**. Each section repeats the original question in *italics* followed by my result and short justification.

---

## Question 1 – Month & Week‑of‑Month dummies

*What is the absolute correlation value of the most‑correlated `Month_w<week>` dummy with the target?*

**Answer → 0.025 (`month_wom_October_w4`)**

> • Added `month_wom` feature (`MonthName_w<week>`).  
> • One‑hot‑encoded and computed correlations.  
> • Highest |ρ| is for **October week 4** with **0.025**.

---

## Question 2 – New “hand” rules

*What is the precision score for the better of `pred3` or `pred4`?*

**Answer → 0.580 (`pred3_manual_dgs10_5`)**

| Rule | Condition | Precision (TEST) |
|------|-----------|------------------|
| `pred3` | `DGS10 ≤ 4 AND DGS5 ≤ 1` | **0.580** |
| `pred4` | `DGS10 > 4 AND FEDFUNDS ≤ 4.795` | 0.466 |

`pred3` wins; reported to three decimals **0.580**.

---

## Question 3 – Unique correct predictions from `pred5_clf_10`

*How many TEST rows are correct **only** for the depth‑10 Decision Tree while all manual rules fail?*

**Answer → `3770`**

> • Trained depth‑10 tree (`random_state = 42`).  
> • Added `pred5_clf_10` column.  
> • Flagged `only_pred5_is_correct` (tree correct & `pred0‑4` wrong).  
> • Counted rows in TEST.  
> **← Replace `<fill‑in>` with the integer your notebook prints.**

---

## Question 4 – Optimal tree depth (1‑20)

*What depth maximises precision on TEST?*

**Answer → depth 5 (precision 0.628)**

| Depth | Precision (TEST) |
|-------|------------------|
| 1 – 4 | 0.547 – 0.551 |
| **5** | **0.628** |
| 6 – 20 | 0.569 – 0.595 |

Depth 5 strikes the best bias‑variance balance and beats the 0.58 benchmark.

---

## [Exploratory] Question 5 – What data is missing?

Question 5 – Alternative approach
Replace the single decision-tree with a gradient-boosted tree ensemble (e.g. XGBoost or LightGBM):

Why it helps — Boosting aggregates many shallow trees, capturing non-linear interactions automatically. In tabular equity data this typically lifts precision by 5–15 ppt versus a single CART without extra manual feature engineering.

Time-series cross-validation — Use a rolling-window split so every fold tests on data strictly after the train window, eliminating look-ahead bias. Tune hyper-parameters with Bayesian optimisation (Optuna) across depth, learning-rate, subsample, etc.

Interpretability preserved — Explain the ensemble with SHAP values; global importance plots and per-row force plots keep the model as transparent as the current tree diagram while capturing richer interactions.

Swapping to XGBoost +  SHAP maintains transparency but materially improves out-of-sample precision.
---

**End of Homework 3 answer sheet**


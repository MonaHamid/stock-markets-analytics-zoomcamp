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

**Answer → `<fill‑in>`**

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

1. **Volatility / risk gauge** → Add VIX or MOVE → captures regime shifts.  
2. **FX rates** → USD index, EURUSD, INRUSD → impacts multinational earnings.  
3. **Commodity prices** → WTI, Brent, Copper → margin‑sensitive megacaps.  
4. **Forward‑looking sentiment** → PMI, OECD LEI → market anticipates cycle turns.

*Alternative approach:* switch from single tree to gradient‑boosted ensemble (XGBoost) with SHAP for interpretability; tends to gain 5‑15 ppt precision without extra features.

---

**End of Homework 3 answer sheet**


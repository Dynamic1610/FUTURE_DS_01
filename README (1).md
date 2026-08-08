# Superstore Sales Performance Analytics

**Business Sales Performance Analytics — Data Science & Analytics Internship, Task 1**

An analysis of 5,009 orders (9,994 line items) from a US retail superstore, covering January 2014 – December 2017, to identify where revenue and profit come from and where the business is leaving money on the table.

**[→ View the interactive dashboard](./superstore_sales_dashboard.html)**

---

## 1. Executive Summary

The business is growing — sales rose from $484K (2014) to $733K (2017), a compound trend of roughly 15% per year. But profit hasn't kept pace, because a meaningful share of every year's revenue comes from products and discount terms that are unprofitable by design.

Four findings drive this report:

1. **Furniture sells like a star and earns like an afterthought.** It brings in nearly as much revenue as Technology, but converts it into a 2.5% margin instead of 17%+.
2. **Discounts above ~20% are, in aggregate, money losers.** This one variable explains most of the difference between a profitable order and an unprofitable one.
3. **The Central region underperforms** West and East by 6–7 points of margin, tracking closely with its Furniture and discount mix.
4. **A handful of high-margin Office Supplies categories are under-leveraged** relative to their profitability.

None of these require new customers or new products — they're changes to *what's already being sold and how it's discounted*.

## 2. Data & Methodology

- **Dataset:** [Sample Superstore](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final) (Kaggle) — order-level retail transactions with Sales, Profit, Discount, Quantity, Category/Sub-Category, Region, and Segment fields.
- **Scope:** 9,994 line items, 5,009 unique orders, 793 unique customers, Jan 2014 – Dec 2017.
- **Data quality:** No missing values, no duplicate rows. Verified date parsing and numeric ranges before analysis.
- **Tools:** Python (pandas for analysis, Plotly for the interactive dashboard).
- **Key derived metric:** Margin % = Profit ÷ Sales, used throughout to separate "sells well" from "earns well" — the dataset's single biggest analytical lesson is that these are not the same thing.

## 3. Key Findings

### 3.1 Revenue trend
Sales grew every year except a slight dip in 2015, with profit growing faster than sales in percentage terms most years. Every year shows the same seasonal shape: a slow first half, then a strong September and a very strong November–December, consistent with back-to-school and year-end/holiday business purchasing.

### 3.2 Category & sub-category performance

| Category | Sales | Profit | Margin |
|---|---|---|---|
| Technology | $836K | $145K | **17.4%** |
| Office Supplies | $719K | $122K | **17.0%** |
| Furniture | $742K | $18K | **2.5%** |

Furniture's weak margin isn't spread evenly — it's concentrated in two sub-categories:

| Sub-Category | Sales | Margin |
|---|---|---|
| Tables | $207K | **-8.6%** |
| Bookcases | $115K | **-3.0%** |
| Chairs | $328K | 8.1% |
| Furnishings | $92K | 14.2% |

Tables and Bookcases are losing money outright — every dollar of Table sales currently *costs* the business 8.6 cents.

The highest-margin sub-categories in the whole business are easy to overlook because they're small: **Labels (44.4%), Envelopes (42.3%), Paper (43.4%), and Copiers (37.2%)** all outperform every Furniture line by a wide margin.

### 3.3 The discount trap
Grouping every order by the size of the discount applied shows a clean pattern:

| Discount Band | Total Profit |
|---|---|
| 0% | +$321K |
| 1–20% | +$101K |
| 21–40% | **-$36K** |
| 41–60% | **-$29K** |
| 60%+ | **-$71K** |

Profit is positive through 20% off and negative at every band beyond it. This same pattern shows up inside Tables specifically: undiscounted Tables are profitable (+$13K); once discounts exceed 20%, Tables lose money at every level tested. Discounting isn't the only cause of Furniture's weak margin, but it's the most controllable one.

### 3.4 Regional performance

| Region | Sales | Margin |
|---|---|---|
| West | $725K | 14.9% |
| East | $679K | 13.5% |
| South | $392K | 11.9% |
| Central | $501K | **7.9%** |

Central lags the other three regions by a meaningful margin despite handling a comparable order volume to South. This is consistent with — though not fully explained by — Central carrying a heavier mix of Furniture and deeper average discounts; it's worth a closer regional cut before concluding the cause.

### 3.5 Product-level extremes
The single largest revenue driver is the **Canon imageCLASS 2200 Advanced Copier** ($61.6K in sales, $25.2K in profit — a standout performer). At the other end, the **Cubify CubeX 3D Printer (Double Head)** alone lost **$8.9K**, and several Furniture/Machines items appear repeatedly among the ten biggest losses — reinforcing the category-level finding rather than being isolated incidents.

## 4. Recommendations

| Priority | Recommendation | Why |
|---|---|---|
| **1** | Cap standard discounting at 20%; require approval above that line | Cleanest, most controllable lever — profit turns negative almost exactly at this threshold |
| **2** | Re-price or renegotiate cost on Tables and Bookcases | These lines lose money even before heavy discounting is applied |
| **3** | Audit Central region's discount approvals and category mix | Largest unexplained regional profit gap; likely connected to Findings 1 & 2 |
| **4** | Bundle high-margin Office Supplies (Paper, Labels, Envelopes) with Technology purchases | Grows the most profitable lines without taking on Furniture-style margin risk |

## 5. Files in this repository

- `superstore_sales_dashboard.html` — self-contained interactive dashboard (open directly in any browser, no server needed)
- `README.md` — this report

---
*Prepared as a Data Science & Analytics internship deliverable. Dataset and task brief per Future Interns Task 1 (2026).*

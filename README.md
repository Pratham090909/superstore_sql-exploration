# Superstore Sales — SQL Exploration

Exploratory data analysis of the Superstore retail dataset using SQL (DuckDB) in a Python/Colab notebook — deriving core business KPIs and answering targeted business questions directly through queries, as a companion piece to my [Power BI executive dashboard](https://github.com/Pratham090909/superstore-executive-dashboard) built on the same data.

---

## Overview

**Dataset:** Superstore Sales (9,800 rows · 4,922 orders · 793 customers)
**Tools:** Python, DuckDB (SQL on a pandas DataFrame), Google Colab
**Goal:** Practice writing SQL directly against the dataset to derive KPIs and answer specific business questions — a query-first complement to the visual BI approach.

---

## Core KPIs Derived

| Metric | Value |
|---|---|
| Total Rows | 9,800 |
| Total Sales | $2,261,536.78 |
| Total Orders | 4,922 |
| Total Customers | 793 |
| Average Sales per Order | $459.48 |

*(Cross-checked against the Power BI dashboard build — numbers match.)*

---

## Questions Explored

**Category & Sub-Category**
- Sales by category: **Technology** leads ($827K), then Furniture ($729K), then Office Supplies ($705K).
- Sales by sub-category: **Phones** ($327.8K) and **Chairs** ($322.8K) are the top two, well ahead of Storage, Tables, and Binders.
- Category sales broken down by region and year.

**Time**
- Monthly sales trend (48 months, 2015–2018).
- Yearly totals: 2015 ($479.9K) → 2016 ($459.4K, a decline) → 2017 ($600.2K) → 2018 ($722.1K, the strongest year).

**Regional**
- Orders by region: South has the fewest orders (810) and fewest customers (509) of any region.
- Average sales per order by region: **East** has the highest AOV ($489.06), followed closely by South ($480.43) — both outpacing West and Central. South's revenue shortfall is a reach/volume problem, not a basket-size problem.
- Full region × segment breakdown (customers, orders, sales, AOV) for all 12 combinations.

**Concentration & Risk**
- Top 10 products by sales, and their share of total revenue: **~10.8%**.
- Top 10 customers' share of total revenue: **~6.8%**.
- Both figures indicate revenue is broadly distributed — not concentrated in a small number of products or customers.

---

## Approach

All queries run via **DuckDB**, querying directly against a pandas DataFrame loaded from the raw CSV (`duckdb.sql("...")` against `df`), rather than pandas method chaining — chosen deliberately to practice SQL syntax (aggregation, `GROUP BY`, `date_trunc`, CTEs, window-style percentage-of-total calculations) directly.

Notebook structure follows a "how much / when / where" question framework, starting from basic row/sales counts and building up to multi-dimensional breakdowns (region × segment) and concentration-risk questions (top N contribution to total sales).

---

## Files

- `DA.ipynb` — the full notebook, runnable in Google Colab or locally with `duckdb` and `pandas` installed.

---

## Related

See the visual, management-facing version of this analysis:(**[Superstore Executive Dashboard (Power BI)](https://github.com/Pratham090909/superstore-executive-dashboard)**).

---

## Notes

Dataset: Sample Superstore (public dataset commonly used for BI/analytics practice, sourced via Kaggle/Tableau).

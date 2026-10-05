# E-Commerce Data Analysis

A hands-on analysis of a 4-table e-commerce dataset (orders, customers, monthly revenue, and product summary) in Excel — reconciling inconsistent source files, then answering four business questions with PivotTables, SUMIFS/COUNTIFS, and charts.

## Dataset

| File | Rows | Grain |
|---|---|---|
| `orders.xlsx` | 25,000 | One row per order |
| `customers.xlsx` | 8,000 | One row per customer |
| `monthly_revenue.xlsx` | 75 | One row per month, 2020–2026 |
| `product_summary.xlsx` | 140 | One row per product |

`orders.xlsx` was found to be roughly a 19% random sample of true order activity (confirmed by comparing `customers.xlsx`'s own order totals against the row count), not a time- or status-based filter. It's reliable for rates and patterns, not for absolute totals.

## Questions answered

**1. Is revenue actually declining?**
Nominal monthly revenue is flat, 2020–2026 — no visible trend. But adjusted for inflation (CPI-compounded, restated in 2025 dollars), real revenue fell **~18%** from 2020 to 2025. Order count, average order value, and units shipped per month are all flat too, ruling out internal causes — the decline is purely the cost of living outpacing flat nominal revenue.

**2. Why is Electronics such a large share of revenue?**
Electronics is 18% of orders but **37% of revenue** — roughly double its "fair share." The cause is price, not volume or discounting: its average unit price ($139) is about double the business average ($68), revenue is spread across many products rather than one bestseller, and its discount rate (5–6%) is no different from any other category.

**3. Do a small number of customers drive most of the revenue?**
Yes. The top 10% of customers account for **42%** of all spend; the top 20% account for **61%**; the bottom 50% account for only **12%**. Higher membership tiers (Gold, Platinum) are overrepresented in the top group, but acquisition channel and country show no meaningful difference — top customers aren't concentrated in any one marketing channel or region.

**4. Do larger discounts drive larger orders?**
No. Average order value falls in a near-straight line as discount increases ($133 at 0% discount → $62 at 50%), while average items per order stays flat at ~1.7 across every discount level. Discounting isn't earning extra volume — it's close to pure margin given away.

## Tools used

Excel only: PivotTables, `SUMIFS`/`COUNTIFS`, `PERCENTILE`, helper columns, and native charts. No external BI tools or scripting.

## Limitations

- `orders.xlsx` is a ~19% sample — dollar totals understate the true business scale; percentages and rates are the reliable output.
- Item-level price trends couldn't be checked: product names are too coarse (e.g. "Tire Inflator" spans $40–$100), likely covering several underlying models under one name.
- A churn investigation was attempted but dropped — the available signals didn't produce a clear, trustworthy explanation.

# Campus Store Performance Analytics — Final Submission

A reproducible analysis of a fictional campus store using the CareerSwami synthetic dataset.

## Start here
1. Read `06_Final/Business_Insight_Memo.pdf`.
2. Open `04_Dashboard/index.html` in a browser (keep the PNG charts beside it).
3. Review `02_Data/campus_store_cleaned.csv` and `05_Evidence/` for cleaning lineage.
4. Use `07_PowerBI/PowerBI_Build_Guide.md` to recreate and save the native Power BI `.pbix` file.

## Question
Why can visits increase while business performance weakens, and what does the category-level evidence show?

## Grain and cleaning
- One row per week × category (12 canonical rows).
- Untouched supplied raw file: `02_Data/campus_store_raw_preserved.csv`.
- Untouched dirty input: `02_Data/campus_store_dirty_input.csv` (13 rows).
- One duplicate Week 1 Books row removed using `(week, category)` as key.
- Blank Week 2 Stationery orders restored to 96 by lookup against supplied canonical raw source.
- Cleaned result: 12 rows.

**Source-instruction note:** The supplied README says the known blank may be restored from canonical raw; the student guide/workbook also presents a conservative option to keep it unknown. This submission chooses the canonical lookup approach because the exact matching source row is supplied. The choice and its risk are documented in the quality and transformation logs. If your mentor requires the conservative treatment, retain the null and recalculate affected order-based metrics rather than silently substituting zero.

## Canonical totals
- Visits: 3,060
- Orders: 624
- Gross revenue: ₹80,550
- Returns: 43

## Measures
- Conversion = SUM(orders) / SUM(visits)
- Return rate = SUM(returns) / SUM(orders)
- AOV = SUM(gross revenue) / SUM(orders)
- Revenue per visit = SUM(gross revenue) / SUM(visits)

Use ratio-of-sums measures, not averages of row-level percentages.

## Main finding
Books visits rise 40% (200→280) from Week 1 to Week 4, while orders fall 30% (40→28) and gross revenue falls 30% (₹8,000→₹5,600). Conversion falls 20%→10%; return rate rises 5%→17.86%. Week 3 is the first visible deterioration, but the dataset does not show why.

Accessories return rate rises from 13.33% to 25%. Stationery conversion remains 30% in each week.

## Limitations
Revenue is gross before refunds. Refund amounts, cost/profit, return reasons, item-level data, traffic sources and customer cohorts are not supplied. Net revenue and profit cannot be calculated; causes cannot be established from four weekly observations.

## Files
- `01_Brief/` — data dictionary and project framing
- `02_Data/` — preserved inputs and cleaned data
- `03_Analysis/` — metric tables and model description
- `04_Dashboard/` — browser dashboard and chart assets
- `05_Evidence/` — quality, transformation, evidence logs and file index
- `06_Final/` — manager memo and five-slide story
- `07_PowerBI/` — DAX measures and Power BI build guide

## AI and source disclosure
AI assistance was used to help prepare analysis, documentation, charting and workbook artifacts. The learner must independently verify calculations, understand the cleaning decisions, complete the native Power BI report, and disclose this assistance as required by the programme. All data are fictional/synthetic.

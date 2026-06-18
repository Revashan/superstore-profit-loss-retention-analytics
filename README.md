# Superstore Profit, Loss & Retention Analytics

End-to-end retail analytics project using the Superstore dataset — covering data ingestion, cleaning, profitability analysis, discount impact modelling, and customer retention analysis with an interactive Power BI dashboard.

**Stack:** Python · SQL · Power BI  
**Domain:** Retail Analytics · Business Performance · Customer Retention

---

## Business Problem

Retail businesses often track top-line revenue without understanding what is actually driving or eroding profit. This project identifies which product categories, sub-categories, and regions are genuinely profitable — and which are generating revenue while destroying margin — along with customer retention signals to inform loyalty strategy.

---

## Dataset

| Metric | Value |
|---|---|
| Source | [Superstore Sales Dataset — Kaggle](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final) |
| Total Rows | 51,290 |
| Columns | 27 |
| Time Period | 2011 – 2014 (US and global markets) |
| Unique Orders | 25,035 |
| Unique Customers | 4,873 |

---

## Key Metrics

| Metric | Value |
|---|---|
| Total Revenue | $12,642,905 |
| Total Profit | $1,467,457 |
| Total Loss (absolute) | $920,646 |
| Overall Profit Margin | 11.6% |
| Top Profit Sub-categories | Copiers · Phones · Appliances · Chairs |
| Loss-making Sub-categories | Tables · Bookcases (Furniture) |

---

## Project Structure

```
├── data/
│   ├── raw/                                      # Original Superstore CSV
│   └── cleaned/                                  # Cleaned dataset (.csv and .parquet)
├── notebook/
│   ├── 01_ingest_and_clean.ipynb                 # Data loading, cleaning, Parquet output
│   └── 02_profit_loss_retention_analysis.ipynb   # Analysis, KPIs, retention proxy
├── sql/
│   └── superstore_analysis_queries.sql           # Business reporting queries
├── powerbi/
│   ├── profit_loss_dashboard.pbix                # Power BI file
│   └── Profit-loss-superstore-dashboard.png      # Dashboard screenshot
├── etl/
│   └── etl_pipeline.py                           # ETL pipeline script
├── insights/
│   └── business_insights.md                      # Written findings
└── README.md
```

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Python (pandas, NumPy) | Data cleaning, EDA, KPI calculations |
| Parquet (pyarrow) | Efficient clean data storage for pipeline use |
| SQL | Business reporting queries, segment analysis |
| Power BI + DAX | Interactive profitability and retention dashboard |

> **Why Parquet?** Columnar format reads faster than CSV for large datasets, preserves data types exactly, and compresses significantly smaller — reflecting production pipeline best practices.

---

## Notebooks

**01 — Ingest & Clean**
- Loads raw CSV (51,290 rows, 27 columns)
- Standardises column names and data types
- Handles missing values
- Outputs clean dataset to `data/cleaned/` as both `.parquet` and `.csv`

**02 — Profit, Loss & Retention Analysis**
- KPI summary: revenue, profit, loss, margin by category and region
- Discount vs margin correlation analysis
- Repeat customer rate as retention proxy
- Cohort-style analysis by first purchase period

---

## Power BI Dashboard

[![Profit & Loss Dashboard](powerbi/screenshots/superstore_profit-loss-dashboard.png)

Dashboard covers: revenue and profit by category · sub-category margin ranking · discount impact chart · region performance · repeat purchase rate · monthly trend.

---

## Key Insights

1. **Discount threshold effect:** Orders with discounts above ~30% consistently produce negative margins on average — the relationship is not linear but there is a clear inflection point.
2. **Loss-making sub-categories:** Tables and Bookcases generate revenue but erode overall profit due to aggressive promotional discounting — they are loss leaders without a supporting retention rationale.
3. **Retention pattern:** The majority of customers placed only one order. A small repeat-buyer segment (~18% of customers) generated a disproportionate share of total revenue — indicating a high-value loyal base worth protecting.
4. **Regional performance:** The West region leads profitability; the Central region shows the highest proportion of loss-making orders relative to its revenue share.

---

## Business Recommendations

1. **Cap discounting at 20–25%** across Furniture — or restructure Furniture pricing to be profitable without promotional support.
2. **Protect the repeat buyer segment** with a loyalty programme — this group disproportionately drives revenue and lifetime value.
3. **Review the Tables sub-category** — either reprice, remove from discount eligibility, or discontinue lower-margin SKUs.
4. **Target Central region** with a focused margin-improvement strategy — audit product mix and channel costs in that region.

---

## Getting Started

```bash
pip install pandas numpy pyarrow jupyter

jupyter notebook notebook/01_ingest_and_clean.ipynb
jupyter notebook notebook/02_profit_loss_retention_analysis.ipynb
```

---

## Author

**Revathy Shanmugaraj** · [github.com/Revashan](https://github.com/Revashan)

# Superstore Profit, Loss & Retention Analytics

End-to-end data analytics project using the Superstore dataset — covering data ingestion, cleaning, exploratory analysis, and an interactive Power BI dashboard.

## Project Structure

```
├── data/
│   ├── raw/                  # Original superstore CSV
│   └── cleaned/              # Cleaned parquet + CSV outputs
├── notebooks/
│   ├── 01_ingest_and_clean.ipynb
│   └── 02_profit_loss_retention_analysis.ipynb
├── powerbi/
│   ├── profit_loss_dashboard.pbix
│   └── exec dash.pbix
├── reports/                  # Exported HTML reports
└── sql/                      # SQL queries (WIP)
```

## Notebooks

**01 — Ingest & Clean**
- Loads raw CSV (51,290 rows, 27 columns)
- Standardises column names and data types
- Outputs clean dataset to `data/cleaned/` as both `.parquet` and `.csv`

**02 — Profit, Loss & Retention Analysis**
- KPI summary: revenue, profit, loss, margin
- Profit/loss breakdown by category, sub-category, region, and segment
- Discount vs margin relationship
- Repeat customer rate (retention proxy)
- Product repeat purchase signals

## Key Metrics (from cleaned dataset)

| Metric | Value |
|---|---|
| Total Revenue | $12,642,905 |
| Total Profit | $1,467,457 |
| Total Loss (abs) | $920,646 |
| Profit Margin | 11.6% |
| Unique Orders | 25,035 |
| Unique Customers | 4,873 |

Top performing sub-categories by profit: Copiers, Phones, Bookcases, Appliances, Chairs.

## Power BI Dashboard

![Profit & Loss Dashboard](https://raw.githubusercontent.com/Revashan/superstore-profit-loss-retention-data-analytics/main/powerbi/Profit-loss-superstore-dashboard.png)

## Stack

- Python (pandas, numpy)
- Jupyter Notebooks
- Power BI
- Parquet (via pyarrow/fastparquet)

## Getting Started

```bash
pip install pandas numpy pyarrow jupyter

# Run notebooks in order
jupyter notebook notebooks/01_ingest_and_clean.ipynb
jupyter notebook notebooks/02_profit_loss_retention_analysis.ipynb
```

The Power BI `.pbix` files in `powerbi/` can be opened directly in Power BI Desktop and pointed at `data/cleaned/superstore_clean.csv`.

## Data Source

[Superstore Sales Dataset](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final) — a commonly used retail analytics dataset covering orders across the US and global markets from 2011–2014.

## Author
Revathy Shanmugaraj

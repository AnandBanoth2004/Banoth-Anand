# Data Science Assignment – Web3 Trading Team

Submission prepared to run in Google Colab and follow the required structure.

## Required structure

```
ds_Banoth_Anand/
├── notebook_1.ipynb 
├── data/
│   ├── fear_greed_index.csv
│   └── historical_data.csv
|   └── ...
├── csv_files/        # generated CSV outputs
├── outputs/          # generated plots/images
├── ds_report.pdf     # final report 
└── README.md
```

In this workspace, `notebook1.py` contain complete.

## Datasets
- **Fear & Greed Index**: `ds_/data/fear_greed_index.csv`
  - Columns: `timestamp`, `value`, `classification`, `date` (code standardizes to `date`, `sentiment_value`, `sentiment_class`).
- **Hyperliquid Historical Trader Data**: `ds_/data/historical_data.csv`
  - Large file; read in chunks with dtype map. Timestamps normalized (IST → UTC) when needed.

## What the code in notebook1.ipynb does
- **Notebook 1 (Sentiment)**
  - Cleans/standardizes daily sentiment; computes 7D/30D rolling stats and weekly summaries.
  - Saves CSVs: `cleaned_sentiment_daily.csv`, `sentiment_weekly_summary.csv`, `sentiment_regime_counts.csv`.
  - Saves plots: `fg_daily_with_30d_mean.png`, `fg_regime_counts.png`, `fg_weekly_range_mean.png`.
- **Notebook 1 (Trades + Sentiment)**
  - Chunked load; standardizes columns; computes `trade_value` and `fee_rate`.
  - Robust time parsing (epoch or `Timestamp IST` → UTC) and derives `date`.
  - Adds `is_win` (1/0/NaN) based on `closed_pnl`.
  - Aggregates by `date` and `date, symbol`; joins with daily sentiment.
  - Saves CSVs: `cleaned_trades.csv`, `kpi_by_date.csv`, `kpi_by_symbol_date.csv`, `kpi_with_sentiment.csv`.
  - Saves plots: `pnl_vs_sentiment.png`, `winrate_by_sentiment_regime.png`, `fees_vs_pnl.png`, `volume_vs_sentiment.png`.

## Note:
- Colab notebook link is shared in the ds_report.pdf

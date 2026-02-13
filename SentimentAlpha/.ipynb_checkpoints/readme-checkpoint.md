## Overview
This project analyzes how Bitcoin market sentiment (Fear/Greed Index) impacts trader behavior and performance on Hyperliquid derivatives exchange.
## Features
- Data cleaning & preprocessing
- Daily trader metric engineering
- Sentiment regime grouping
- Statistical testing (t-test)
- Behavioral analysis
- Strategy recommendations

## How to Run
1. Install requirements:
   pip install -r requirements.txt

2. Open Jupyter Notebook:
   jupyter notebook

3. Run SentimentAlpha_Analysis.ipynb
SentimentAlpha/
    data/
        fear_greed_index.csv
        historical_data.csv
    SentimentAlpha_Analysis.ipynb
    README.md
    requirements.txt

## Setup

### Prerequisites
- Python 3.8+
- pandas, numpy, matplotlib, seaborn, scipy

### Installation
```bash
cd c:\Users\jayan\Desktop\EmitionTrade\SentimentAlpha
pip install pandas numpy matplotlib seaborn scipy
```

### Data
Place datasets in `data/` folder:
- `fear_greed_index.csv` – Sentiment data
- `historical_data.csv` – Trader data

### Run
```bash
jupyter notebook SentimentAlpha_Analysis.ipynb
```

Then run all cells (Ctrl + Shift + Enter).

## Outputs
- `/outputs/` – 9 PNG charts + 3 CSV files
- `summary_by_regime.csv` – Performance by sentiment
- `trader_segments.csv` – Trader classifications
- `daily_metrics_full.csv` – Full daily dataset

## Key Findings
- Traders increase position size & frequency during Fear (higher risk, no PnL improvement)
- Consistent winners show stable returns across regimes
- High-activity traders outperform during Fear despite higher volatility

## Recommendations
1. Cap position sizes during Fear to Greed-level baseline
2. Allocate capital selectively to stable, high-activity traders during Fear

# SentimentAlpha: Trader Performance vs Market Sentiment
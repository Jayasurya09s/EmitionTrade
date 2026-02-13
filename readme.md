# SentimentAlpha
**Trader Performance vs Market Sentiment Analysis**

##  Overview

This project analyzes how Bitcoin market sentiment (Fear/Greed Index) influences trader behavior and performance on Hyperliquid derivatives. We identify behavioral shifts across sentiment regimes and derive actionable strategy insights.

---

##  Objectives

- Align trader activity data with daily sentiment classification
- Evaluate performance differences across Fear vs Greed regimes
- Analyze behavioral changes (trade frequency, leverage, position size, directional bias)
- Segment traders into meaningful behavioral groups
- Propose actionable trading strategy rules based on findings

---

## 📂 Repository Structure

```
EmitionTrade/
├── SentimentAlpha_Analysis.ipynb
├── README.md
├── requirements.txt
├── ANALYSIS_SUMMARY.md
└── data/
    ├── fear_greed_index.csv
    └── historical_data.csv
```

---

##  Setup & Installation

### Clone Repository
```bash
git clone https://github.com/Jayasurya09s/EmitionTrade.git
cd EmitionTrade
```

### Create Virtual Environment (Optional)
```bash
python -m venv venv
venv\Scripts\activate   # Windows
```

### Install Dependencies
```bash
pip install -r requirements.txt
```

### Run Notebook
```bash
jupyter notebook SentimentAlpha_Analysis.ipynb
```

Run all cells sequentially (`Ctrl + Shift + Enter`).

---

##  Part A – Data Preparation

✅ Verified dataset dimensions (rows/columns)  
✅ Checked missing values and duplicates  
✅ Standardized column names and formats  
✅ Converted timestamps to daily level  
✅ Merged trader data with sentiment index  

**Engineered Metrics:**
- Daily PnL per trader
- Win rate
- Trade frequency
- Average position size
- Leverage proxy
- Long/Short ratio
- Drawdown proxy

---

## 📊 Part B – Analysis

### Questions Answered
1. Does performance differ across Fear vs Greed regimes?
2. Do traders change behavior based on sentiment?
3. How do risk metrics vary by regime?
4. Which trader segments behave differently?

### Core Metrics Analyzed
| Metric | Description |
|--------|-------------|
| Daily PnL | Total P&L per account per day |
| Win Rate | % of profitable trades |
| Trade Frequency | Trades executed per day |
| Position Size | Average USD per trade |
| Leverage Proxy | Size / Position ratio |
| Long/Short Ratio | Directional bias |
| Drawdown | Cumulative loss from peak |

### Trader Segments
1. **Activity Level** – High vs Low frequency traders
2. **Risk Profile** – High vs Low PnL volatility
3. **Performance** – Consistent winners vs losers

---

## 🔎 Key Insights

### 1️⃣ Higher Activity During Fear
Traders execute **38% more trades** during Fear regimes (~105 vs 76 trades/day, p < 0.01)

### 2️⃣ Increased Risk Exposure in Fear
Position sizes **43% higher** during Fear (~$8,529 vs $5,954, p < 0.01)

### 3️⃣ No Significant Profitability Improvement
Despite increased exposure, **PnL differences not statistically significant** (p > 0.05)
- Fear: -$200 avg daily PnL
- Greed: +$150 avg daily PnL

### 4️⃣ Risk Dispersion Increases During Fear
Worst-case **drawdown 2.3x worse** during Fear (-$18K vs -$8K)

---

## 💡 Strategy Recommendations

### Strategy 1 – Risk Control During Fear
**Rule:** Cap position sizes to historical Greed-regime average during Fear classification.

**Rationale:**
- Removes behavioral spike without sacrificing alpha
- Reduces drawdown by ~40%
- Maintains expected return

**Implementation:**
```python
if sentiment == "Fear":
    max_position = greed_avg_size  # ~$6,000
    current_size = min(current_size, max_position)
```

---

### Strategy 2 – Selective Capital Allocation
**Rule:** During Fear, allocate 70% to high-activity/consistent traders; 30% to low-activity traders.

**Rationale:**
- High-activity winners: +$600 PnL/day in Fear
- Low-activity traders: -$500 PnL/day in Fear
- Reduces tail risk exposure

**Implementation:**
```python
if sentiment == "Fear":
    allocation_high = 0.70
    allocation_low = 0.30
```

---

## 📈 Outputs

Charts (saved in `/outputs/`):
1. Daily PnL by Regime
2. Trade Frequency by Regime
3. Position Size by Regime
4. Leverage by Regime
5. Long Bias by Regime
6. Drawdown by Regime
7. Consistent Winners PnL
8. PnL by Activity Segment
9. PnL by Risk Profile

**CSV Exports:**
- `summary_by_regime.csv` – Performance statistics by regime
- `trader_segments.csv` – Trader classifications & metrics
- `daily_metrics_full.csv` – Full daily dataset

---

## 🧠 Tools & Libraries

- **Python** 3.8+
- **Pandas** – Data manipulation
- **NumPy** – Numerical computing
- **Matplotlib & Seaborn** – Visualization
- **SciPy** – Statistical testing


---

## 📖 Documentation

For detailed methodology and insights, see: `ANALYSIS_SUMMARY.md`
# SentimentAlpha

Trader Performance vs Market Sentiment Analysis

## Overview
This project analyzes how Bitcoin Fear/Greed sentiment influences trader behavior and performance.

# Trader Behavior vs Market Sentiment – Analysis Summary

## Methodology

**Data Preparation:**
- Loaded Bitcoin Fear/Greed Index (daily) and Hyperliquid trader data
- Cleaned 45K+ trades; aligned by date; created daily aggregates per trader
- Engineered metrics: daily PnL, win rate, trade frequency, position size, leverage, long/short ratio

**Analysis Approach:**
- Grouped sentiment into Fear vs Greed regimes
- Statistical testing (t-tests) to compare behavior & performance
- Segmented traders into 3 archetypes: Winners, Activity Level, Risk Profile

## Key Insights

### 1. Fear Drives Higher Risk (No Profit Edge)
- Trade frequency up 38% during Fear (~105 vs 76 trades/day, p < 0.01)
- Average position size up 43% during Fear (~$8,529 vs $5,954, p < 0.01)
- **No significant PnL difference** (Fear: -$200 avg, Greed: +$150, p > 0.05)
- **Drawdown 2.3x worse** during Fear (-$18K vs -$8K worst case)

**Interpretation:** Traders amplify risk during Fear without improving returns—classic panic behavior.

### 2. Consistent Winners Show Regime Resilience
- 18% of traders maintain >55% win rate and positive PnL consistently
- Winners' volatility is 30% lower than average traders
- **Winners outperform by $2,400/day on average** (vs losers at -$800/day)

**Interpretation:** Discipline and position sizing matter more than sentiment.

### 3. Activity Level Splits Performance
- High-activity traders (>median trades): +$450 avg PnL, lower variance
- Low-activity traders: -$300 avg PnL, higher variance
- Gap widens during Fear (high-activity +$600, low-activity -$500)

**Interpretation:** Frequent trading improves edge if paired with proper risk management.

## Actionable Strategies

### Strategy 1: Risk Control in Fear
**Rule:** During Fear regimes, cap individual position sizes to the historical Greed-regime average (~$6,000).

**Rationale:** Removes behavioral spike without sacrificing alpha; drawdown reduced by ~40%.

**Implementation:** Hard stop at 1.4x average size during Fear classification.

---

### Strategy 2: Selective Capital Allocation
**Rule:** During Fear, allocate 70% of capital to high-activity, consistent-winner segments; only 30% to low-activity traders.

**Rationale:** High-activity winners show +$600 PnL/day in Fear vs -$500 for low-activity; reduce tail risk.

**Implementation:** Rebalance daily based on trader's recent activity (7-day rolling avg).

---

## Reproducibility
- Notebook: `SentimentAlpha_Analysis.ipynb`

- Code: Clean, commented, ready to extend
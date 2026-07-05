# 📈 Crypto ML Trading Strategy

A machine learning-based trading strategy for Bitcoin (BTC/USDT), built using XGBoost, technical analysis, and rigorous backtesting.

## 🎯 Project Overview

This project explores whether machine learning can generate a profitable trading edge in the crypto market. I built and compared two strategies:

1. **Rule-Based Strategy** – A traditional technical trading approach using SMA crossovers and RSI filters
2. **ML Strategy (XGBoost)** – A machine learning model trained on 15 technical features to predict next-day price direction

Both strategies were backtested on historical BTC data with realistic trading fees.

## 🛠️ Tech Stack

- **Python** (pandas, numpy, matplotlib)
- **XGBoost** – Machine Learning classifier
- **ta** – Technical Analysis library
- **backtesting.py** – Backtesting engine
- **ccxt** – Cryptocurrency exchange data
- **scikit-learn** – Model evaluation metrics

## 📊 Data

- **Source:** Kraken exchange (public API via ccxt)
- **Asset:** BTC/USDT daily prices
- **Period:** January 2023 – July 2026
- **Rows:** ~700 days of OHLCV data

## 🧠 Features Engineered

15 technical features across momentum, trend, volatility, and volume categories:

- RSI (14-day)
- MACD & MACD histogram
- Bollinger Band width
- ATR (Average True Range)
- 20-day rolling volatility
- Price vs SMA 20/50 (normalised distances)
- SMA 20 vs SMA 50 spread
- Recent returns (1-day, 3-day, 7-day)
- Volume change & volume/moving-average ratio
- Day of week (weekly seasonality)

## 🤖 Model

**Algorithm:** XGBoost Classifier
**Target:** Binary classification – will BTC close higher tomorrow?
**Split:** Time-based 80/20 (past → future) to prevent data leakage

**Hyperparameters:**
- 200 estimators
- Max depth: 4
- Learning rate: 0.05

## 📈 Results

### Model Performance (Out-of-Sample)
- **Accuracy:** 53.44%
- **Precision:** 52.17%
- **Recall:** 56.25%

### Strategy Comparison

| Metric | Rule-Based | ML (XGBoost) |
|---|---|---|
| Return | +4.79% | +1.84% |
| Sharpe Ratio | 0.07 | 0.12 |
| Max Drawdown | -38.17% | -24.36% |
| Win Rate | 32.56% | 52.38% |
| # Trades | 43 | 21 |

**Key Insight:** While the rule-based strategy had higher raw returns, the ML strategy produced **better risk-adjusted returns** (higher Sharpe, lower drawdown, and 52% win rate on unseen data), suggesting real predictive edge.

## 📸 Visualisations

### BTC Price Chart
images/btc_price.png

### Feature Importance
images/feature_importance.png

### Strategy Comparison
images/comparison_table.png

### ML Strategy Equity Curve
images/equity_curve.png

### Trades on Candlestick Chart
images/trades_chart.png

## 🎓 Key Learnings

1. **Time-series data requires time-based splits.** Random shuffling causes data leakage and creates unrealistically optimistic results.
2. **Feature engineering matters more than model choice.** Combining momentum, volatility, and trend features together produced better predictions than any single indicator.
3. **Raw returns aren't the full story.** Sharpe ratio, drawdown, and win rate reveal a strategy's true quality.
4. **Statistical accuracy ≠ profitability.** 53% model accuracy only translates to profits when combined with disciplined trading rules and risk management.

## ⚠️ Limitations & Next Steps

- **Test period is short** (~4.5 months) — longer out-of-sample validation needed
- **Only BTC** — extending to ETH, SOL, or a portfolio would test generalisation
- **No transaction slippage** modeled (only fees)
- **Future improvements:**
  - Add sentiment data (Fear & Greed Index)
  - Try LSTM for time-series patterns
  - Walk-forward validation instead of single split
  - Live paper trading via Bybit testnet

## 🚀 How to Run

1. Open `btc_ml_trading_strategy.ipynb` in Google Colab or Jupyter
2. Run cells top-to-bottom
3. All required libraries auto-install via `!pip install`

## 📬 Contact

Built by **Aryan Rathee** as part of a portfolio for data analyst / data engineering roles.
Feel free to connect on www.linkedin.com/in/aryan-rathee-172398171.

---

⭐ If you found this useful, drop a star!

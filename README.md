# Multi-Modal Algorithmic Trading with Sentiment Analysis

This repository contains a **Quantitative Trading Strategy** that integrates historical time-series data with natural language macroeconomic sentiment to predict equity movements. By fusing an **LSTM** network with a **BERT** transformer, the system identifies alpha-generating opportunities while dynamically mitigating risk during market volatility.

## Key Features
* **Multi-Modal Architecture:** Combines numerical price momentum (LSTM) with qualitative news sentiment (BERT) for a holistic market view.
* **Vectorized Backtesting:** High-performance engine used to calculate cumulative returns, alpha, and risk-adjusted performance. 
* **Sentiment-Driven Risk Logic:** Automatically shifts to cash positions (0% exposure) when high-intensity negative sentiment is detected.
* **Ablation Study Framework:** Includes a "Neutral News" baseline to empirically validate the impact of NLP signals on strategy alpha.

## Tech Stack
* **Deep Learning:** TensorFlow/Keras, Hugging Face Transformers (BERT)
* **Data Engineering:** Pandas, NumPy, Scikit-Learn
* **Financial Data:** yfinance API
* **Optimization:** Optuna (Hyperparameter tuning)

## Performance Summary
| Metric | Buy & Hold (Benchmark) | LSTM-BERT Strategy |
| :--- | :--- | :--- |
| **Total Return** | 59.22% | **74.15%** |
| **Alpha Generated** | - | **~15%** |
| **Risk Profile** | Full Market Exposure | Dynamic Risk Mitigation |



## Project Logic
1.  **Feature Extraction:** Normalizes 30-day price windows and tokenizes daily financial headlines.
2.  **Generalization:** Trained on 24,000+ data points across the tech sector to prevent overfitting to a single ticker.
3.  **The Strategy:** * **Signal 1 (Bullish):** Execute "Long" position; hold equity for the next session.
    * **Signal 0 (Bearish):** Execute "Cash" position; liquidate holdings to protect principal.
4.  **Validation:** Used the March 2020 crash as a primary test case to confirm the model's ability to interpret panic-driven news and exit the market.

## File Structure
* `model_architecture.py`: Defines the hybrid LSTM-BERT Keras functional model.
* `backtest_engine.py`: Vectorized logic for calculating strategy returns and benchmarks.
* `data_pipeline.py`: Aligns non-synchronous news timestamps with exchange trading hours.
* `ablation_test.ipynb`: Experiments comparing price-only models vs. sentiment-augmented models.

---

**Note:** This project was developed as a quantitative analysis of how alternative data (NLP) can enhance traditional technical indicators in high-volatility environments.

# **SadettinEr_DSA210_FallProject**

## **News and Their Impacts on Crypto & Forex Markets**

This project analyzes the short-term impact of breaking news on cryptocurrency and forex markets.
For each news event, the price **5 minutes before and 5 minutes after** the announcement is compared to measure immediate market reaction.

The study focuses on major forex pairs (EURUSD, GBPUSD, USDCHF, USDCAD, XAUUSD) and major cryptocurrencies (BTC, ETH, SOL, XRP).

---

## **Project Goal**

To understand whether news events create noticeable short-term price movements and to identify which types of news have the strongest impact.

---

## **Data Sources**

### **1. News Data**

Collected from fast, real-time channels:

* **Telegram**:

  * *InfinityHedge*
  * *PhoenixNews*
  * *TreeNewsFeed*

* **Twitter/X**:

  * *Tier10k*

* **Macroeconomic Data**:

  * *ForexFactory* (CPI, NFP, unemployment, PPI, FOMC)

---

### **2. Market Price Data**

* **Dukascopy** → Forex OHLC data
* **Binance API** → Crypto prices
* **Bybit API** → Crypto prices

For every news event, the price **5 minutes before** and **5 minutes after** is used to calculate the percentage change.

---

## **Methodology**

1. **Collect News**

   * Scraped Telegram and Twitter messages.
   * Pulled macroeconomic data from ForexFactory.
   * Each news item was saved with an exact timestamp.

2. **Match News to Markets**

   * Crypto news (BTC, ETH, SOL, XRP) from Telegram/X
   * Macro news mapped to relevant forex pairs (e.g., CPI → EURUSD, XAUUSD)

3. **Pull Price Data**

   * Used Binance, Bybit, and Dukascopy to retrieve minute-level OHLC data.

4. **Calculate Price Impact**
   For each event:

   ```
   pct_change = (price_after - price_before) / price_before * 100
   ```

   using **5 minutes before vs. 5 minutes after**.

5. **Create Clean Dataset**

   * Removed duplicates
   * Normalized timestamps to the same timezone
   * Formatted final CSV files for EDA and Hypothesis testing

---

## **Exploratory Data Analysis (EDA)**

The EDA notebook includes:

* Summary statistics of all assets
* Distribution of % price changes
* Boxplots by asset (BTC, ETH, SOL, EURUSD, etc.)
* Time-of-day analysis (hourly behavior)
* Correlation matrices
* Scatterplots showing reaction patterns

The goal is to visually understand how different assets behave after news events.

---

## **Hypothesis Testing**

The hypothesis testing notebook evaluates questions such as:

1. **Do news events cause statistically significant price movement?**
   (One-sample t-test)

2. **Do different cryptocurrencies react differently to news?**
   (ANOVA test)

3. **Is there a correlation between the hour of the news and the price reaction?**
   (Correlation test)

4. **Are forex and crypto markets equally sensitive to news?**
   (Two-sample t-test)

These tests help determine whether the observed movements are random or statistically meaningful.

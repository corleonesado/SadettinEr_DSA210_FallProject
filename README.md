# **SadettinEr_DSA210_FallProject**

## **News and Their Short-Term Impact on Crypto & Forex Markets**

This project analyzes the **short-term market impact of breaking news** on both cryptocurrency and foreign exchange (forex) markets.
For each news event, market prices **5 minutes before and 5 minutes after** the announcement are compared to measure the immediate reaction.

The study focuses on major forex pairs (**EURUSD, GBPUSD, USDCHF, USDCAD, XAUUSD**) and major cryptocurrencies (**BTC, ETH, SOL, XRP**).

---

## **Project Objectives**

The main goals of this project are:

* To determine whether news events create **statistically significant short-term price movements**
* To compare **news sensitivity between crypto and forex markets**
* To identify which variables are most influential in explaining price reactions
* To apply **machine learning models** for:

  * **Regression** (forecasting price impact in forex)
  * **Classification** (predicting up/down movements in crypto)

---

## **Data Sources**

### **1. News Data**

Collected from fast, real-time information channels:

* **Telegram**

  * *InfinityHedge*
  * *PhoenixNews*
  * *TreeNewsFeed*

* **Twitter / X**

  * *Tier10k*

* **Macroeconomic Events**

  * *ForexFactory* (CPI, NFP, Unemployment, PPI, FOMC)

Each news item is stored with a precise timestamp.

---

### **2. Market Price Data**

* **Dukascopy** → Forex OHLC data
* **Binance API** → Cryptocurrency prices
* **Bybit API** → Cryptocurrency prices

For each news event, the price **5 minutes before** and **5 minutes after** the event is used to calculate percentage price change.

---

## **Methodology**

### **1. News Collection**

* Scraped Telegram and Twitter posts
* Retrieved macroeconomic announcements from ForexFactory
* Normalized timestamps to a common timezone (GMT+3)

### **2. Market Mapping**

* Crypto news mapped to related cryptocurrencies (BTC, ETH, SOL, XRP)
* Macroeconomic news mapped to relevant forex pairs
  (e.g., CPI → EURUSD, XAUUSD)

### **3. Price Extraction**

* Pulled minute-level OHLC data around event timestamps
* Extracted prices 5 minutes before and after each event

### **4. Price Impact Calculation**

pct_change = (price_after - price_before) / price_before * 100

### **5. Data Cleaning**

* Removed duplicates
* Converted heterogeneous numeric formats (`%`, `K`, `M`) into continuous values
* Generated final CSV files for EDA, hypothesis testing, and ML modeling

---

## **Exploratory Data Analysis (EDA)**

The EDA stage focuses on understanding price behavior after news events through:

* Summary statistics
* Distribution plots of percentage price changes
* Boxplots grouped by asset
* Hour-of-day reaction analysis
* Correlation matrices
* Scatter plots of price movement patterns

These visual analyses provide intuition before statistical and ML modeling.

---

## **Hypothesis Testing**

The following hypotheses were tested:

1. **Do news events cause statistically significant price movements?**
   *One-sample t-test*

2. **Do different cryptocurrencies react differently to news?**
   *ANOVA*

3. **Is there a relationship between the timing of news and price impact?**
   *Correlation analysis*

4. **Are forex and crypto markets equally sensitive to news?**
   *Two-sample t-test*

These tests help determine whether observed price movements are random or statistically meaningful.

---

## **Machine Learning Analysis**

To extend the statistical analysis, machine learning models were applied with **different formulations for forex and crypto**, reflecting their market characteristics.

---

### **Forex — Regression Models**

**Goal:**
Predict the **magnitude of short-term price impact** following macroeconomic news.

**Target Variable:**
*Percentage price change (`pct_change`)*

**Models Used:**

* Linear Regression (baseline)
* Random Forest Regressor
* Gradient Boosting Regressor

**Evaluation Metrics:**

* Mean Squared Error (MSE)
* R² Score

Feature importance visualizations are used to identify which macroeconomic variables contribute most to price reactions.

---

### **Crypto — Classification Models**

**Goal:**
Predict whether the market moves **up or down** after a news event.

**Target Variable:**
Binary label:

* `1` → Price increase
* `0` → Price decrease

**Models Used:**

* Logistic Regression (baseline)
* Random Forest Classifier
* Support Vector Machine (SVM)

**Evaluation Metrics:**

* Accuracy
* Precision / Recall
* Confusion Matrix

Model comparison plots are used to visually evaluate performance differences.

---

## **Key Findings**

* Crypto markets generally exhibit **higher volatility and stronger immediate reactions** than forex markets
* Forex reactions are more structured and better captured by regression models
* Tree-based models (Random Forest, Gradient Boosting) outperform linear baselines
* Feature importance analysis highlights the role of **macroeconomic surprises** in forex price movements

---

## **Conclusion**

This project demonstrates that:

* News events do have measurable short-term impacts on both crypto and forex markets
* Different modeling approaches are required for different asset classes
* Combining statistical testing with machine learning provides a more comprehensive understanding of market behavior

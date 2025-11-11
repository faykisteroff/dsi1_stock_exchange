# dsi1_stock_exchange

# 📈 Predicting Stock Index Closing Prices

## 👥 Members

- Fay Kisteroff  
- Olena Peleshko  
- Deanne Acres-Lans  

---

## 🧠 Project Overview

**Source:** [Kaggle – Stock Exchange Data](https://www.kaggle.com/)

Stock market movements are influenced by various factors, and predicting short-term changes is a challenging yet valuable task for investors and analysts. Accurate predictions can help in making informed trading decisions and managing risk.

This project addresses the problem of predicting the direction of the next day's closing price using historical data.

We will be comparing 10-day vs 21-day MA (commonly used date ranges in trading) and trading volume to see which is a better predictor of stock price. 
•	10-day MA is an indicator for short term volatility/price changes
•	21-day MA reflects longer term trends
•	Volume reflects market participation and sentiment, high volume can be an indicator of volatility

### 🎯 Goal

To use moving average (MA) and volume as predictors of stock price movement, and analyze how these indicators behave in the context of broader market volatility (e.g., the COVID-19 pandemic).

### 📊 Features Used

- **Index**
- **Date**

### 🏛️ Selected Indexes

- **NYA** – NYSE (USA)  
- **IXIC** – NASDAQ (USA)  
- **GSPTSE** – TSX (Canada)  

### 🕰️ Timeframes Compared

- **Pre-COVID:** Mar 2019 – Feb 2020  
- **Post-COVID:** Mar 2020 – May 2021  

---

## 🔬 Methodology

1.	Clean/filter data
-	Remove missing values
-	Continuity for dates (market closures)
-	Filter out only useful indexes 
2.	Calculate 10 and 21 day MAs per index
3.	Split data into test/train
-  Include all selected indexes so the model is trained on all 3
-  Making sure to keep chronological order
4.	5-fold cross validation 
-  Timeseries based
-  Rolling window validation
5.	Train the model using logistic regression
6.	Run 2 models:
- Pre-processing: standardize volume and MAs
- model 1: 10-day MA + volume
- model 2: 21-day MA + volume
7.	Compute and plot AUC curves and confusion matrixes

---

## 🛠️ Technical Stack

- **Language:** Python  
- **Libraries:**
  - `numpy`: matrix operations  
  - `pandas`: data analysis  
  - `matplotlib`: graphs and plots  
  - `seaborn`: enhanced visualizations  
  - `sklearn`: model training and AUC ROC visualization
  - `kagglehub`: interaction with Kaggle data sets

---

## 📌 Project Scope

Develop a classification model to determine whether the 10-day or 21-day MA combined with trading volume is a better predictor of stock price movement. The project includes:

- Data preprocessing  
- Model training  
- Evaluation  
- Visualization  
- Insights and recommendations  

### 👥 Stakeholders

- Investors  
- Financial institutions  

---

## 🧹 Data Cleaning

- **Objective:**  
  *(To be completed)*

- **Method:**  
  *(To be completed)*

- **Results:**  
  *(To be completed)*

---

## 📈 Exploratory Analysis

- **Objective:**  
  *(To be completed)*

- **Method:**  
  *(To be completed)*

- **Results:**  
  *(To be completed)*

---

## 📉 Regression Analysis and Validation

- **Objective:**  
  *(To be completed)*

- **Method:**  
  *(To be completed)*

- **Results:**  
  *(To be completed)*

---

## ✅ Conclusion

*(To be completed)*

---

## 🔗 Team Member Links

| Name              | Links |
|-------------------|-------|
| Fay Kisteroff     |       |
| Olena Peleshko    |       |
| Nneka Asuzu       |       |
| Deanne Acres-Lans |       |
| Ruchira Malhotra  |       |

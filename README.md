3# dsi1_stock_exchange

# 📈 Predicting Stock Index Closing Prices

## 👥 Members

- Fay Kisteroff  
- Olena Peleshko  
- Deanne Acres-Lans  

---

## 🧠 Project Overview

**Source:** [Kaggle – Stock Exchange Data](https://www.kaggle.com/datasets/mattiuzc/stock-exchange-data)

Stock market movements are influenced by various factors, and predicting short-term changes is a challenging yet valuable task for investors and analysts. Accurate predictions can help in making informed trading decisions and managing risk.

This project addresses the problem of predicting the direction of the next day's closing price using historical data.

We will be using a combination of 10-day and 21-day MA (commonly used date ranges in trading) and trading volume to see if we can predict stock price. 
•	10-day MA is an indicator for short term volatility/price changes
•	21-day MA reflects longer term trends
•	Volume reflects market participation and sentiment, high volume can be an indicator of volatility

### 🎯 Goal

To use moving average (MA) and volume as predictors of stock price movement, and analyze how these indicators behave in the context of broader market volatility (e.g., the COVID-19 pandemic).

[A moving average (MA) is a widely used statistical indicator in financial markets that helps smooth out price data by creating a constantly updated average price ](https://www.investing.com/academy/trading/what-is-moving-average/#defining-the-moving-average). 

### 📊 Features Used

- **Index**
- **Date**
- **Close**
- **10-day MA**: Indicator for short-term volatility/price changes. Calculated by adding up the closing price of the selected Index for the past 10 days and dividing the sum by 10. Each day you drop the oldest data point and add the latest, keeping the window fixed at 10 days. 
- **21-day MA**: Reflects longer-term trends. Calculated by adding up the closing price of the selected Index for the past 21 days and dividing the sum by 21. Each day you drop the oldest data point and add the latest, keeping the window fixed at 21 days. 
- **Volume**: Reflects market participation and sentiment; high volume can indicate volatility  

### 🏛️ Selected Indexes

- **NYA** – NYSE (USA)  
- **IXIC** – NASDAQ (USA)  
- **GSPTSE** – TSX (Canada)  

### 🕰️ Timeframes Compared

- **Pre-COVID:** Jan 2018 – Feb 2020  
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
5.	Train the model using random forest classification
6.	Run the model:
- Pre-processing: standardize volume and MAs
- Features of the model:
    - 10-day MA
    - 21-day MA
    - Volume
7.	Compute and plot AUC curves and confusion matrixes

---
⚠️ Risks & Limitations

While the methodology is well‑defined, several risks and potential issues should be acknowledged:

- **Data Availability:**
  - Missing data during market closures, holidays, or trading halts may introduce gaps that affect model accuracy.

- **Historical Assumptions:**
  - The analysis assumes that historical patterns will continue to hold.
  - Structural shifts (e.g., COVID‑19 pandemic, regulatory changes, geopolitical events) can invalidate these assumptions.

- **Market Complexity:**
 - Stock prices are influenced by many interacting variables (macroeconomic indicators, sentiment, global events) beyond the features currently used.
 - Simplified models may fail to capture nonlinear relationships.

- **Model Generalizability:**
 - Performance may vary across different time periods or regimes (e.g., pre‑COVID vs. post‑COVID).

---

## 🛠️ Technical Stack

- **Language:** Python  
- **Libraries:**
  - `numpy`: matrix operations  
  - `pandas`: data analysis  
  - `matplotlib`: graphs and plots  
  - `seaborn`: enhanced visualizations  
  - `sklearn`: model training, AUC ROC visualization, Confusion Matri
  - `kagglehub`: interaction with Kaggle data sets
  - `pickle`: save and load trained machine learning models
    
---

## 📌 Project Scope

Develop a classification model to determine if the 10-day and 21-day MA combined with trading volume is a predictor of stock price movement, and if this model can be applied to high volatility time periods such as during the Covid Pandemic. The project includes:

- Data preprocessing  
- Model training  
- Evaluation  
- Visualization  
- Insights and recommendations  

### 👥 Stakeholders

- Investors 
- Financial Analysts
- Portfolio Managers
- Financial Institutions  

---

## 🧹 Data Cleaning

- **Objective:**  
To prepare a clean and focused dataset for analysis by isolating relevant stock market indexes and time periods, ensuring data integrity through null value removal.

- **Method:**
   Filtered the dataset to include only three selected indexes:
   - NYA – NYSE (USA)
   - IXIC – NASDAQ (USA)
   - GSPTSE – TSX (Canada)

   Applied two distinct date range filters:
  - Pre-COVID: March 2019 to February 2020
  - Post-COVID: March 2020 to May 2021
  - Removed all rows containing null values to ensure consistency and reliability in downstream analysis.*

- **Results:**  
Dataset reduced to only relevant indexes and timeframes, improving focus and analytical clarity. Null values successfully eliminated, resulting in a clean dataset ready for visualization and performance comparison.

---

## 📉 Classification Analysis and Validation

- **Objective:**  
1. To train and build a machine learning model that can use 10 day moving average, 21 day moving average, and volume to predict whether the stock price will go up or down.

- **Method:**  
1. define the features and target for the model (x and y variables)
2. split the dataset 80/20 to keep some holdout data for the test set
3. use ColumnTransformer, StandardScaler, and OneHotEncorder to transform the data and wrap in preprocessing pipeline
4. define the Random Forest Classifier model and combine with preprocessing pipeline
5. cross-validate with a TimeSeriesSplit to keep temporal order

- **Results:**  

Pre-covid train/test:

AUC ROC = 0.56

| measure  | down value (0) | up value (1) | 
|----------|----------------|--------------|
|precision |      0.67      |    0.43      |
|recall    |      0.66      |    0.44      | 
|f1        |      0.66      |    0.44      | 

Post-covid:

AUC ROC = 0.526
Precision = 0.451
Recall = 0.174


---

## ✅ Conclusion

📌 The current model fails to reliably predict stock direction. 
- The model's AUC ROC scores of 0.553 and 0.522 show that the model's accuracy is just above random guessing, which would have a score of 0.5. A "good" AUC ROC would be = ≥ 0.8. - The model is better at predicting down movements than up movements.
- The model performed better on pre-COVID data than post-COVID data suggesting the model cannot adapt to structural market changes.

🔑 Key Takeaways
- The model is not robust across different market regimes (pre- vs. post-COVID).
- Poor accuracy does not mean that the selected variables have no value, signals may exist but require more sophisticated modeling.
- Financial prediction tasks demand richer feature engineering and advanced algorithms to uncover hidden patterns.
- Iterative experimentation is essential to refine models and avoid overfitting simplistic assumptions.


⚠️ Several key challenges emerged:

- Prediction Limitations: The model does not consistently predict market movements.
- Feature Constraints: Individual features alone cannot represent the complexity of financial markets.
- Market Complexity: Stock price changes are driven by many interacting variables beyond those used in the model.
- Data Imbalance: The dataset contains more “up” cases than “down,” which skews accuracy.


🚀 Areas for Improvement
- Incorporate more complex features such as momentum indicators and lagged returns.
- Optimize Random Forest hyperparameters via GridSearchCV.
- Explore alternative models like XGBoost for nonlinear patterns.

---

## 🔗 Team Member Links

| Name              |              Links                |
|-------------------|-----------------------------------|
| Fay Kisteroff     |  https://youtu.be/Q4UN3ItvE8M     |
| Olena Peleshko    |                                   |
| Deanne Acres-Lans |  https://youtu.be/-b15ZRbvbRg     |


# Module 4: Time Series Analysis and Financial Applications

## Module Overview
In this module, we focus on **time series data** and its applications in finance and beyond. Topics include:
- Creating and handling **datetime indices**
- Working with **seasonality** and **trends**
- Rolling and **exponential** moving averages
- Basic **forecasting** methods (ARIMA, etc.) in conjunction with Pandas or external libraries

## Learning Objectives
1. Parse and use **datetime** information effectively.
2. Resample data to different time frequencies (daily, weekly, monthly, etc.).
3. Detect **trends** and **seasonality** in time series.
4. Implement simple forecasting or predictions using ARIMA or exponential smoothing.

## Required Datasets
1. **Yahoo Finance Stock Data**  
   - Source: [Yahoo Finance / Kaggle stocks data](https://finance.yahoo.com/)  
   - Example: Apple (AAPL), Microsoft (MSFT), etc.
2. **Energy Consumption Time Series**  
   - Source: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets.php) (e.g., Household Power Consumption)

---

## Exercises (10 Total)

### Exercise 1
**Objective**: **Datetime parsing** and index creation.  
**Difficulty**: Intermediate  
**Required Dataset**: Stock Data (CSV exported from Yahoo Finance)  
**Problem Statement**:  
- Read `stock_data.csv` and parse the `Date` column as a datetime.  
- Set it as the DataFrame index.  
- Ensure the DataFrame is sorted by date.  

**Key Concepts**:  
- `parse_dates=['Date']`, `df.set_index('Date')`, `df.sort_index()`  
**Solution Approach**:  
- Use `pd.read_csv(..., parse_dates=['Date'])`, set index, then sort by index.

---

### Exercise 2
**Objective**: **Resample** time series data.  
**Difficulty**: Intermediate  
**Required Dataset**: Stock Data  
**Problem Statement**:  
- Create weekly resampled data for `Close` prices.  
- Compute the first, last, min, and max for each week.  

**Key Concepts**:  
- `.resample('W').agg({'Close': ['first','last','min','max']})`  
**Solution Approach**:  
- Use `resample('W')` on the datetime index, then apply multiple aggregations.

---

### Exercise 3
**Objective**: **Rolling** and **exponential** moving averages.  
**Difficulty**: Intermediate  
**Required Dataset**: Stock Data  
**Problem Statement**:  
- Calculate a 20-day **simple moving average** (SMA) of `Close`.  
- Calculate a 20-day **exponential moving average** (EMA).  
- Plot both for comparison.  

**Key Concepts**:  
- `.rolling(window=20).mean()`, `df.ewm(span=20).mean()`  
**Solution Approach**:  
- Compare the lag of SMA vs. EMA visually or statistically.

---

### Exercise 4
**Objective**: **Seasonal decomposition** of time series.  
**Difficulty**: Advanced  
**Required Dataset**: Energy Consumption Time Series  
**Problem Statement**:  
- Decompose daily or hourly consumption data into **trend**, **seasonal**, and **residual** components using `statsmodels`.  

**Key Concepts**:  
- `seasonal_decompose()`, frequency setting, interpret decomposition plots  
**Solution Approach**:  
- `from statsmodels.tsa.seasonal import seasonal_decompose`, specify frequency, visualize results.

---

### Exercise 5
**Objective**: **Detecting anomalies** in energy consumption.  
**Difficulty**: Advanced  
**Required Dataset**: Energy Consumption Time Series  
**Problem Statement**:  
- Identify consumption points that deviate significantly from the **trend** component.  
- Flag and count the anomalies.  

**Key Concepts**:  
- Decomposition residuals, statistical thresholds, anomaly detection  
**Solution Approach**:  
- Compare residual to standard deviation threshold, mark points as outliers.

---

### Exercise 6
**Objective**: **Handling missing dates** in time series.  
**Difficulty**: Intermediate  
**Required Dataset**: Stock Data  
**Problem Statement**:  
- Some trading days are missing in the dataset (weekends, holidays).  
- Reindex to include all calendar days, then **forward fill** missing prices.  

**Key Concepts**:  
- `df.asfreq('D')`, forward fill with `.ffill()`, missing date handling  
**Solution Approach**:  
- Use `asfreq('D')`, then fill with `.fillna(method='ffill')`.

---

### Exercise 7
**Objective**: **ARIMA** or basic forecasting.  
**Difficulty**: Advanced  
**Required Dataset**: Stock Data  
**Problem Statement**:  
- Select a single stock (e.g., AAPL).  
- Split the data into train and test sets.  
- Fit an ARIMA model on the train set, forecast on the test set.  

**Key Concepts**:  
- ARIMA modeling with `statsmodels.tsa.arima.model.ARIMA`, train/test split, forecast evaluation  
**Solution Approach**:  
- Evaluate forecast with RMSE or MAPE on the test set.

---

### Exercise 8
**Objective**: **Rolling correlation** between two stocks.  
**Difficulty**: Intermediate  
**Required Dataset**: Stock Data (two tickers)  
**Problem Statement**:  
- Merge two DataFrames on date (e.g., AAPL and MSFT).  
- Compute a **30-day rolling correlation** of their daily returns.  

**Key Concepts**:  
- Merging on index (date), `pct_change()`, rolling correlation  
**Solution Approach**:  
- Calculate daily returns for both, then `.rolling(30).corr()` with each other.

---

### Exercise 9
**Objective**: Time zone handling and **UTC** conversion.  
**Difficulty**: Intermediate  
**Required Dataset**: Energy Consumption or any dataset with timezone info  
**Problem Statement**:  
- Convert times from local time to **UTC**.  
- Resample data to hourly intervals in UTC.  

**Key Concepts**:  
- `df.tz_localize('America/Los_Angeles')`, then `df.tz_convert('UTC')`  
**Solution Approach**:  
- Verify date/time columns are timezone-aware before resampling.

---

### Exercise 10
**Objective**: Visualization of **seasonal** and **trend** changes over multiple years.  
**Difficulty**: Advanced  
**Required Dataset**: Energy Consumption Time Series (multi-year)  
**Problem Statement**:  
- Plot yearly usage in subplots (one subplot per year).  
- Highlight peak usage periods each year.  

**Key Concepts**:  
- Splitting data by year, advanced plotting, analyzing seasonal patterns  
**Solution Approach**:  
- Use `df.groupby(df.index.year)` or create subplots in a loop for each year.

---

## Expected Outcomes
After this module, you will:
- Confidently **handle and analyze time series** data with Pandas.
- Resample, decompose, and forecast using basic methods.
- Understand how to manage anomalies, missing data, and time zones.

## Additional Resources
- [Pandas Time Series Docs](https://pandas.pydata.org/docs/user_guide/timeseries.html)
- [Statsmodels Time Series Analysis](https://www.statsmodels.org/stable/tsa.html)
- [ARIMA Forecasting Example](https://www.machinelearningplus.com/time-series/arima-model-time-series-forecasting-python/)
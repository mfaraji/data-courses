# Module 3: Advanced Data Analysis and Statistical Operations

## Module Overview
Dive deeper into **descriptive statistics**, **correlation analysis**, **regressions**, and **complex groupby operations**. You’ll learn:
- Advanced `groupby()` patterns
- Statistical methods (`describe()`, correlation matrices)
- Applying basic regression inside Pandas
- Using rolling and expanding windows for analytics

## Learning Objectives
1. Create advanced **aggregations** using multi-key groupby.
2. Perform **correlation** and basic statistical analysis on numeric columns.
3. Implement simple **linear regression** with Pandas or minimal external libraries.
4. Use **rolling** and **expanding** functions for moving averages, sums, etc.

## Required Datasets
1. **World Happiness Report**  
   - Source: [Kaggle Dataset](https://www.kaggle.com/datasets/unsdsn/world-happiness)  
2. **Stock Market Sample**  
   - Source: [Yahoo Finance CSV exports or Kaggle Stock Datasets](https://finance.yahoo.com/)

---

## Exercises (10 Total)

### Exercise 1
**Objective**: Advanced **groupby** with multiple levels and transformations.  
**Difficulty**: Intermediate  
**Required Dataset**: World Happiness Report  
**Problem Statement**:  
- Group by `Region` and `Year`, compute average `Happiness Score` and total population.  
- Use **transform** to add each country’s deviation from the regional average.  

**Key Concepts**:  
- Multi-level groupby, `transform()`, applying custom logic in groupby  
**Solution Approach**:  
- `df.groupby(['Region','Year'])['HappinessScore'].transform(lambda x: x - x.mean())` to get deviation.

---

### Exercise 2
**Objective**: **Pivot tables** for aggregated statistics.  
**Difficulty**: Intermediate  
**Required Dataset**: World Happiness Report  
**Problem Statement**:  
- Create a pivot table summarizing `Happiness Score` by `Region` and `Year`.  
- Include sub-aggregations for mean, min, and max.  

**Key Concepts**:  
- `pd.pivot_table()`, multiple aggregation functions  
**Solution Approach**:  
- Use `pivot_table` with `aggfunc=['mean','min','max']`, index=`Region`, columns=`Year`.

---

### Exercise 3
**Objective**: **Correlation** matrix and analysis.  
**Difficulty**: Intermediate  
**Required Dataset**: World Happiness Report  
**Problem Statement**:  
- Calculate the correlation matrix for `Happiness Score`, `GDP per Capita`, `Life Expectancy`.  
- Identify the highest correlated pairs.  

**Key Concepts**:  
- `df.corr()`, numerical relationships, correlation analysis  
**Solution Approach**:  
- Subset numeric columns, use `.corr()`, interpret correlation coefficients.

---

### Exercise 4
**Objective**: **Statistical testing** (t-test or ANOVA).  
**Difficulty**: Advanced  
**Required Dataset**: World Happiness Report  
**Problem Statement**:  
- Compare `Happiness Score` among different **Regions** (ANOVA or multiple t-tests).  
- Determine if there is a statistically significant difference.  

**Key Concepts**:  
- T-test, ANOVA, `scipy.stats` integration  
**Solution Approach**:  
- Group by region, gather scores, run `scipy.stats.f_oneway(*groups)` for ANOVA.

---

### Exercise 5
**Objective**: Basic **regression** in Pandas (or minimal usage of `statsmodels`).  
**Difficulty**: Advanced  
**Required Dataset**: World Happiness Report  
**Problem Statement**:  
- Regress `Happiness Score` on `GDP per Capita` and `Life Expectancy`.  
- Evaluate model summary (R², p-values).  

**Key Concepts**:  
- Using `statsmodels.formula.api` or manual OLS methods, linear regression basics  
**Solution Approach**:  
- `import statsmodels.api as sm`, set up `X` and `y`, fit a regression, interpret the results.

---

### Exercise 6
**Objective**: **Rolling** window calculations.  
**Difficulty**: Intermediate  
**Required Dataset**: Stock Market Sample  
**Problem Statement**:  
- Compute a **20-day rolling average** of daily closing prices.  
- Add a rolling **volatility** measure (standard deviation) for each stock.  

**Key Concepts**:  
- `.rolling(window=20).mean()`, `.rolling(window=20).std()`  
**Solution Approach**:  
- Sort by date, group by stock symbol, then apply rolling on the `Close` column.

---

### Exercise 7
**Objective**: **Expanding** window calculations for cumulative metrics.  
**Difficulty**: Intermediate  
**Required Dataset**: Stock Market Sample  
**Problem Statement**:  
- Calculate a **cumulative sum** of trading volume for each stock symbol.  
- Identify when the cumulative volume surpasses a certain threshold.  

**Key Concepts**:  
- `.expanding()`, cumulative metrics, groupby expansions  
**Solution Approach**:  
- `df.groupby('Symbol')['Volume'].expanding().sum()`, then compare to threshold.

---

### Exercise 8
**Objective**: **Grouping** by time-based periods for stock data.  
**Difficulty**: Intermediate  
**Required Dataset**: Stock Market Sample  
**Problem Statement**:  
- Convert the `Date` column to a datetime index.  
- Group by **quarter** and compute average closing price for each stock in each quarter.  

**Key Concepts**:  
- `resample('Q')`, time-based grouping, multi-level grouping with stock symbol  
**Solution Approach**:  
- Set `Date` as index, group by `Symbol`, then `.resample('Q')['Close'].mean()`.

---

### Exercise 9
**Objective**: **Identify outliers** using a rolling approach.  
**Difficulty**: Advanced  
**Required Dataset**: Stock Market Sample  
**Problem Statement**:  
- For each stock, calculate a rolling mean and rolling std of `Close`.  
- Flag days where the `Close` price is more than 2 standard deviations from the rolling mean.  

**Key Concepts**:  
- Rolling mean and std, outlier detection, Boolean indexing  
**Solution Approach**:  
- `upper_bound = rolling_mean + 2 * rolling_std`, compare daily `Close` to `upper_bound` and `lower_bound`.

---

### Exercise 10
**Objective**: **Multi-dimensional** groupby and advanced transformations.  
**Difficulty**: Advanced  
**Required Dataset**: World Happiness Report  
**Problem Statement**:  
- Group data by `Region` and **Income Level** (create categories from `GDP per Capita`).  
- Compute advanced statistics (mean, median, custom transformations).  

**Key Concepts**:  
- Creating bins/categorical columns from numeric data, multi-key groupby, custom aggregator  
**Solution Approach**:  
- Use `pd.cut(...)` to create income level bins, then group by `[Region, 'IncomeLevel']` and apply `.agg()`.

---

## Expected Outcomes
By the end of this module, you will be able to:
- Perform **in-depth statistical analyses** with Pandas.
- Understand advanced usage of `groupby()`, pivot tables, and rolling windows.
- Integrate minimal external libraries for regression and hypothesis testing.

## Additional Resources
- [Statsmodels Documentation](https://www.statsmodels.org/)
- [Pandas Rolling Window Docs](https://pandas.pydata.org/docs/user_guide/window.html)
- [Advanced Pandas GroupBy Tricks](https://realpython.com/pandas-groupby/)
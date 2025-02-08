---

# Module 1: Advanced Data Manipulation and Transformation

**Folder**: `Module1-AdvancedDataManipulation/README.md`

```markdown
# Module 1: Advanced Data Manipulation and Transformation

## Module Overview
This module covers **complex data manipulation** techniques using Pandas. You will learn about:
- Multi-level indexing
- Merging and joining DataFrames in advanced scenarios
- Reshaping data (melt, pivot, pivot_table)
- Complex groupby operations and custom aggregations
- Data cleaning and handling categorical data

## Learning Objectives
1. Master multi-index and hierarchical structures in Pandas.
2. Perform **advanced joins** and merges (one-to-many, many-to-many).
3. Reshape data using **melt**, **pivot**, and **stack/unstack** operations.
4. Handle missing data with **custom logic** and data transformations.
5. Create custom aggregation functions with **groupby**.

## Required Datasets
1. **Air Quality Data**  
   - Source: [Air Quality Dataset on Kaggle](https://www.kaggle.com/datasets/volpatto/air-quality-dataset)  
   - This dataset contains air pollution measurements from various sensors.
2. **Retail Sales Data**  
   - Source: [Online Retail Data](https://archive.ics.uci.edu/ml/datasets/Online+Retail)  
   - A transactional dataset of online retail store sales.

*(Download these datasets and store them in a local `data/` folder for easy reference.)*

---

## Exercises (10 Total)

### Exercise 1
**Objective**: Practice advanced DataFrame **merging** and **joining**.  
**Difficulty**: Intermediate  
**Required Dataset**: Retail Sales Data  
**Problem Statement**:  
- You have two CSV files: `sales_data.csv` (transaction-level) and `customer_data.csv` (customer info).  
- Perform a **left join** to combine them into a single DataFrame with **all transactions**.  
- Identify and handle **duplicate** or **conflicting** keys.  

**Key Concepts**:  
- `pd.merge()`, join types, handling duplicates, verifying joins  
**Hints**:  
- Look out for columns with the same name in both DataFrames.  
**Solution Approach**:  
- Use `pd.merge(..., how='left')` on the correct key columns.  
- Check for duplicates or mismatch after merge.  

---

### Exercise 2
**Objective**: Explore **multi-level indexing** and hierarchical data structures.  
**Difficulty**: Intermediate  
**Required Dataset**: Retail Sales Data  
**Problem Statement**:  
- Convert the combined retail data (from Exercise 1) to a **multi-level index** on `[Country, InvoiceNo]`.  
- Sort the multi-index and practice selecting subsets using **.loc** with multiple levels.  

**Key Concepts**:  
- Setting multi-level index, sorting index, indexing subsets  
**Hints**:  
- `df.set_index(['Country', 'InvoiceNo'])`  
**Solution Approach**:  
- Use `.sort_index()` after setting the multi-level index, then query slices with `.loc[('United Kingdom', 536365), :]`.

---

### Exercise 3
**Objective**: Reshape data using **melt** and **pivot**.  
**Difficulty**: Intermediate  
**Required Dataset**: Air Quality Data  
**Problem Statement**:  
- You have monthly average pollutant concentrations for multiple cities stored **wide**.  
- Convert the data to a **long** format using `melt()`.  
- Then **pivot** it back to a wide format but index by the date column.  

**Key Concepts**:  
- `pd.melt()`, `df.pivot()`, wide-to-long transformations  
**Hints**:  
- Understand `id_vars` and `value_vars` in `melt()`.  
**Solution Approach**:  
- Melt the data with `id_vars=['Date']`. Then pivot using `df.pivot(index='Date', columns='City', values='Concentration')`.

---

### Exercise 4
**Objective**: Use **stack** and **unstack** to manage hierarchical columns.  
**Difficulty**: Intermediate  
**Required Dataset**: Air Quality Data  
**Problem Statement**:  
- Create a DataFrame with multi-level columns (pollutant type, city).  
- Convert columns to rows with `stack()`, then revert with `unstack()`.  

**Key Concepts**:  
- `stack()`, `unstack()`, multi-index columns, dimension transformations  
**Hints**:  
- Start with a pivoted table to get a multi-level column structure.  
**Solution Approach**:  
- `df.stack(level=-1)` to pivot the innermost level of columns into rows.

---

### Exercise 5
**Objective**: Practice **groupby with custom aggregation**.  
**Difficulty**: Intermediate  
**Required Dataset**: Retail Sales Data  
**Problem Statement**:  
- Group the retail data by `Country` and create a **custom aggregation** that calculates total quantity, average unit price, and a custom metric (e.g., total quantity * average unit price).  

**Key Concepts**:  
- `groupby()`, `.agg()`, custom functions, multiple aggregations  
**Hints**:  
- Use a dictionary in `.agg({'Quantity': 'sum', 'UnitPrice': 'mean', ...})`.  
**Solution Approach**:  
- Define a function for custom metric, pass it into `.agg(custom_function)`.

---

### Exercise 6
**Objective**: **Combine** multiple DataFrames using `concat()`.  
**Difficulty**: Intermediate  
**Required Dataset**: Retail Sales Data (two separate monthly files)  
**Problem Statement**:  
- You have two monthly sales files `sales_jan.csv` and `sales_feb.csv`.  
- Concatenate them vertically.  
- Ensure consistent columns and handle any missing fields.  

**Key Concepts**:  
- `pd.concat()`, verifying column alignment, dealing with missing columns  
**Hints**:  
- If columns differ, specify `join='outer'` or `join='inner'`.  
**Solution Approach**:  
- Check for differences in columns, handle them appropriately with `concat([df1, df2], axis=0)`.

---

### Exercise 7
**Objective**: Advanced **data cleaning** and outlier handling.  
**Difficulty**: Intermediate  
**Required Dataset**: Air Quality Data  
**Problem Statement**:  
- Identify extreme outliers in pollutant readings that are likely data entry errors.  
- Implement a strategy to **clip** or remove them.  

**Key Concepts**:  
- Detecting outliers, data cleaning, `clip()`, descriptive statistics  
**Hints**:  
- Use IQR-based or z-score-based methods.  
**Solution Approach**:  
- Calculate bounds using IQR or standard deviation, then remove or clip values outside a threshold.

---

### Exercise 8
**Objective**: Work with **categorical data** and memory optimization.  
**Difficulty**: Intermediate  
**Required Dataset**: Retail Sales Data  
**Problem Statement**:  
- Convert columns like `Country` and `StockCode` to **categorical**.  
- Compare **memory usage** before and after.  

**Key Concepts**:  
- `astype('category')`, `df.memory_usage(deep=True)`, optimizing DataFrame memory  
**Hints**:  
- Use `info(memory_usage='deep')` to see changes in memory usage.  
**Solution Approach**:  
- `df['Country'] = df['Country'].astype('category')`, measure memory usage differences.

---

### Exercise 9
**Objective**: Complex **sort** and **rank** operations.  
**Difficulty**: Intermediate  
**Required Dataset**: Retail Sales Data  
**Problem Statement**:  
- Sort data by `Country` ascending, then by `UnitPrice` descending.  
- Create a new column **rank** based on `UnitPrice` within each country.  

**Key Concepts**:  
- `sort_values()`, `groupby().rank()`, multi-level sorting  
**Hints**:  
- Use `df.sort_values(['Country','UnitPrice'], ascending=[True, False])`.  
**Solution Approach**:  
- Perform the sort, then group by `Country` and rank by `UnitPrice`.

---

### Exercise 10
**Objective**: Handle **duplicates** and maintain data integrity.  
**Difficulty**: Intermediate  
**Required Dataset**: Retail Sales Data  
**Problem Statement**:  
- Find duplicate entries in the combined retail dataset.  
- Decide which duplicates are valid and which to remove.  

**Key Concepts**:  
- `df.duplicated()`, `df.drop_duplicates()`, advanced deduplication logic  
**Hints**:  
- Check columns `['InvoiceNo','StockCode','Quantity']` or others for identifying duplicates.  
**Solution Approach**:  
- Use `df.duplicated(subset=['InvoiceNo','StockCode'], keep='first')` to locate duplicates, then remove or handle them carefully.

---

## Expected Outcomes
By completing this module, you will:
- Confidently reshape and merge complex datasets.
- Manage multi-level indices and categorical data.
- Develop advanced groupby logic and custom aggregations.

## Additional Resources
- [Pandas Official Documentation](https://pandas.pydata.org/docs/)
- [Pandas CookBook by Julia Evans](https://github.com/jvns/pandas-cookbook)
- [Reshaping and pivot tables in Pandas](https://pandas.pydata.org/docs/user_guide/reshaping.html)
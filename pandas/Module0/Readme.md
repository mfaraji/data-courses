# Module 0: Pandas Fundamentals and Data Manipulation

## Overview
This module contains 10 comprehensive exercises designed to help you master fundamental to advanced Pandas concepts. Each exercise builds upon previous ones, covering data manipulation, cleaning, analysis, and performance optimization.

## Dataset
We'll be using the Titanic dataset for most exercises:
- Source: [Titanic Dataset](https://raw.githubusercontent.com/mwaskom/seaborn-data/master/titanic.csv)
- Download using:
```python
import pandas as pd
df = pd.read_csv('https://raw.githubusercontent.com/mwaskom/seaborn-data/master/titanic.csv')
```

## Exercise List

### Exercise 1: Getting Started with Pandas
**Goal**: Learn how to load data and inspect a DataFrame.

**Tasks**:
1. Import Pandas and load the Titanic dataset
2. Display the first 10 rows
3. Print the shape, column names, and summary statistics

**Key Concepts**:
- DataFrame basics
- Data inspection methods
- Basic DataFrame properties

### Exercise 2: Data Selection and Filtering
**Goal**: Master indexing, slicing, and conditional filtering.

**Tasks**:
1. Select specific columns (`sex`, `age`, `fare`)
2. Filter passengers older than 30
3. Find passengers who paid more than 50 and were under 18
4. Get the youngest passenger's details

**Key Concepts**:
- Boolean indexing
- Column selection
- Complex conditions

### Exercise 3: Data Cleaning and Handling Missing Values
**Goal**: Learn missing value handling strategies.

**Tasks**:
1. Identify missing values per column
2. Fill missing age values with median
3. Drop rows with missing embarked values
4. Replace missing cabin values

**Key Concepts**:
- Missing value detection
- Imputation strategies
- Data cleaning techniques

### Exercise 4: Data Transformation and Applying Functions
**Goal**: Master data transformation techniques.

**Tasks**:
1. Create age categories
2. Normalize fare column
3. Transform string columns

**Key Concepts**:
- Custom functions
- apply() method
- Data normalization

### Exercise 5: Grouping and Aggregations
**Goal**: Learn data summarization techniques.

**Tasks**:
1. Calculate average fare by class
2. Compute survival rates by gender
3. Find age statistics by embarkation point

**Key Concepts**:
- GroupBy operations
- Aggregation functions
- Multiple statistics

### Exercise 6: Sorting and Ranking
**Goal**: Master data ordering techniques.

**Tasks**:
1. Sort by fare (descending)
2. Identify oldest passengers
3. Create age rankings

**Key Concepts**:
- sort_values()
- rank()
- Multiple sort criteria

### Exercise 7: Merging, Joining, and Concatenation
**Goal**: Learn DataFrame combination techniques.

**Tasks**:
1. Create supplementary DataFrame
2. Perform merge operations
3. Practice concatenation

**Key Concepts**:
- merge()
- concat()
- Join types

### Exercise 8: Pivot Tables and Crosstabs
**Goal**: Master data restructuring.

**Tasks**:
1. Create multi-level pivot tables
2. Generate crosstab analysis

**Key Concepts**:
- pivot_table()
- crosstab()
- Multi-index operations

### Exercise 9: Time Series Analysis
**Goal**: Introduction to time-based operations.

**Tasks**:
1. Create date range
2. Generate time series data
3. Perform resampling

**Key Concepts**:
- date_range()
- Resampling
- Time series operations

### Exercise 10: Performance Optimization
**Goal**: Learn optimization techniques.

**Tasks**:
1. Optimize data types
2. Use eval() for computations
3. Compare operation speeds

**Key Concepts**:
- Memory optimization
- Vectorization
- Performance testing

## Getting Started
1. Create a new Jupyter notebook
2. Import required libraries:
```python
import pandas as pd
import numpy as np
```
3. Download the dataset
4. Complete exercises in order

## Additional Resources
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [10 Minutes to Pandas](https://pandas.pydata.org/docs/user_guide/10min.html)
- [Pandas Cheat Sheet](https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf)
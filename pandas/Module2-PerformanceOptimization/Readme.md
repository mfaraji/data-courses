# Module 2: Performance Optimization and Large Dataset Handling

## Module Overview
Large datasets can be challenging when working with Pandas due to memory constraints and performance bottlenecks. In this module, you will learn:
- **Vectorization** vs. `apply()` vs. loops
- **Chunking** and incremental data loading
- Memory profiling and type optimization
- Parallelization strategies (optional or with external libraries)

## Learning Objectives
1. Efficiently load and process **large CSV** or JSON files using chunking.
2. Compare **performance** between vectorized operations and Python loops.
3. Profile and reduce **memory usage** through data type conversions.
4. Understand best practices for **parallel** or distributed data processing.

## Required Datasets
1. **NYC Taxi Trip Data** (large subset)  
   - Source: [NYC Taxi Dataset on Kaggle](https://www.kaggle.com/datasets/nyctaxi/taxi-trip-duration)  
   - Make sure to download a smaller subset if memory is limited.
2. **IMDB Movies Dataset**  
   - Source: [IMDB Movies Dataset](https://www.kaggle.com/datasets/PromptCloudHQ/imdb-data)  

---

## Exercises (10 Total)

### Exercise 1
**Objective**: Practice **incremental data loading** (chunking).  
**Difficulty**: Intermediate  
**Required Dataset**: NYC Taxi Trip Data  
**Problem Statement**:  
- Load the dataset in chunks of 100k rows.  
- Compute the average trip distance for each chunk and keep a running total.  

**Key Concepts**:  
- `pd.read_csv(..., chunksize=100000)`, iterating over chunks, aggregations  
**Solution Approach**:  
- Use a loop to read each chunk, calculate stats, and aggregate results in a final summary.

---

### Exercise 2
**Objective**: Compare **vectorized** operations vs. `apply()` and **pure Python loops**.  
**Difficulty**: Intermediate  
**Required Dataset**: NYC Taxi Trip Data  
**Problem Statement**:  
- Calculate a new column `cost_per_mile = total_amount / trip_distance` three ways:  
  1. Vectorized  
  2. `df.apply(...)`  
  3. Simple for-loop  
- **Time** each approach.  

**Key Concepts**:  
- `%timeit` (in Jupyter), vectorization, apply performance  
**Solution Approach**:  
- Use Jupyter magic commands or `time.perf_counter()` to measure execution time for each approach.

---

### Exercise 3
**Objective**: **Memory profiling** and type optimization.  
**Difficulty**: Intermediate  
**Required Dataset**: NYC Taxi Trip Data  
**Problem Statement**:  
- Convert `passenger_count`, `payment_type`, and other columns to smaller integer types (e.g., `int8`).  
- Convert location-based columns to `float32` if appropriate.  
- Measure memory usage **before and after**.  

**Key Concepts**:  
- `df.dtypes`, `df.astype()`, memory usage, integer downcasting  
**Solution Approach**:  
- Identify columns with low numeric ranges. Use `astype('int8')` or `astype('float32')`.

---

### Exercise 4
**Objective**: Handling **missing data** in large datasets efficiently.  
**Difficulty**: Intermediate  
**Required Dataset**: NYC Taxi Trip Data  
**Problem Statement**:  
- Identify columns with missing data above a certain threshold (e.g., 5%).  
- Decide whether to drop, fill, or otherwise handle those columns/rows.  
- Compare performance of `fillna()` vs. chunk-based strategies.  

**Key Concepts**:  
- `df.isnull().sum()`, chunked approach, memory trade-offs  
**Solution Approach**:  
- Evaluate the proportion of missing data, then either drop or use a method like `fillna(method='ffill')`.

---

### Exercise 5
**Objective**: Use **categorical** data for large string columns.  
**Difficulty**: Intermediate  
**Required Dataset**: IMDB Movies Dataset  
**Problem Statement**:  
- Columns like `Genre` and `Director` can have repeated values. Convert them to `category`.  
- Check **query performance** before and after.  

**Key Concepts**:  
- String columns, `df['column'].astype('category')`, memory vs. performance trade-offs  
**Solution Approach**:  
- Benchmark a simple query (e.g., filter movies by a certain genre) before and after conversion to `category`.

---

### Exercise 6
**Objective**: Implement **parallel** or multi-threaded computations (optional advanced).  
**Difficulty**: Advanced  
**Required Dataset**: NYC Taxi Trip Data  
**Problem Statement**:  
- Use an external library (like `dask` or `swifter`) to parallelize an expensive operation.  
- Compare the time to a single-thread approach.  

**Key Concepts**:  
- Dask DataFrame, parallel processing, concurrency  
**Solution Approach**:  
- Convert Pandas DataFrame to Dask DataFrame, then run the same transformations using `dask.dataframe`.

---

### Exercise 7
**Objective**: Incremental **aggregation** and on-the-fly **analysis**.  
**Difficulty**: Advanced  
**Required Dataset**: NYC Taxi Trip Data  
**Problem Statement**:  
- Continuously read new monthly data from a directory.  
- For each new file, update the total number of trips and average fare.  
- This simulates an **append-only** scenario.  

**Key Concepts**:  
- Incremental loading, updating aggregates, real-time analysis approaches  
**Solution Approach**:  
- Watch for new files in a directory, read them, and update a stored summary table.

---

### Exercise 8
**Objective**: **Resampling** large datasets with date/time columns.  
**Difficulty**: Intermediate  
**Required Dataset**: NYC Taxi Trip Data  
**Problem Statement**:  
- Convert `pickup_datetime` to a Pandas datetime index.  
- Resample to monthly frequency, calculating total trips per month.  

**Key Concepts**:  
- `pd.to_datetime()`, setting datetime index, `.resample()`, large dataset considerations  
**Solution Approach**:  
- Create a date-based index and use `.resample('M').size()` or `.count()` to get monthly counts.

---

### Exercise 9
**Objective**: Sorting and **ranking** large datasets efficiently.  
**Difficulty**: Intermediate  
**Required Dataset**: IMDB Movies Dataset  
**Problem Statement**:  
- Sort movies by `IMDB Score` descending.  
- Generate a **rank** for each movie.  
- Compare performance with chunk-based partial sorting if the dataset is huge.  

**Key Concepts**:  
- Sorting a large DataFrame, ranking, partial sorting strategies  
**Solution Approach**:  
- Attempt normal sorting with `.sort_values()`, then explore chunk-based approach or out-of-memory solutions.

---

### Exercise 10
**Objective**: Using **HDF5** or **Parquet** format for optimized storage.  
**Difficulty**: Advanced  
**Required Dataset**: NYC Taxi Trip Data or IMDB Movies Dataset  
**Problem Statement**:  
- Convert CSV data into Parquet or HDF5.  
- Demonstrate reduced storage size and faster load times.  

**Key Concepts**:  
- Parquet format (`df.to_parquet()`), `PyTables` for HDF5, I/O performance  
**Solution Approach**:  
- Load CSV into a DataFrame, then `df.to_parquet('data.parquet')`. Measure file size and load time differences.

---

## Expected Outcomes
After completing this module, learners will:
- Efficiently handle **large datasets** in Pandas.
- Optimize memory usage and speed up operations.
- Explore advanced solutions like parallelization and alternative file formats.

## Additional Resources
- [Dask Documentation](https://docs.dask.org/en/stable/)
- [Pandas Performance Tips](https://pandas.pydata.org/docs/user_guide/enhancingperf.html)
- [Efficient I/O with Parquet](https://towardsdatascience.com/the-ultimate-guide-to-data-parquet-421f3ad4b4c2)
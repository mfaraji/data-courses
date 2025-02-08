# Module 5: Advanced Visualization and Reporting with Pandas

## Module Overview
This module focuses on creating **compelling visualizations and reports** directly from Pandas or in combination with libraries like Matplotlib, Seaborn, and Plotly. You will:
- Use **Pandas plotting** APIs
- Leverage **Seaborn** for advanced statistical plots
- Create **interactive** visualizations
- Generate professional **reports** in PDF or HTML

## Learning Objectives
1. Utilize **Pandas built-in** plot methods for quick visual insights.
2. Create advanced visualizations with **Seaborn** (pairplot, heatmap, etc.).
3. Build **interactive** dashboards using Plotly or other libraries (intro level).
4. Automate reporting in **HTML** or **PDF** (e.g., `pandas-profiling` or Jupyter nbconvert).

## Required Datasets
1. **Healthcare Analytics Dataset**  
   - Source: [Kaggle Healthcare Data](https://www.kaggle.com/datasets?search=healthcare) (e.g., hospital readmissions)  
2. **Marketing Campaign Data**  
   - Source: [Marketing Data on Kaggle](https://www.kaggle.com/datasets) (customer segmentation, marketing campaigns)

---

## Exercises (10 Total)

### Exercise 1
**Objective**: **Basic plotting** with Pandas (`.plot()`).  
**Difficulty**: Intermediate  
**Required Dataset**: Healthcare Analytics Dataset  
**Problem Statement**:  
- Plot the distribution of patient ages as a **histogram**.  
- Plot the count of admissions per department as a **bar chart**.  

**Key Concepts**:  
- `df['Age'].plot(kind='hist')`, `df['Department'].value_counts().plot(kind='bar')`  
**Solution Approach**:  
- Use built-in `.plot()` methods for quick overviews.

---

### Exercise 2
**Objective**: **Seaborn** advanced statistical plots.  
**Difficulty**: Intermediate  
**Required Dataset**: Healthcare Analytics Dataset  
**Problem Statement**:  
- Compare the distribution of **Length of Stay** across different **Age Groups**.  
- Use a **boxplot** or **violin plot** from Seaborn.  

**Key Concepts**:  
- `sns.boxplot(x='AgeGroup', y='LengthOfStay', data=df)`  
**Solution Approach**:  
- Convert `Age` to categories or bins, then plot using Seaborn.

---

### Exercise 3
**Objective**: **Correlation heatmap** with Seaborn.  
**Difficulty**: Intermediate  
**Required Dataset**: Marketing Campaign Data  
**Problem Statement**:  
- Compute correlation of numeric features (spend amounts, customer age, etc.).  
- Visualize it with a **heatmap**.  

**Key Concepts**:  
- `df.corr()`, `sns.heatmap()`  
**Solution Approach**:  
- Generate correlation matrix, pass it into `sns.heatmap(...)`.

---

### Exercise 4
**Objective**: **Pairplot** for multivariate exploration.  
**Difficulty**: Intermediate  
**Required Dataset**: Marketing Campaign Data  
**Problem Statement**:  
- Use Seaborn’s `pairplot` to visualize relationships among numeric columns (spend, income, etc.).  

**Key Concepts**:  
- `sns.pairplot(df[["Income","Spend","Age"]])`  
**Solution Approach**:  
- Subset relevant columns, create pairplot, observe bivariate distributions.

---

### Exercise 5
**Objective**: **Interactive** plots with Plotly (or another library).  
**Difficulty**: Advanced  
**Required Dataset**: Healthcare Analytics Dataset  
**Problem Statement**:  
- Create an **interactive line chart** showing daily admissions over time.  
- Hover tooltips should show date and total admissions.  

**Key Concepts**:  
- Plotly Express (`px.line()`), interactivity, customizing tooltips  
**Solution Approach**:  
- `import plotly.express as px`, prepare daily aggregated data, and pass to `px.line(...)`.

---

### Exercise 6
**Objective**: **Geo-visualizations** (maps).  
**Difficulty**: Advanced  
**Required Dataset**: Marketing Campaign Data (with regional or city info)  
**Problem Statement**:  
- Plot customer distribution on a **map**, coloring regions by number of customers or sales.  

**Key Concepts**:  
- `plotly.express.choropleth()`, mapping region codes, geospatial analysis  
**Solution Approach**:  
- Convert region/city info to valid geo-codes or lat/long, then produce a choropleth or scatter map.

---

### Exercise 7
**Objective**: Create a **dashboard** layout in Jupyter.  
**Difficulty**: Advanced  
**Required Dataset**: Marketing Campaign Data  
**Problem Statement**:  
- Combine a bar chart, a line chart, and a summary table into a single interactive dashboard.  

**Key Concepts**:  
- `ipywidgets` or Plotly Dash or Panel to arrange multiple charts  
**Solution Approach**:  
- Use a Jupyter environment with interactive widgets or a minimal dash app to layout visuals.

---

### Exercise 8
**Objective**: **Automate** a basic PDF or HTML report.  
**Difficulty**: Intermediate  
**Required Dataset**: Healthcare Analytics Dataset  
**Problem Statement**:  
- Generate a summary report with **tables** and **charts**.  
- Export it as an HTML file (and optionally convert to PDF).  

**Key Concepts**:  
- `pandas.DataFrame.to_html()`, Jupyter `nbconvert`, or libraries like `WeasyPrint`  
**Solution Approach**:  
- Programmatically create HTML with embedded charts, then use nbconvert or a printing library to export PDF.

---

### Exercise 9
**Objective**: **Styling** DataFrames for reporting.  
**Difficulty**: Intermediate  
**Required Dataset**: Marketing Campaign Data  
**Problem Statement**:  
- Apply **conditional formatting** (highlight top spenders or certain conditions).  
- Save the styled table to an HTML file.  

**Key Concepts**:  
- `df.style.highlight_max()`, `.style.apply(...)`, exporting styled HTML  
**Solution Approach**:  
- Use Pandas styling API, create a custom highlight function.

---

### Exercise 10
**Objective**: **Advanced** custom visuals with Matplotlib and Seaborn.  
**Difficulty**: Advanced  
**Required Dataset**: Healthcare Analytics Dataset or Marketing Data  
**Problem Statement**:  
- Create a multi-plot figure with custom subplots.  
- Combine a bar chart, line chart, and scatter plot with a shared legend.  

**Key Concepts**:  
- `plt.subplots()`, subplots layout, shared legend, advanced customization  
**Solution Approach**:  
- Use Matplotlib object-oriented API, create multiple Axes, pass them to Seaborn or Pandas plots.

---

## Expected Outcomes
By completing this final module, you’ll:
- Develop **beautiful and insightful** data visualizations with Pandas and Seaborn.
- Create **interactive** charts for deeper analysis and presentations.
- Automate **reporting** workflows for professional environments.

## Additional Resources
- [Seaborn Documentation](https://seaborn.pydata.org/)
- [Plotly Express](https://plotly.com/python/plotly-express/)
- [Pandas Styling and Visualization Guide](https://pandas.pydata.org/docs/user_guide/style.html)
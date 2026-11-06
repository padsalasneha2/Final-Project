# 🌍 AIR QUALITY DATA ANALYSIS
### Python | NumPy | Pandas | Matplotlib | Seaborn | Jupyter Notebook

---

## 📌 1. Project Introduction

The **Air Quality Data Analysis** project is a Python-based data analysis project. It uses an air-quality dataset containing 300 records and 25 columns. The project explores air-quality measurements, cleans and prepares the data, performs numerical calculations, and creates charts to understand Carbon Monoxide (CO) measurements and their relationship with other variables.

The project is implemented in a Jupyter Notebook using NumPy, Pandas, Matplotlib, and Seaborn.

## 🎯 2. Project Objectives

1. Import the required Python libraries.
2. Load the air-quality CSV dataset.
3. Explore the dataset using Pandas.
4. inspect the first and last records.
5. Identify missing values.
6. Remove rows containing missing values.
7. Convert the Date column into datetime format.
8. Check column data types and dataset information.
9. Find unique CO-level categories.
10. Perform statistical calculations using NumPy.
11. Create data visualizations using Matplotlib.
12. Create statistical visualizations using Seaborn.
13. Study numerical correlations between air-quality measurements.

## 🧰 3. Technologies and Libraries Used

| Technology | Use in This Project |
|---|---|
| Python | Main programming language |
| NumPy | Numerical arrays and statistical calculations |
| Pandas | CSV loading, data exploration, and cleaning |
| Matplotlib | Creating charts and plots |
| Seaborn | Creating statistical visualizations |
| Jupyter Notebook | Writing and executing code cell by cell |

### Library Import

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

## 📂 4. Project Files

```text
Air-Quality-Data-Analysis/
│
├── finel-project.ipynb
├── AirQuality_300_final_no_city.csv
└── README.md
```

- `finel-project.ipynb` — Main notebook containing the complete analysis.
- `AirQuality_300_final_no_city.csv` — Dataset used by the notebook.
- `README.md` — Project documentation.

## 📊 5. Dataset Description

The project reads the following CSV file:

`AirQuality_300_final_no_city.csv`

The uploaded notebook displays a dataset with **300 rows and 25 columns**.

### Important Dataset Columns

| Column | Description |
|---|---|
| `Country` | Country name |
| `Date` | Date of the recorded measurement |
| `Time` | Time of the recorded measurement |
| `CO_GT` | Carbon Monoxide measurement |
| `PT08_S1_CO` | CO sensor response |
| `NMHC_GT` | Non-methane hydrocarbons measurement |
| `C6H6_GT` | Benzene measurement |
| `PT08_S2_NMHC` | NMHC sensor response |
| `Nox_GT` | Nitrogen oxides measurement |
| `PT08_S3_Nox` | NOx sensor response |
| `T` | Temperature |
| `RH` | Relative humidity |
| `AH` | Absolute humidity |
| `CO_level` | CO category |
| `Year` | Year |
| `Month` | Month |
| `Day` | Day |
| `Hour` | Hour |
| `Weekday` | Day of the week |
| `Is_Weekend` | Weekend indicator |
| `Season` | Season |
| `Time_of_Day` | Time period category |

The dataset also contains additional sensor-related columns.

## 🔍 6. Data Loading and Exploration Using Pandas

The CSV dataset is loaded with:

```python
df = pd.read_csv('AirQuality_300_final_no_city.csv')
```

The notebook uses the following Pandas operations:

| Function / Attribute | Purpose |
|---|---|
| `df` | Displays the complete DataFrame |
| `df.head()` | Displays the first 5 rows |
| `df.head(10)` | Displays the first 10 rows |
| `df.tail()` | Displays the last 5 rows |
| `df.tail(10)` | Displays the last 10 rows |
| `df.dtypes` | Displays the data type of each column |
| `df.isnull().sum()` | Counts missing values in each column |
| `df.dropna(inplace=True)` | Removes rows containing missing values |
| `df.info()` | Displays DataFrame information |
| `df['CO_level'].unique()` | Displays unique CO categories |

These operations help understand the structure and quality of the dataset before analysis.

## 🧹 7. Data Cleaning and Date Conversion

### Missing Value Checking

```python
df.isnull().sum()
```

This checks the number of missing values in each column.

### Removing Missing Values

```python
df.dropna(inplace=True)
```

This removes rows containing missing values from the DataFrame.

### Converting Date into Datetime

```python
df['Date'] = pd.to_datetime(df['Date'], format='mixed')
```

The Date column is converted into Pandas datetime format.

### Checking Date Data Type

```python
df['Date'].dtype
```

The notebook also checks the updated data types and displays the converted date values.

## 🔢 8. NumPy Analysis

NumPy is used for numerical calculations on the `CO_GT` column.

### Creating a NumPy Array

```python
arr = np.array(df['CO_GT'].dropna())
print(arr)
```

This converts the CO measurement values into a NumPy array.

### Statistical Functions

```python
print("Sum:", np.sum(arr))
print("Mean:", np.mean(arr))
print("Median:", np.median(arr))
print("Minimum:", np.min(arr))
print("Maximum:", np.max(arr))
print("Standard Deviation:", np.std(arr))
print("Variance:", np.var(arr))
```

| NumPy Function | Purpose |
|---|---|
| `np.sum()` | Calculates the total |
| `np.mean()` | Calculates the average |
| `np.median()` | Finds the middle value |
| `np.min()` | Finds the minimum value |
| `np.max()` | Finds the maximum value |
| `np.std()` | Calculates standard deviation |
| `np.var()` | Calculates variance |
| `np.array()` | Creates a NumPy array |

### Array Indexing

```python
print("First Value:", arr[0])
print("Last Value:", arr[-1])
```

This displays the first and last values of the array.

### Column Mean Calculation

```python
columns = df[['CO_GT', 'T', 'RH', 'AH']].dropna()
print(np.mean(columns.to_numpy(), axis=0))
```

This calculates the mean of the selected numerical columns: `CO_GT`, `T`, `RH`, and `AH`.

## 📈 9. Matplotlib Data Visualizations

Matplotlib is used to create the following charts.

### 1. Line Plot — Date vs CO Level

Displays the relationship between the Date and CO-level category.

### 2. Line Plot — CO Concentration Over Date

Displays CO measurement values over time using the `Date` and `CO_GT` columns.

### 3. Bar Chart — CO Level Category Count

Displays the number of records in each `CO_level` category.

### 4. Histogram — CO Distribution

Displays the frequency distribution of `CO_GT` values using 10 bins.

### 5. Scatter Plot — Temperature vs CO Concentration

Displays the relationship between temperature (`T`) and CO concentration (`CO_GT`).

### 6. Pie Chart — CO Level Category Percentage

Displays the percentage distribution of the available `CO_level` categories.

### 7. Correlation Heatmap — Air Quality Measurements

Calculates the correlation matrix of numerical columns and displays it as a heatmap using Matplotlib.

## 🎨 10. Seaborn Data Visualizations

The notebook sets the Seaborn theme:

```python
sns.set_theme(style="whitegrid")
```

It creates the following charts:

### 1. Seaborn Line Plot

- X-axis: `Date`
- Y-axis: `CO_GT`
- Displays CO concentration over time.

### 2. Seaborn Count Plot

- X-axis: `CO_level`
- Displays the count of records in each CO category.

### 3. Seaborn Histogram

- Column: `CO_GT`
- Uses 10 bins and `kde=True`.
- Displays the CO distribution with a KDE curve.

### 4. Seaborn Scatter Plot

- X-axis: `T`
- Y-axis: `CO_GT`
- `hue='CO_level'` distinguishes points by CO category.

### 5. Seaborn Heatmap

- Uses the correlation matrix of numerical columns.
- `annot=True` displays correlation values.
- Uses the `coolwarm` color map.

## 📉 11. Correlation Analysis

The notebook selects numerical columns and calculates their correlation:

```python
corr = df.select_dtypes(include='number').corr()
```

The correlation matrix is visualized with both Matplotlib and Seaborn heatmaps. This helps examine how numerical air-quality measurements are related to one another.

## ▶️ 12. How to Run the Project

### Step 1: Install Python

Install Python on your computer.

### Step 2: Install Required Libraries

Open the terminal and run:

```bash
pip install numpy pandas matplotlib seaborn jupyter
```

### Step 3: Keep Project Files Together

Keep these files in the same folder:

- `finel-project.ipynb`
- `AirQuality_300_final_no_city.csv`

### Step 4: Open Jupyter Notebook

Run:

```bash
jupyter notebook
```

### Step 5: Run the Notebook

Open `finel-project.ipynb` and execute the cells from top to bottom.

## 📚 13. Concepts Covered

This project demonstrates practical use of:

- Python library imports.
- CSV file reading.
- Pandas DataFrame.
- `head()` and `tail()`.
- Data types and DataFrame information.
- Missing-value checking and removal.
- Date-time conversion.
- Unique values.
- NumPy arrays and indexing.
- NumPy statistical functions.
- Column-wise mean calculation.
- Matplotlib line, bar, histogram, scatter, and pie charts.
- Correlation matrix and heatmap.
- Seaborn line plot, count plot, histogram, scatter plot, and heatmap.

## ✅ 14. Conclusion

The Air Quality Data Analysis project demonstrates how Python libraries can be used to explore, clean, process, and visualize air-quality data. Pandas is used for dataset handling, NumPy is used for numerical calculations, Matplotlib is used for plotting, and Seaborn is used for statistical visualization.

The charts and calculations provide different ways to examine CO measurements, CO categories, temperature, and relationships between numerical columns.

## ⚠️ 15. Important Notes

- The notebook expects the CSV file name to be exactly `AirQuality_300_final_no_city.csv`.
- The CSV file should be in the same folder as the notebook.
- Run notebook cells in order because later cells depend on variables created earlier.
- The notebook reloads the CSV before the Seaborn section and converts dates using `errors='coerce'`.
- The notebook contains `df.describe` without parentheses, so that cell references the method rather than displaying descriptive statistics.
- This documentation describes the code present in the uploaded notebook. It does not add unperformed machine-learning models or claim specific findings that the notebook does not calculate.

---

## 👩‍💻 Project Information

**Project Name:** Air Quality Data Analysis  
**Main File:** `finel-project.ipynb`  
**Dataset:** `AirQuality_300_final_no_city.csv`  
**Libraries:** NumPy, Pandas, Matplotlib, Seaborn  
**Environment:** Jupyter Notebook
**Author:** padsala sneha

⭐ **Thank you for visiting this project!**

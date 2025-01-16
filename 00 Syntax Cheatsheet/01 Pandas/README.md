# PANDAS SYNTAX CHEATSHEET

---

## **1. Importing Pandas**
```python
import pandas as pd
```

---

## **2. Loading Data**
```python
# Load CSV file
df = pd.read_csv('data.csv')

# Load Excel file
df = pd.read_excel('data.xlsx')
```

---

## **3. Quick Data Overview**
```python
# View first few rows
df.head()

# View last few rows
df.tail()

# Get dataframe shape (rows, columns)
df.shape

# Summary statistics
df.describe()

# Data types of each column
df.dtypes

# Check for missing values
df.isnull().sum()
```

---

## **4. Selecting Data**
```python
# Select a single column
df['column_name']

# Select multiple columns
df[['col1', 'col2']]

# Select rows using index
df.iloc[0]  # First row
df.iloc[1:5]  # Rows 1 to 4

# Select rows/columns by label
df.loc[0, 'column_name']  # Specific cell
df.loc[:, 'col1':'col3']  # Columns col1 to col3
```

---


## **5. Filtering Data**
```python
# Filter rows based on condition
df[df['column_name'] > 50]

# Multiple conditions
df[(df['col1'] > 50) & (df['col2'] < 100)]

# Using .query()
df.query('col1 > 50 and col2 < 100')
```

---


## **6. Handling Missing Data**
```python
# Drop rows with missing values
df.dropna()

# 1. Fill missing values
df['column_name'] = df['column_name'].fillna(value=0)

# 2. Fill with Mean 
# Fill missing values in a specific column with the mean of that column
df['column_name'] = df['column_name'].fillna(df['column_name'].mean())

# Fill missing values in all numeric columns with the mean
df.fillna(df.mean(), inplace=True)

# 3. Fill with Median
# Fill missing values in a specific column with the median of that column
df['column_name'] = df['column_name'].fillna(df['column_name'].median())

# Fill missing values in all numeric columns with the median
df.fillna(df.median(), inplace=True)


## 4. Fill with Mode
# Fill missing values in a specific column with the mode of that column
df['column_name'] = df['column_name'].fillna(df['column_name'].mode()[0])

# Fill missing values in all columns with the mode
for col in df.columns:
    df[col] = df[col].fillna(df[col].mode()[0])
```
---


## **7. Creating/Modifying Columns**
```python
# Add a new column
df['new_col'] = df['col1'] + df['col2']

# Modify an existing column
df['col1'] = df['col1'] * 2

# Apply a custom function
df['col1'] = df['col1'].apply(lambda x: x**2)
```

---


## **8. Grouping and Aggregation**
```python
# Group by and calculate statistics
df.groupby('category')['value'].mean()

# Multiple aggregations
df.groupby('category').agg({'value': ['mean', 'sum']})
```

---


## **9. Sorting**
```python
# Sort by a column
df.sort_values('column_name')

# Sort in descending order
df.sort_values('column_name', ascending=False)
```

---


## **10. Merging and Joining**
```python
# Merge two dataframes
pd.merge(df1, df2, on='common_column', how='inner')  # 'left', 'right', 'outer'

# Concatenate dataframes
pd.concat([df1, df2], axis=0)  # axis=1 for columns
```

---


## **11. Resetting and Setting Index**
```python
# Reset index
df.reset_index(drop=True)

# Set a column as the index
df.set_index('column_name')
```

---


## **12. Exporting Data**
```python
# Save to CSV
df.to_csv('output.csv', index=False)

# Save to Excel
df.to_excel('output.xlsx', index=False)
```

---
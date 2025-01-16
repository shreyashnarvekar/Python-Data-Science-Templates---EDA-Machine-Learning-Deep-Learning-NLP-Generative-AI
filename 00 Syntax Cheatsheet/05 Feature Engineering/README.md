# FEATURE ENGINEERING SYNTAX CHEATSHEET

---

## **1. Importing Basic Libraries**
```python
import pandas as pd
import numpy as np
from sklearn.preprocessing import LabelEncoder, MinMaxScaler, StandardScaler, PolynomialFeatures
from sklearn.feature_selection import SelectKBest, f_classif
```

---

## **2. Handling Missing Values**

### Fill Missing Values with Mean, Median, or Mode
```python
# Fill missing values with the mean of the column
df['column_name'] = df['column_name'].fillna(df['column_name'].mean())

# Fill missing values with the median of the column
df['column_name'] = df['column_name'].fillna(df['column_name'].median())

# Fill missing values with the mode of the column
df['column_name'] = df['column_name'].fillna(df['column_name'].mode()[0])
```

### Drop Rows with Missing Values
```python
# Drop rows where any column has missing values
df.dropna(inplace=True)

# Drop rows where specific columns have missing values
df.dropna(subset=['column_name_1', 'column_name_2'], inplace=True)
```

---

## 3. Encoding Categorical Variables

### Label Encoding (Convert categorical labels to numbers)
```python
le = LabelEncoder()
df['column_name'] = le.fit_transform(df['column_name'])
```

### One-Hot Encoding (Convert categorical columns to dummy/indicator variables)
```python
df_encoded = pd.get_dummies(df, columns=['column_name'], drop_first=True)
```

### Ordinal Encoding (Assign numerical values based on order)
```python
ordinal_mapping = {'low': 1, 'medium': 2, 'high': 3}
df['column_name_encoded'] = df['column_name'].map(ordinal_mapping)
```

---


## **4. Train-Test Split**
# Split data into features and target
X = df.drop(columns=['target_column'])
y = df['target_column']

# Perform train-test split (80% train, 20% test)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)


---


## **5. Feature Scaling (Normalization and Standardization)**

### Min-Max Scaling (Normalization)
```python
# Initialize the MinMaxScaler
scaler = MinMaxScaler()

# Fit and transform the scaler on X_train
X_train = scaler.fit_transform(X_train)

# Transform X_test using the already fitted scaler
X_test = scaler.transform(X_test)
```

### Z-Score Standardization (Standardization)
```python
# Initialize the Standard Scaler
scaler = StandardScaler()

# Fit and transform the scaler on X_train
X_train = scaler.fit_transform(X_train)

# Transform X_test using the already fitted scaler
X_test = scaler.transform(X_test)
```

---


## **6. Feature Creation**

### Create New Feature (Based on existing columns)
```python
df['new_feature'] = df['column_name_1'] + df['column_name_2']  # Sum of two columns
df['new_feature'] = df['column_name_1'] * df['column_name_2']  # Product of two columns
df['new_feature'] = df['column_name_1'] / df['column_name_2']  # Division of two columns
```

### Date-Time Features (Extract year, month, day, etc. from a DateTime column)
```python
df['year'] = df['date_column'].dt.year
df['month'] = df['date_column'].dt.month
df['day'] = df['date_column'].dt.day
df['weekday'] = df['date_column'].dt.weekday
```

---


## **7. Feature Selection**

### Select Features Based on Correlation
```python
correlation_matrix = df.corr()

# Select highly correlated features
highly_correlated_features = correlation_matrix[correlation_matrix > 0.8]
```

### Drop Unwanted Columns (Features)
```python
df.drop(columns=['column_name_to_drop'], inplace=True)
```

### SelectKBest (Select top k features using statistical tests)
```python
X = df.drop(columns=['target_column'])
y = df['target_column']

selector = SelectKBest(f_classif, k=5)
X_new = selector.fit_transform(X, y)
```

---


## **8. Polynomial Features**

### Feature Engineering through Polynomial Transformation
```python
poly = PolynomialFeatures(degree=2)
X_poly = poly.fit_transform(X)  # Transform the feature matrix X into polynomial features
```

---


## **9. Binning (Discretization of continuous variables)**

### Binning Continuous Variable into Categories
```python
bins = [0, 10, 20, 30, 40]
labels = ['0-10', '10-20', '20-30', '30-40']
df['binned_column'] = pd.cut(df['column_name'], bins=bins, labels=labels)
```

---
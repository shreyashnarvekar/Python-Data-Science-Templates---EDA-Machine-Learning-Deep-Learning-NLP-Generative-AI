# MATPLOTLIB SYNTAX CHEATSHEET

---

## **1. Importing Seaborn**
```python
import seaborn as sns
```

---

## **2. Basic Plotting Functions**

### Line Plot
```python
sns.lineplot(x='column_name_1', y='column_name_2', data=df)
plt.xlabel('X-axis Label')  # Set X-axis label
plt.ylabel('Y-axis Label')  # Set Y-axis label
plt.title('Line Plot Title')  # Set plot title
plt.show()
```

### Scatter Plot
```python
sns.scatterplot(x='column_name_1', y='column_name_2', data=df)
plt.xlabel('X-axis Label')  # Set X-axis label
plt.ylabel('Y-axis Label')  # Set Y-axis label
plt.title('Scatter Plot Title')  # Set plot title
plt.show()
```

### Bar Plot
```python
sns.barplot(x='column_name_1', y='column_name_2', data=df)
plt.xlabel('X-axis Label')  # Set X-axis label
plt.ylabel('Y-axis Label')  # Set Y-axis label
plt.title('Bar Plot Title')  # Set plot title
plt.show()
```

### Box Plot
```python
sns.boxplot(x='column_name_1', y='column_name_2', data=df)
plt.xlabel('X-axis Label')  # Set X-axis label
plt.ylabel('Y-axis Label')  # Set Y-axis label
plt.title('Box Plot Title')  # Set plot title
plt.show()
```

### Histogram / Distribution Plot
```python
sns.histplot(df['column_name'], bins=10, kde=True)
plt.xlabel('X-axis Label')  # Set X-axis label
plt.ylabel('Frequency')  # Set Y-axis label
plt.title('Histogram Title')  # Set plot title
plt.show()
```

---

## 3. Customizing Plots

### Adjusting Plot Style
```python
sns.set_style("whitegrid")  # Options: white, dark, whitegrid, darkgrid, ticks
```

### Adding Grid
```python
sns.set(rc={'figure.figsize':(10, 6)})  # Adjust figure size (width, height)
```

---

## **4. Visualizing Relationships Between Variables**

### Pair Plot
```python
sns.pairplot(df)
```

### Heatmap
```python
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
```

### Violin Plot
```python
sns.violinplot(x='column_name_1', y='column_name_2', data=df)
```

---


## **5. Categorical Plots**

### Count Plot
```python
sns.countplot(x='column_name', data=df)
```

### Catplot (For various categorical plots)
```python
sns.catplot(x='column_name', y='target_column', kind='box', data=df)
```

### Swarm Plot
```python
sns.swarmplot(x='column_name', y='column_name_2', data=df)
```

---


## **6. Regression Plots**

### Simple Linear Regression Plot
```python
sns.regplot(x='column_name_1', y='column_name_2', data=df)
```

### Polynomial Regression Plot (with different degree)
```python
sns.regplot(x='column_name_1', y='column_name_2', data=df, order=2)
```

---


## **7. FacetGrid and Subplots**

### FacetGrid for Multiple Plots
```python
g = sns.FacetGrid(df, col='category_column')
g.map(sns.scatterplot, 'column_name_1', 'column_name_2')
```

### Multiple Plots in a Grid (Subplots)
```python
g = sns.FacetGrid(df, col='column_name', row='column_name_2')
g.map(sns.scatterplot, 'column_name_1', 'column_name_3')
```

---


## **8. Styling and Themes**

### Set Color Palette
```python
sns.set_palette("pastel")  # Options: deep, muted, pastel, dark, colorblind
```

### Set Context (For controlling the scale)
```python
sns.set_context("notebook")  # Options: paper, notebook, talk, poster
```

---


## **9. Saving Plots**
```python
sns.scatterplot(x='column_name_1', y='column_name_2', data=df)
plt.savefig('plot.png')  # Save plot to a file
```

---


## **10. Plotting with Seaborn and Matplotlib Together**

You can use Seaborn's plotting functions with Matplotlib’s features for additional customization.

```python
sns.scatterplot(x='column_name_1', y='column_name_2', data=df)
plt.title('Scatter Plot')
plt.xlabel('X-axis Label')
plt.ylabel('Y-axis Label')
plt.show()
```

---
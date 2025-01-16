# MATPLOTLIB SYNTAX CHEATSHEET

---

## **1. Importing Matplotlib**
```python
import matplotlib.pyplot as plt
```

---

## **2. Creating Basic Plots**

### Line Plot
```python
plt.plot(x, y)
plt.xlabel('X-axis Label')
plt.ylabel('Y-axis Label')
plt.title('Line Plot Title')
plt.show()
```

### Scatter Plot
```python
plt.scatter(x, y, color='blue', marker='o')
plt.xlabel('X-axis Label')
plt.ylabel('Y-axis Label')
plt.title('Scatter Plot Title')
plt.show()
```

### Bar Plot
```python
plt.bar(x, y, color='green')
plt.xlabel('X-axis Label')
plt.ylabel('Y-axis Label')
plt.title('Bar Plot Title')
plt.show()
```

### Histogram
```python
plt.hist(data, bins=10, color='red', edgecolor='black')
plt.xlabel('Bins')
plt.ylabel('Frequency')
plt.title('Histogram Title')
plt.show()
```

---

## 3. Customizing Plots

### Adding Legends
```python
plt.plot(x, y, label='Line 1')
plt.plot(x2, y2, label='Line 2')
plt.legend(loc='upper right')  # Location of legend
plt.show()
```

### Adding Grid
```python
plt.plot(x, y)
plt.grid(True)  # Display grid
plt.show()
```

### Customize Axis Limits
```python
plt.plot(x, y)
plt.xlim(0, 10)  # Set x-axis limits
plt.ylim(0, 20)  # Set y-axis limits
plt.show()
```

---

## **4. Subplots - (Creating Multiple Plots in One Figure)**
```python
plt.subplot(2, 2, 1)  # 2 rows, 2 columns, 1st subplot
plt.plot(x, y)

plt.subplot(2, 2, 2)  # 2 rows, 2 columns, 2nd subplot
plt.scatter(x, y)

plt.subplot(2, 2, 3)  # 2 rows, 2 columns, 3rd subplot
plt.bar(x, y)

plt.subplot(2, 2, 4)  # 2 rows, 2 columns, 4th subplot
plt.hist(data, bins=10)

plt.tight_layout()  # Adjust layout
plt.show()
```

---


## **5. Plotting Multiple Lines**
```python
plt.plot(x, y, label='Line 1')
plt.plot(x2, y2, label='Line 2', linestyle='--')
plt.xlabel('X-axis Label')
plt.ylabel('Y-axis Label')
plt.title('Multiple Lines')
plt.legend()
plt.show()
```

---


## **6. Saving Figures**
```python
# Save the current plot to a file
plt.plot(x, y)
plt.savefig('plot.png')  # Save as PNG file
plt.savefig('plot.pdf')  # Save as PDF file
plt.show()
```

---


## **7. Customizing Plot Appearance**

### Set Figure Size
```python
plt.figure(figsize=(8, 6))  # Set figure size (width, height in inches)
plt.plot(x, y)
plt.show()
```

### Change Plot Color and Style
```python
plt.plot(x, y, color='purple', linestyle='-', marker='o')  # Color, Line style, and Marker style
plt.show()
```

---


## **8. Pie Chart**
```python
labels = ['Category 1', 'Category 2', 'Category 3']
sizes = [30, 40, 30]
plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=90)
plt.title('Pie Chart Title')
plt.show()
```

---


## **9. Box Plot**
```python
plt.boxplot(data)
plt.title('Box Plot Title')
plt.show()
```

---


## **10. Plotting with Seaborn (Bonus for Advanced Plotting)**

Seaborn is built on top of Matplotlib and offers advanced plotting features.

```python
import seaborn as sns

# Example of a seaborn plot
sns.heatmap(data, annot=True, cmap='coolwarm', cbar=True)
plt.title('Heatmap Title')
plt.show()
```

---
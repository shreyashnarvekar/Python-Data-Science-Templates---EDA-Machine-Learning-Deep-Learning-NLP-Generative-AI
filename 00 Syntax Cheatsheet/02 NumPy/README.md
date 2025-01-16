# NUMPY SYNTAX CHEATSHEET

---

## **1. Importing NumPy**
```python
import numpy as np
```

---

## **2. Creating Arrays**
```python
# Create a 1D array
np.array([1, 2, 3, 4])

# Create a 2D array
np.array([[1, 2, 3], [4, 5, 6]])

# Create an array of zeros
np.zeros((3, 3))

# Create an array of ones
np.ones((2, 4))

# Create an array of random values
np.random.random((3, 3))

# Create an array with evenly spaced values
np.arange(0, 10, 2)  # Start at 0, end before 10, step of 2

# Create an array with a specific range and number of points
np.linspace(0, 1, 5)  # 5 points between 0 and 1
```

---

## **3. Inspecting Arrays**
```python
# Shape of the array
arr.shape

# Number of dimensions
arr.ndim

# Total number of elements
arr.size

# Data type of elements
arr.dtype

# View the first few elements of a large array (like head for Pandas)
arr[:5]
```

---

## **4. Reshaping and Manipulating Arrays**
```python
# Reshape an array
arr2d.reshape(3, 2)

# Flatten a 2D array into 1D
arr2d.flatten()

# Transpose a 2D array
arr2d.T
```

---


## **5. Basic Array Operations**
```python
# Element-wise addition, subtraction, multiplication, and division
arr1 + arr2
arr1 - arr2
arr1 * arr2
arr1 / arr2

# Dot product of two arrays
np.dot(arr1, arr2.T)

# Sum of all elements
arr.sum()

# Row-wise and column-wise sum
arr2d.sum(axis=1)  # Sum along rows
arr2d.sum(axis=0)  # Sum along columns

# Minimum and maximum
arr.min()
arr.max()

# Mean, median, and standard deviation
arr.mean()
np.median(arr)
arr.std()
```

---


## **6. Indexing and Slicing**
```python
# Access single elements
arr[2]  # Third element in 1D array
arr2d[1, 2]  # Element in second row, third column

# Slicing arrays
arr[1:4]  # Elements from index 1 to 3
arr2d[:, 1]  # All rows, second column
arr2d[0:2, 1:3]  # Subarray from rows 0-1 and columns 1-2
```

---


## **7. Boolean Indexing and Filtering**
```python
# Boolean condition
arr > 2  # Array of True/False

# Filter elements
arr[arr > 2]
```

---


## **8. Random Number Generation**
```python
# Random integers between a range
np.random.randint(0, 10, size=(3, 3))

# Random floats in the range [0.0, 1.0)
np.random.rand(3, 3)

# Normal distribution (mean=0, std=1)
np.random.randn(3, 3)

# Set a random seed for reproducibility
np.random.seed(42)
```

---


## **9. Handling Missing or Invalid Data**
```python
# Replace invalid values with NaN
np.array([1, 2, np.nan, 4])

# Check for NaN values
np.isnan(arr_with_nan)

# Replace NaN values with a specific number
np.nan_to_num(arr_with_nan, nan=0)
```

---


## **10. Saving and Loading Arrays**
```python
# Save to a file
np.save('array_file.npy', arr)

# Load from a file
np.load('array_file.npy')

# Save to a text file
np.savetxt('array_file.txt', arr)

# Load from a text file
np.loadtxt('array_file.txt')
```

---
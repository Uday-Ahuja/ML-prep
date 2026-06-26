## NumPy

### What is NumPy

NumPy (Numerical Python) is Python's core library for numerical computing. It provides the **ndarray** (n-dimensional array) — a fixed-type, contiguous-memory data structure that is significantly faster and more memory-efficient than Python lists.

**Why faster than lists:**
- Python list stores pointers to objects scattered in memory; each integer takes ~28 bytes
- NumPy array stores raw data in contiguous memory blocks; each int64 takes 8 bytes
- Operations run in optimized C under the hood, not Python loops

Memory example: 100 Python ints ≈ 2800 bytes vs same NumPy array ≈ 800 bytes. Speed difference becomes dramatic at scale (10M element addition: lists ~4.4s vs NumPy ~0.11s).

### Creating Arrays

`np.array(list)` — converts a Python list to ndarray. Pass a nested list for 2D.

**Pre-filled arrays:**
- `np.zeros((rows, cols))` — all zeros, float64 by default
- `np.ones((rows, cols))` — all ones
- `np.identity(n)` — n×n identity matrix (diagonal = 1, rest = 0)

**Range-based arrays:**
- `np.arange(n)` — integers 0 to n-1 (note: `arrange` is wrong, common mistake)
- `np.arange(start, stop, step)` — like Python range
- `np.linspace(start, stop, n)` — n evenly spaced floats including both endpoints

**Copying:** `arr.copy()` creates an independent copy. Direct assignment (`b = a`) creates a view — modifying b modifies a.

### Array Attributes

- `arr.shape` — tuple of dimensions, e.g. `(3, 3)` for 3×3 matrix, `(5,)` for 1D
- `arr.ndim` — number of dimensions
- `arr.size` — total number of elements
- `arr.dtype` — data type (`int64`, `float64`, etc.)
- `arr.itemsize` — bytes per element (int64 = 8, float64 = 8)
- `arr.astype('int')` — returns new array with converted dtype

### Reshaping

`arr.reshape(rows, cols)` — changes shape without changing data. Total elements must stay the same (e.g. 24 elements → 6×4 or 4×6 or 2×12).

### Indexing and Slicing

**1D:** Same as Python lists — `arr[2]`, `arr[1:4]`, `arr[-1]`

**2D syntax: `arr[row, col]`**
- `arr[:, 2]` — entire column 2
- `arr[1:3, 0:2]` — row slice × column slice
- `arr[4:, 2:]` — rows from 4 onwards, cols from 2 onwards

**Fancy indexing:** Pass a list of non-contiguous indices — `arr[[0, 2, 4]]` returns rows 0, 2, 4. Works where slicing can't.

### Iteration

- `for i in arr` — iterates row by row for 2D arrays (each `i` is a row array)
- `for i in np.nditer(arr)` — iterates element by element regardless of dimensions

### Arithmetic Operations

Operations between arrays of the same shape are **element-wise** by default.

- `arr1 + arr2`, `arr1 - arr2`, `arr1 * arr2` — element-wise
- `arr1 > 3` — returns boolean array (element-wise comparison)
- `arr3.dot(arr4)` — true matrix multiplication (requires compatible shapes: m×n dot n×p → m×p)

### Aggregate Functions

All can be applied globally or along an axis. `axis=0` operates down columns (per-column result), `axis=1` operates across rows (per-row result).

- `arr.max()`, `arr.min()`, `arr.sum()`, `arr.mean()`, `arr.std()`
- `np.median(arr)` — median (not a method, called as function)
- `np.sin(arr)`, `np.exp(arr)` — universal functions (ufuncs), apply element-wise to entire array

### Random Module (`np.random`)

Used constantly in ML for generating test data, weight initialization, and simulation.

- `np.random.rand(rows, cols)` — uniform floats in [0, 1)
- `np.random.randint(low, high, size)` — random integers; `high` is exclusive
- `np.random.randn(rows, cols)` — samples from standard normal distribution (mean=0, std=1)
- `np.random.random(size)` — alias for rand, floats in [0.0, 1.0)

Use `np.random.seed(n)` to fix randomness for reproducible results — important in ML experiments.

### Shape Manipulation

- `arr.ravel()` — flattens to 1D array
- `arr.transpose()` — swaps rows and columns; also accessible as `arr.T`
- `np.hstack((a, b))` — stack arrays horizontally (column-wise); shapes must match on rows
- `np.vstack((a, b))` — stack arrays vertically (row-wise); shapes must match on cols
- `np.hsplit(arr, n)` — split array into n equal parts along columns

### Plotting with NumPy + Matplotlib

NumPy is typically the data source; Matplotlib does the rendering.

```python
x = np.linspace(-40, 40, 100)
y = np.sin(x)
plt.plot(x, y)   # smooth sine wave

y2 = x*x + 2*x + 6
plt.plot(x, y2)  # parabola
```

`%matplotlib inline` — Jupyter magic command to render plots inside the notebook.

---

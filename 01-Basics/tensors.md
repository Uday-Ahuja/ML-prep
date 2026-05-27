## Tensors

A **tensor** is a general-purpose data structure that unifies scalars, vectors, matrices, and higher-dimensional arrays under one framework. Everything in ML — inputs, weights, outputs — is a tensor.

---

## Tensor Dimensions and Rank

**Rank** (also called **ndim** or **number of axes**) is the number of dimensions a tensor has. A single number has rank 0; a list has rank 1; a grid has rank 2; and so on.

> Important distinction: a **1-D tensor** with 4 elements is a *1-D tensor* (rank 1) but a *4-D vector* — the tensor dimension refers to rank, the vector dimension refers to element count.

**Shape** describes the size along each axis as a tuple (rows, cols, ...). **Size** is the product of all shape values; for a scalar, size is always 1.

---

## Tensor Types by Rank

### 0-D Tensor (Scalar)
A single numeric value. No axes. Example: `[2]`, `[3.14]`. ndim = 0, size = 1.

### 1-D Tensor (Vector)
A flat array of values along one axis. Example: `[1, 2, 3, 4]`. ndim = 1.

### 2-D Tensor (Matrix)
A grid of values with rows and columns. Example:
```
[[1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]]
```
ndim = 2, shape = (3, 3).

### N-D Tensor
Any tensor with rank > 2. Each additional dimension wraps the previous structure in a new axis.

---

## Worked Examples by Rank

### 1-D Tensor — Student Feature Vector
For 1000 students with attributes `cgpa`, `iq`, `state` (where state: 0 = WB, 1 = other), one student's feature vector is:

`[8.1, 91, 0]` → 1-D tensor (rank 1), 3-D vector (3 elements)

Two valid representations of the dataset:
- One 1-D tensor per **row** (one vector per student)
- One 1-D tensor per **column** (one vector per feature)

### 2-D Tensor — Student Dataset Matrix
Stack all student vectors into a matrix **D** of shape `(1000, 3)` — 1000 rows (students), 3 columns (features). This is the standard tabular data format in ML.

### 3-D Tensor

**NLP — Sentence Vectorization**
Given sentences: *"hi Uday"*, *"hi Ahuja"*, *"hi Vashist"*, each word is one-hot encoded over a vocabulary of 4 words `{hi, Uday, Ahuja, Vashist}`:

```
[
  [[1,0,0,0], [0,1,0,0]],   ← "hi Uday"
  [[1,0,0,0], [0,0,1,0]],   ← "hi Ahuja"
  [[1,0,0,0], [0,0,0,1]]    ← "hi Vashist"
]
```
Shape: `(3, 2, 4)` — 3 sentences, 2 words each, 4-element one-hot vector per word.

**Time-Series — Stock Prices**
Daily high/low prices tracked over 10 years: shape `(10, 365, 2)`. The axis order is `(years, days, features)` — the days axis is the **time axis**.

### 4-D Tensor — Image Collection
A single colour image is a 3-D tensor of shape `(H, W, 3)` — height × width × RGB channels. A batch of images becomes a 4-D tensor of shape `(N, H, W, 3)` where N is the number of images.

### 5-D Tensor — Video Collection
A single video at 30fps for 60 seconds = 1800 frames, each frame at 480×720 with 3 channels → shape `(1800, 480, 720, 3)`. A collection of 4 such videos: shape `(4, 1800, 480, 720, 3)`.

Raw float32 size: $4 \times 1800 \times 480 \times 720 \times 3 \times 4\ \text{bytes} \approx 27\ \text{GB}$

This is why video encoding formats (mp4, mkv, mpeg) exist — raw tensor representation is computationally infeasible for ML pipelines without compression.

---
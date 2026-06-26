## Matplotlib — Fundamentals & Advanced

### Core Concepts

Matplotlib is Python's primary plotting library. Import convention is `import matplotlib.pyplot as plt`. In Jupyter, plots render inline automatically — `plt.show()` is only needed in IDEs like PyCharm/VS Code.

### Line Plot (`plt.plot`)

Used for visualizing trends over a continuous variable (time series, comparisons). Basic usage takes x and y as lists or Series.

Key parameters:
- `color` — named colors ('green', 'black') or hex
- `linestyle` — `'solid'`, `'dashed'`, `'dotted'`, `'dashdot'`
- `linewidth` — thickness of line
- `marker` — shape at data points (e.g. `'D'` for diamond), `markersize` controls size
- `label` — text used in legend

Essential plot-level functions:
- `plt.title()`, `plt.xlabel()`, `plt.ylabel()` — text labels
- `plt.legend()` — renders labels; default `loc='best'` auto-places in empty space
- `plt.grid()` — adds grid lines
- `plt.ylim(min, max)` / `plt.xlim()` — axis limits, useful when outliers flatten the rest of the curve
- `plt.savefig('filename.png')` — saves figure to disk; call before `plt.show()`

### Scatter Plot (`plt.scatter`)

Used for bivariate analysis between two numerical columns to find correlation or clustering patterns.

Key parameters:
- `c` — color by a numeric column (maps values to colors); pair with `cmap` for color themes (`'viridis'`, `'summer'`, `'winter'`)
- `plt.colorbar()` — adds color scale legend when using `c`
- `alpha` — opacity (0 to 1), useful when points overlap
- `s` — marker size, can be mapped to a third variable (bubble chart effect)
- `plt.figure(figsize=(width, height))` — must be called before plotting to set canvas size

**Annotations:**
- `plt.text(x, y, label)` — adds text at a coordinate; loop over DataFrame rows to label each point
- `plt.axhline(value)` / `plt.axvline(value)` — draws horizontal/vertical reference lines; useful for thresholds (e.g. SR > 130, Avg > 30)

### Bar Chart (`plt.bar`)

Used for categorical vs numerical comparisons.

- Basic: `plt.bar(x_categories, y_values)`
- Multiple bars (grouped): manually offset x positions using `np.arange(n) - 0.3`, `np.arange(n)`, `np.arange(n) + 0.3` with matching `width=0.3` — tedious in raw Matplotlib
- `plt.xticks(old_positions, new_labels)` — replaces numeric x-axis with category names
- `plt.xticks(rotation='vertical')` — rotates labels for readability when names are long
- Stacked bar: use `bottom` parameter — second bar starts where first ends, third starts at sum of first two

### Histogram (`plt.hist`)

Univariate analysis for numerical columns. Shows frequency distribution (how many values fall in each range/bin).

- `bins` — either an int (number of bins) or a list defining exact bin edges
- `log=True` — logarithmic y-scale; use when one bin is orders of magnitude larger than others, making smaller bins invisible

### Pie Chart (`plt.pie`)

Shows contribution of each category as a proportion of the whole. Best for categorical vs numerical when you care about relative share.

- `labels` — category names
- `autopct='%0.1f%%'` — shows percentage on each slice
- `colors` — list of colors matching slice order
- `explode` — list of float offsets; pulls a slice outward for emphasis
- `shadow=True` — adds drop shadow

### Styles

`plt.style.available` lists all built-in styles. Apply with `plt.style.use('stylename')` — affects all subsequent plots in the session. Common options: `'ggplot'`, `'fivethirtyeight'`, `'dark_background'`, `'seaborn-v0_8'`.

### Subplots (`plt.subplots`)

Two syntaxes exist — `plt` (stateless, sequential calls) and `fig, ax` (object-oriented, explicit).

**Object-oriented style (preferred for multiple plots):**
```python
fig, ax = plt.subplots(nrows=2, ncols=1, sharex=True)
ax[0].scatter(...)
ax[0].set_title(...)
ax[1].scatter(...)
```
`sharex=True` links x-axes so zooming/panning one affects all. Use `ax[row][col]` indexing for 2D grids.

### Pandas `.plot()` Integration

Pandas DataFrames have a built-in `.plot()` method that wraps Matplotlib — cleaner syntax for quick plots.

- `df.plot(kind='line'/'bar'/'hist'/'pie')`
- `df.plot(kind='bar')` on multi-column DataFrame auto-creates grouped bar chart
- `df.plot(kind='bar', stacked=True)` for stacked
- `subplots=True` — plots each column in its own subplot
- Pivot tables plot directly: `df.pivot_table(...).plot(kind='line')` — rows become x-axis, columns become separate lines

**Colored scatter for classification:** Map string labels to integers, pass as `c=` parameter. Lets you visually separate classes on a scatter — directly relevant to ML classification visualization.
---
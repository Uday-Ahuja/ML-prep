## Pandas — EDA on Real Datasets

### Loading and Inspecting Data

The first step in any EDA is loading and getting a feel for the data before touching it.

```python
data = pd.read_csv('filename.csv')
data.head()        # first 5 rows
data.shape         # (rows, cols)
data.info()        # dtypes + null counts
data.describe()    # stats for numeric cols
```

Always assign to a variable — calling `pd.read_csv()` without assignment is throwaway.

### GroupBy

**`df.groupby('col')`** splits the DataFrame into groups based on unique values of a column. Returns a GroupBy object, not a DataFrame — you need to apply an aggregation or accessor to get data out.

```python
groups = data.groupby('player_of_match')
```

Common aggregations on a GroupBy:
- `.sum()` — total per group
- `.mean()` — average per group
- `.count()` — number of rows per group
- `.max()` / `.min()` — extreme value per group

Chain `.sort_values(ascending=False)` to rank results:

```python
data.groupby('player_of_match')['win_by_runs'].sum().sort_values(ascending=False)
```

This gives total runs margin of wins for each player when they were Player of the Match — a simple impact metric.

### get_group()

`.get_group('value')` extracts all rows belonging to one specific group as a DataFrame. Useful for drilling into a single entity after groupby.

```python
groups = data.groupby('player_of_match')
groups.get_group('V Kohli')   # all matches where Kohli was POTM
```

Equivalent to filtering: `data[data['player_of_match'] == 'V Kohli']` — but cleaner when you already have a GroupBy object.

### Groupby on Multiple Columns

Pass a list to group by combinations of columns:

```python
data.groupby(['season', 'winner'])['win_by_runs'].mean()
```

### EDA Workflow Pattern

A clean order for approaching any new dataset:

1. Load and check shape, dtypes, nulls (`info()`, `describe()`)
2. Handle missing values (fill or drop)
3. Univariate analysis — distribution of individual columns
4. Bivariate analysis — relationships between two columns
5. GroupBy aggregations — performance by category
6. Sort and rank to extract insights

---
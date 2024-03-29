## 10 minutes to pandas
- Customarily, we import as follows: `import numpy as np` and `import pandas as pd`

### Object creation
- Creating a `series` by passing a list of values, letting pandas create a default integer index:
- In [3] `s = pd.Series([1, 3, 5, np.nan, 6, 8])`
- In [4] `s`
- Out[4]:
0   1.0
1   3.0
2   5.0
3   NaN
4   6.0
5   8.0
dtype: float64
- Creating a `DataFrame` by passing Numpy array, with a datetime index and labeled columns:
- In [5]: `dates = pd.date_range("20130101", periods=6)`
- In [6]: `date`
- Out[6]:
- DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
               '2013-01-05', '2013-01-06'],
              dtype='datetime64[ns]', freq='D')

In [7]: `df = pd.DataFrame(np.random.randn(6, 4), index=dates, columns=list("ABCD"))`

In [8]: `df`
Out[8]: 
                   A         B         C         D
2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
2013-01-05 -0.424972  0.567020  0.276232 -1.087401
2013-01-06 -0.673690  0.113648 -1.478427  0.524988

## Viewing Data:
- Here is how to view the top and bottom srows of the frame:
- In [13]: `df.head()`
- Out [13]: 
                   A         B         C         D
2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
2013-01-05 -0.424972  0.567020  0.276232 -1.087401
- In [14]: `df.tail(3)`
- Out [14]
                   A         B         C         D
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
2013-01-05 -0.424972  0.567020  0.276232 -1.087401
2013-01-06 -0.673690  0.113648 -1.478427  0.524988
- Display the index, columns:
- In [15]: `df.index`
- Out[15]: 
DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
               '2013-01-05', '2013-01-06'],
              dtype='datetime64[ns]', freq='D')

- In [16]: df.columns
- Out[16]: Index(['A', 'B', 'C', 'D'], dtype='object')

#### DataFrame.to_numpy()
- give a Numpy representation of the underlying data. This can be an expensive operation when your `DataFraome` has colums with diff data types, which comes down to a fundamental difference between pandas and Numpy: **Numpy arrays have one `dtype` for the entire array, while pandas `DataFrames` have one `dtype` per column.**. 
- When you call `DataFrame.to_numpy()`, pandas will find the Numpy `dtype` that can hold all of the `dtype` in the `DataFrame`.
- For `df`, our **DataFrame** of all floating-point values, `DataFrame.to_numpy()` is fast and doesn't require copying data.
- In [17]: `df.to_numpy()`
- Out[17]: 
array([[ 0.4691, -0.2829, -1.5091, -1.1356],
       [ 1.2121, -0.1732,  0.1192, -1.0442],
       [-0.8618, -2.1046, -0.4949,  1.0718],
       [ 0.7216, -0.7068, -1.0396,  0.2719],
       [-0.425 ,  0.567 ,  0.2762, -1.0874],
       [-0.6737,  0.1136, -1.4784,  0.525 ]])
- For `df2`, the **DataFrame** with mult dtypes, `DataFrame.to_numpy()` is relatively expensive.
- In [18]: `df2.to_numpy()`
- Out[18]: 
array([[1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'test', 'foo'],
       [1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'train', 'foo'],
       [1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'test', 'foo'],
       [1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'train', 'foo']],
      dtype=object)
- **NOTE:** `DataFrame.to_numpy()` does not include the index or column labels in the output.
- `describe()` shows a quick stat sum of your data:
- In [19]: `df.describe()`
- Out[19]: 
              A         B         C         D
count  6.000000  6.000000  6.000000  6.000000
mean   0.073711 -0.431125 -0.687758 -0.233103
std    0.843157  0.922818  0.779887  0.973118
min   -0.861849 -2.104569 -1.509059 -1.135632
25%   -0.611510 -0.600794 -1.368714 -1.076610
50%    0.022070 -0.228039 -0.767252 -0.386188
75%    0.658444  0.041933 -0.034326  0.461706
max    1.212112  0.567020  0.276232  1.071804
- You can also Transpose your data `df.T`, sort by axis `df.sort_index(axis=1, ascending=False)` and sort by value `df.sort_values(by="B")`

## Reference
- https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html
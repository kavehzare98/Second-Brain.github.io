202406121313
Status: #learning
Tags: [Machine Learning], [Data Science], [Python], [CSV]
# How to Read CSV Files in Python?

### Read CSV files using NumPy **genfromtxt()** method

```python {hl_lines=[3, 4, 5]}
import numpy as np

arr = np.genfromtxt(fname="sample_data.csv",
				   delimiter=", ",
				   dtype=str)
display(arr)
```
#### Additional parameter: **missing_values**
The set of strings to use incase of a missing value.
#### Issues:
This will only separate one-dimensionally, meaning each row is still one long string.

### Read CSV files using Pandas **`read_csv()`** method

```python {hl_lines=[3]}
from pandas import read_csv

d = read_csv('sample_data.csv')

df = d.values
print(df)
```
### Read CSV files using built-in Python **csv module**

```python {hl_lines=[3,4]}
import csv

with open("sample_data.csv", 'r') as x:
	sample_data = list(cvs.reader(x, delimiter=","))

sample_data = np.array(sample_data)
display(sample_data)
```
# References
Link: https://www.geeksforgeeks.org/how-to-read-csv-files-with-numpy/
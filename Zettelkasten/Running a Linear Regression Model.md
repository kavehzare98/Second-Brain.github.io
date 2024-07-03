202406141226
Status: #how-to
Tags: [Machine Learning], [Python], [Pandas]
# Running a Linear Regression Model
### 1. Importing Libraries

```python
import pandas as pd # Used for Pandas DataFrame and reading CSV file
from statistics import linear_regression, correlation 
from scipy import stats # Used for running an alternative linear regression model
import matplotlib.pyplot as plt # Used for plotting data and regression line
```

#### Notes:
- While statistics module's linear_regression allows you to force the regression line through the origin, scipy's stats.linregress does not support this feature. 
- You can only force the regression line through the origin using Python 3.12+
- Configuration worked using Conda environment

### 2. Exploratory Analysis of Data

#### Opening Data Description:

```python {hl_lines=[1, 3, 4]}
file = open("data_description.txt", 'r')

for i in file:
	print(i)
```

Output:
```txt
MSSubClass: Identifies the type of dwelling involved in the sale.	

        20	1-STORY 1946 & NEWER ALL STYLES

        30	1-STORY 1945 & OLDER

        40	1-STORY W/FINISHED ATTIC ALL AGES
        ....
```

#### Obtaining Quick Statistics
```python
data.describe()
```
Sample output:
![[Screenshot 2024-06-14 at 5.43.09 PM.png | 300]] 
### 3. Reading CSV File

```python
# Change Pandas setting to display all columns
pd.set_option('display.max_columns', None)

# Read CSV file
train_data0 = pd.read_csv("train.csv")

# Convert data to Pandas DataFrame
train_data1 = pd.DataFrame(train_data0)
display(train_data1)

# Selecting an individual cell in the table
print(train_data1.loc[2, 'MSSubClass']) # Output: 60
```
### 4. Selecting a handful of Columns

```python
train_data2 = train_data1[['LotArea', '1stFlrSF', '2ndFlrSF', 'SalePrice']]
display(train_data2)
```
### 5. Creating a New Column and assigning Formula

```python
# Creating Total Square Footage column by adding 1st Floor SF and 2nd Floor SF
train_data2['TotalSF'] = train_data2['1stFlrSF'] + train_data2['2ndFlrSF']
display(train_data2)
```
### 6. Reorient DataFrame
```python
train_data2 = train_data2[['LotArea',
						   '1stFlrSF',
						   '2ndFlrSF',
						   'TotalSF',
						   'SalePrice']]
display(train_data2)
```
### 7. Display Scatter Plots of Data
```python
plt.scatter(train_data2['TotalSF'], train_data2['SalePrice'])
plt.show()
```
### 8. Run **Linear Regression Model**

#### Function for returning prediction (shared):
```python
def linear_model(x, m, b):
	return m * x + b
```

#### A. Running the model for LotArea vs. SalePrice (**SciPy**)

```python
# Using SciPy module
# Returns a tuple with the following output
slope, intercept, r, p, std_err = stats.linregress(train_data2['LotArea'],
												  train_data2['SalePrice'])	

linear_housing_model = linear_model(train_data2['LotArea'],
								    slope,
								    intercept)

# Equation text, formatted for 2 decimal places
equation_text = f'y = {slope:.2f} * x + {intercept:.2f}\t;\tr = {r:.2f}*'

linear_housing_model = list(linear_housing_model)

# Plot the points in the dataset
plt.scatter(train_data2['LotArea'], train_data2['SalePrice'])
# Plot the linear regression line, in red
plt.plot(train_data2['LotArea'], linear_housing_model, color='red')
plt.show()
print(equation_text)
```

#### B. Running the model for TotalSF vs. SalePrice(**SciPy**)

```python {hl_lines=[3,4]}
# Using SciPy module
# Returns a tuple with the following output
slope, intercept, r, p, std_err = stats.linregress(train_data2['TotalSF'],
												  train_data2['SalePrice'])	

linear_housing_model = linear_model(train_data2['TotalSF'],
								    slope,
								    intercept)

# Equation text, formatted for 2 decimal places
equation_text = f'y = {slope:.2f} * x + {intercept:.2f}\t;\tr = {r:.2f}*'

linear_housing_model = list(linear_housing_model)

# Plot the points in the dataset
plt.scatter(train_data2['TotalSF'], train_data2['SalePrice'])
# Plot the linear regression line, in red
plt.plot(train_data2['TotalSF'], linear_housing_model, color='red')
plt.show()
print(equation_text)
```

#### C. Running the model for TotalSF vs. SalePrice (**Statistics**)

**statistics.linear_regression**: model will allow you to force line through origin

```python {hl_lines=[4,5]}
# Using Statistics Module
# Returns a tuple of two variables
# NOTE: Porportional Argument, if True, will force regression line thru origin
slope, intercept = linear_regression(train_data2['TotalSF'],
										   proportional=True)

corr_coeff = round(correlation(train_data2['TotalSF'],
									 train_data2['SalePrice']), 2)

linear_housing_model = linear_model(train_data2['TotalSF'],
								    slope,
								    intercept)
equation_text = f'y = {slope:.2f} * x + {intercept:.2f}\t;\tcorrelation coeff = {corr_coeff}'

linear_housing_model = list(linear_housing_model)

plt.scatter(train_data2['TotalSF'], train_data2['SalePrice'])
plt.plot(train_data2['TotalSF'], linear_housing_model, color='purple')
plt.show()
print(equation_text)
```


# References
Data Set: [[Housing Data Set from Kaggle]]

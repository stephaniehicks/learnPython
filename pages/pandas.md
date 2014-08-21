---
layout: page
title: Pandas
tagline: 
---
{% include JB/setup %}

Pandas is a module in Python for working with data structures.  The two main objects from [Pandas](http://pandas.pydata.org) are the `Series` and `DataFrame`. This object can easily subset, aggregate and reshape the data using the array-computing features of NumPy.  

## Import Pandas

>	from pandas import Series, DataFrame
>	import pandas as pd
>	import numpy as np


## Series
The `Series` is a one-dimensional array-like object with associated data labels called the *index*.  The `values` and `index` of the `Series` can be accessed using attributes of the object.  Similar to strings and tuples, the `index` of a `Series` is **immutable** (same is true for a `DataFrame` later on). 
>	x = Series([5, 10, 15, 20])
>	x.values
>	x.index

The default index for a `Series` is the set of integers starting at 0 through the length of the data (e.g. $N - 1$). To define a new index, use `index` in the `Series` definition. These indexes can be used to select a subset of the `Series`. Other subsetting such as using boolean arrays also work. 

>	x = pd.Series([5, 10, 15, 20], index = ['Holly', 'Bart', 'Josh', 'Karen'])
>	x[['Josh', 'Holly']]
>	x[x > 10 ]

Both the `Series` itself and its index have a `name` attribute. 

>	x.name = 'age'
>	x.index.name = 'firstName'

The index of a `Series` can also re-ordered

>	x.index = ['Josh', 'Holly', 'Bart', 'Karen']

#### Series and dictionaries
This object is very similar to an ordered `dict` because of the mapping between the index and values.  In fact you can use the `in` operator to check if an index exists in the object You can also directly pass a `dict` to a `Series`. 

>	'Bart' in x
>	y = Series[{'Holly': 5, 'Bart': 10, 'Alan': 27, 'Beau': 5}]

**Note**: The resulting `Series` will have the `dict`'s keys in a sorted order. 

#### Series and missing data
When creating a `Series`, you can have missing data (i.e. `NaN` values).  to testing for missing data, use `pd.isnull` and `pd.notnull` 

>	pd.isnull(x)
>	pd.notnull(x)

#### Combining multiple Series

One of the benefits of a `Series` is you can combine two `Series` which are indexed differently.  For example, 

>	x + y

returns a new `Series` with the union of all the indexes and values in `x` and `y`. 


## Creating a DataFrame

The `DataFrame` is an extension of the `Series` because instead of just being one-dimensional, it organizes data into a column structure with row and column labels. This allows the user to have a collection of columns of data with different `type`s.  The `DataFrame` has a both row and column index.  The column names can be found using the attribute `columns`. The `values` and `index` can be....

>	data = {'height' : 5.6, 7.0, 4.9, 6.7, 5.2, 5.5, 6.1, 5.4], 
>	       'age' : [15, 21, 15, 20, 22, 41, 18, 38]}
>	z = DataFrame(data)
>	z.columns  		# column names
>	z.values			# values
>	z.index			# index
>	z.ix				# indexing field

To extract a specific column, you can use `[ ]` (brackets) or attribute notation.  If you specify a sequence of columns, the `DataFrame` will return the columns you ask for.  If you pass a column that isn't in your data set, then it will return `NaN` values. 

>	z.height
>	z['height']
>	z = DataFrame(data, columns = ['height', 'age', 'weight'])

Altering the value of a column can be done too. 

>	z['weight'] = 180		# assigns 180 to all the values in the `weight` column
>	z['footSize'] = 7			# assigning values to a column that doesn't exist creates a new column
>	z.index = ['Holly', 'Bart', 'Josh', 'Karen', 'Tom', 'Doug', 'Sophie'']		# assigns the index values


Both the `DataFrame` itself, its `index` and its `columns` have a `name` attribute. 

>	z.name = 'Team1'
>	z.index.name = 'firstName'
>	z.columns.name


A `DataFrame` can be transposed using `.T`

>	z.T


#### Ways to create a DataFrame [Mostly taken from [Data analysis for Python](http://www.amazon.com/Python-Data-Analysis-Wrangling-IPython/dp/1449319793)]

Approach | Details
--- | --- 
`dict` of `array`s, `list`s, or `tuple`s | Each group of elements becomes a column (all groups must be the same length)
`dict` of `dict`s |  If you have a nested `dict` of `dict`s then when you pass it to a `DataFrame`, the outer `dict` keys will be the columns and the inner keys will be the rows. 
`dict` of `Series` | Each `value` becomes a column
2D `ndarray` | Use the `numpy` `ndarray` with optional row and column labels
Another `DataFrame` | Combine `DataFrame`s using their `index`es
`list` of `dict`s or `Series` | Each item in the `list` becomes a *row* in the `DataFrame`. Union of the `dict` `keys` (or `Series` `index`es) is the column names 
`list` of `list`s or `tuple`s | Similar idea to the `ndarray`


## Index methods 

There are a set of methods that specifically operate on the `index` of a `DataFrame` (i.e. `z.index`). **Note**: These methods do not alter the index, but rather creates a new index that has been modified using one of the following methods. 

--- | --- 
`unique` | Return the unique values in the index
`is_unique` | Returns a `Bool` if index has no duplicates
`insert(n, elem)` | Insert `elem` at position `n`
`delete(n)` | Delete the `value` at position `n`
`drop(elem)` | Drop the `elem` value 
`union` | Return the union of indexes
`intersection` | Return the intersection of indexes
`diff` |
`append` | Append a new index object


## Import data from a tab-delimited file to a DataFrame 

>	data = pd.read_csv('myfile.txt', delimiter='\t', names=headernames).dropna()
>	print "Number of rows: %i" % data.shape[0]
>	data.head()  # print the first 5 rows



---
layout: page
title: Pandas
tagline: 
---
{% include JB/setup %}

Pandas is a module in Python for working with data structures.  The main object from [Pandas](http://pandas.pydata.org) is the `DataFrame` which organizes data into a column structure with row and column labels. This object can easily subset, aggregate and reshape the data using the array-computing features of NumPy.  

# Import Pandas

>	import pandas as pd
>	import numpy as np


# Creating a DataFrame

>	height = [5.6, 7.0, 4.9, 6.7, 5.2, 5.5, 6.1]
>	names = ['Holly', 'Bart', 'Josh', 'Karen', 'Tom', 'Doug', 'Sophie', 'Joe']
>	c1.height
>	over5.5 = c1.height[c1.height >=5.5]

To import data from a tab-delimited file,  

>	data = pd.read_csv('myfile.txt', delimiter='\t', names=headernames).dropna()
>	print "Number of rows: %i" % data.shape[0]
>	data.head()  # print the first 5 rows


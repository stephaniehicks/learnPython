---
layout: page
title: NumPy
tagline: 
---
{% include JB/setup %}

NumPy and SciPy are modules in Python for scientific computing.  [NumPy](http://www.numpy.org) lets you do fast, vectorized operations on arrays and [SciPy](http://www.scipy.org) is a collection of mathematical and scientific modules built on top of NumPy.  

Why use these modules?  Because working with these modules gives you the performance of using low-level code (e.g. C or Fortran) with the benefit of writing the code in an interpreted scripting language (all while keeping the native Python code). For example, the objects created by NumPy (e.g. arrays) are memory efficient and support mathematical functions.  


# Import NumPy

>	from numpy import *


# Creating NumPy arrays

To create a `numpy` array, use the `numpy.array()` method on a python `list` or `tuple` or reading data from files. This will create a `ndarray` object. 

>	x = array([1,2,3,4])
>	y = array([[1,2], [3,4]])
>	type(x), type(y)


#### Properties of NumPy arrays
There are a set of properties about the numpy arrays such the dimensions, the size, etc.  

Property | Description
--- | ----
`y.shape` (or `shape(y)` | Shape or dimension of the array
`y.size` (or `size(y)`) | Number of elements in the array 
`y.dtype` | Data type
`y.astype(float)` | Forces the data type to be a `float` (or `bool`, etc)
`y.nbytes` | Number of bytes
`y.itemsize` | Number of bytes per element
`y.ndim` | number of dimensions 


#### Various other ways to generate NumPy arrays

Function | Description
--- | ---
`arange(start,stop,step)` | Create a range between the start and stop arguments
`linspace(start,stop,length)` | Create a range between start and stop (both ends included)
`logspace(start, stop, length, base)` | Create a range in the log space with a define base)
`mgrid[0:n, 0:m]` | Create a meshgrid 
`random.rand(n, m)` | Generate uniform random numbers in [0,1] of dim n x m
`random.randn(n, m)` | Generate standard normal random numbers of dim n x m
`diag([1,2,3], k=offset)` | Generate a diagonal matrix with the input on the diagonal with an offset
`zeros((3,3))` | Generate a zeros matrix
`ones((3,3,))` | Generate a ones matrix


#### Reshaping, resizing and stacking Numpy arrays

To reshape an array, use `reshape()`:

>	z = arange(0, 10)
>	z.reshape((2,5)) # dim 2 x 5
>	shape(z)

To flatten an array (convert a higher dimensional array into a vector), use `flatten()`: 

>	A = random.rand(4,4)
>	B = A.flatten()
>	shape(B)

Function | Description 
--- | ---
`z.reshape((n,m))` | Reshape z to have dim or shape `n`, `m`
`z.flatten()` | Flatten a higher dimensional array into a vector
`z[:, newaxis]` | Added a new dimension to the z array using `newaxis`
`z.repeat(n)` | Repeat each element in z `n` times. 
`z.repeat(n)` | Repeat each element in z `n` times. 
`tile(z, n)` | Repeat the entire array z `n` times. 
`concatenate((a,b), axis = 0)` | Concatenate two arrays (a, b) along the columns 
`concatenate((a,b), axis = 1)` | Concatenate two arrays (a, b) along the rows 
`hstack((a,b))` | horizontally stack two arrays
`vstack((a,b))` | vertically stack two arrays




#### Reading and writing from CSV files
To read comma-separated values (CSV) data from a file into numpy arrays, use the `numpy.genfromtxt()` function in `numpy`.  

>	data = genfromtxt('myfile.csv')
>	data.shape

To save a `numpy` array in a CSV format, use `numpy.savetxt()` where `fmt` specifies the format to save in

>	dat = random.rand(3,3)
>	savetxt("output.csv", dat, fmt = '%.5f')


#### Reading and writing from NumPy's native file format
To read from the numpy native file format (`.npy`), use the `numpy.save()` and `numpy.load()` functions. 

>	dat = random.rand(3,3)
>	save("output.npy", dat, fmt = '%.5f')
>	load("output.npy"))
>	output.npy





# Operating on NumPy arrays

#### Assigning values
To assign values to a specific element in a `ndarray`, use the assignment operator.  **Note**: You cannot assign a value of the wrong type to a `ndarray` (e.g. strings), but you can define the type data using the `dtype` property (such as `int`,`float`, `complex`, `bool` etc)

>	y[0,0] = 10
>	y[0,0] = "Boston"
>	y = array([[1.1,2.2], [3.1,4.2]], dtype = float)


#### Indexing arrays
To extract elements of the NumPy arrays, use the bracket operator and the slice (i.e. colon) operator.  To slice specific elements in the array, use `dat[lower:upper:step]`. To extract the diagonal (and subdiagonal) elements, use `diag()`. 

>	dat = random.rand(3:3)
>	dat[0, :] # row 1
>	dat[:, 0] # column 1
>	dat[0:3:2, 0] # first and third elements in column 1
>	diag(dat, -1) 


#### Subsetting arrays using a mask
You can subset for elements in an array using a conditional statement. 

>	z = array([i for i in range(11)])
>	my_mask = (2 < z) * (z < 8) # check is the elements of z are larger than 2 and less than 8
>	z[my_mask]

To determine the position index of a mask, use the `where()` function. The `take()` function is similar to the subsetting above, except it works on 

>	keep_indices = where(my_mask)
>	z.take(keep_indices)
>	take(z, keep_indices)

Finally, the `choose()	` function creates an array from picking elements from several arrays

>	which = [1, 0, 1, 0]
>	choices = [[-2,-2,-2,-2], [5,5,5,5]]
>	choose(which, choices)


#### Iterating over array elements
Iterating over array elements is not suggested (very slow compared to vectorized operations), but sometimes they are unavoidable.  To iterate over array elements, use a `for` loop: 

>	z = arange(0, 10)
>	for elem in z:
>	    print elem


#### Linear algebra

Performing matrix and vector operations is very straightforward with NumPy.  Arithmetic operators (+, - , * ) can be used with arrays. 

>	A = array([ [n+m for n in range(5)] for m in range(5)])
>	A + 5
>	A * 10
>	A * A  # element wise multiplication 
>	dot(A, A) # matrix multiplication on arrays



# Creating NumPy matrices 

To convert a numpy `array` to a numpy `matrix`, use the `matrix()` function.  This allows the standard arithmetic operators (+, -, *) to use matrix algebra. 

>	x = matrix(A)
>	y = matrix(arange(0, 5))
>	yT = y.T # makes it a column vector
>	x * x
>	x * yT
>	shape(x * yT)

Other useful matrix computations

Function | Description 
--- | --- 
`inv(x)` | Inverse of the matrix x
`det(x)` | Determinant of matrix x
`sum(x)` (or `x.sum()`) | Sum of the values
`prod(x + 1)` | Product of all values 
`cumsum(x)` | Cumulative sum
`mean(x[:, 0])` | Mean of the first column
`std(x[0,:])` | Standard deviation of first row
`var(x[0, :])` | Variance of first row
`x.min()`, `x.min(axis=0)`, `x.min(axis=`) | global min, min in each column (or row)
`x.max()`, `x.max(axis=0)`, `x.max(axis=`) | global max, max in each column (or row)
`trace(x)` | Trace (Same as `diag(x).sum()`)



# Vectorizing functions

It is important to state again that you should avoid looping through elements in vectors if at all possible.  One way to get around that when writing functions is to use what are called **vectorized functions**.  Say you wrote a function `f` which accepts some input `x` and checks if `x` is bigger or smaller than 0.  

>	def f(x):
>	    if x >=0:
>	    	return True
>	    else:
>	        return False
>	print f(3)

If we give the function an array instead of just one value (e.g. 3), then Python will give an error because there is more than one element in `x`.  The way to get around this is to **vectorize** the function.  

>	f_vec = vectorize(f)
>	f_vec(arange(-5, 6))

Instead of vectorizing the function, you can also make the function itself aware that it will be accepting vectors from the beginning. 

>	def f(x):
>	    return (x >=0)
>	print f(3)

#### Using conditional statements in arrays

To check if `any` or `all` elements in an array meet a certain criteria, use `any()` and `all()`. 

>	if (x > 0).any()
>	if (x > 0).all()




#### Resources

* [Video of Walt Mankowski on NumPy and SciPy](https://www.youtube.com/watch?v=I_XLoTQSuUk)
* [Scientific Lectures (python notebooks) on Github from Robert Johansson](https://github.com/jrjohansson/scientific-python-lectures)
---
layout: page
title: NumPy
tagline: 
---
{% include JB/setup %}

NumPy and SciPy are modules in Python for scientific computing.  [NumPy](http://www.numpy.org) lets you do fast, vectorized operations on arrays.  Why use this module?  

* It gives you the performance of using low-level code (e.g. C or Fortran) with the benefit of writing the code in an interpreted scripting language (all while keeping the native Python code). 
* It gives you a fast, memory-efficient multidimensional array called `ndarray` which allows you perform vectorized operations on (and supports mathematical functions such as linear algebra and random number generation)


# Import NumPy

>	import numpy as np


# Creating NumPy arrays

To create a fast, multidimensional `ndarray` object, use the `np.array()` method on a python `list` or `tuple` or reading data from files. 

>	x = np.array([1,2,3,4])
>	y = np.array([[1,2], [3,4]])
>	type(x), type(y)


#### Properties of NumPy arrays
There are a set of properties about the `ndarray` object such the dimensions, the size, etc.  

Property | Description
--- | ----
`y.shape` (or `shape(y)` | Shape or dimension of the array
`y.size` (or `size(y)`) | Number of elements in the array 
`y.dtype` | Data type of array
`y.astype(float)` | Forces the data type to be a `float` (or `bool`, etc)
`y.nbytes` | Number of bytes
`y.itemsize` | Number of bytes per element
`y.ndim` | number of dimensions 


#### Other various ways to generate NumPy arrays

Function | Description
--- | ---
`np.arange(start,stop,step)` | Create a range between the start and stop arguments
`np.linspace(start,stop,length)` | Create a range between start and stop (both ends included)
`np.logspace(start, stop, length, base)` | Create a range in the log space with a define base)
`np.mgrid[0:n, 0:m]` | Create a meshgrid 
`np.diag([1,2,3], k=offset)` | Generate a diagonal matrix with the input on the diagonal with an offset
`np.zeros((3,3))` | Generate a zeros matrix with given length or shape
`np.ones((3,3,))` | Generate a ones matrix with given length or shape
`np.empty((m,n))` | Generate an array without initializing any values (pass a tuple for the shape)
`np.eye(n)` | Generate an n x n identity matrix


In addition, the `numpy.random` module can be used to create arrays using a random number generation 

>	from numpy import random

Function | Description
--- | ---
`np.random.randint(a, b, N)` | Generate N random integers between a and b
`np.random.rand(n, m)` | Generate uniform random numbers in [0,1] of dim n x m
`np.random.randn(n, m)` | Generate standard normal random numbers of dim n x m
`np.random.binomial(n, p, size = N)` | Generate N binomial random variables with parameters n, p
`np.random.normal(size=N)` | Generate N standard normal random variables
`np.random.shuffle()` | Randomly permute a sequence in place
`np.random.beta()` | Generate N standard normal random variables
`np.random.chisquare()` | Generate N chisquare random variables
`np.random.gamma()` | Generate N gamma random variables
`np.random.uniform()` | Generate N uniform random variables

#### Reshaping, resizing and stacking NumPy arrays

To reshape an array, use `reshape()`:

>	z = np.arange(0, 10)
>	z = z.reshape((2,5)) # dim 2 x 5
>	np.shape(z)


To flatten an array (convert a higher dimensional array into a vector), use `flatten()`: 

>	A = np.random.rand(4,4)
>	B = A.flatten()
>	np.shape(B)



Function | Description 
--- | ---
`z.reshape((n,m))` | Reshape z to have dim or shape `n`, `m`
`z.flatten()` | Flatten a higher dimensional array into a vector
`z[:, newaxis]` | Added a new dimension to the z array using `newaxis`
`z.repeat(n)` | Repeat each element in z `n` times. 
`z.repeat(n)` | Repeat each element in z `n` times. 
`z.sort()` | Sorts the elements in place
`np.tile(z, n)` | Repeat the entire array z `n` times. 
`np.concatenate((a,b), axis = 0)` | Concatenate two arrays (a, b) along the columns 
`np.concatenate((a,b), axis = 1)` | Concatenate two arrays (a, b) along the rows 
`np.hstack((a,b))` | horizontally stack two arrays
`np.vstack((a,b))` | vertically stack two arrays




#### Reading and writing from CSV files
To read comma-separated values (CSV) data from a file into numpy arrays, use the `np.genfromtxt()` function in `np`.  

>	data = np.genfromtxt('myfile.csv')
>	np.shape(data)

To save a `ndarray` object in a CSV format, use `np.savetxt()` where `fmt` specifies the format to save in

>	dat = random.rand(3,3)
>	np.savetxt("output.csv", dat, fmt = '%.5f')


#### Reading and writing from NumPy's native file format
To read from the numpy native file format (`.npy`), use the `np.save()` and `np.load()` functions. 

>	dat = random.rand(3,3)
>	np.save("output.npy", dat, fmt = '%.5f')
>	np.load("output.npy"))
>	output.npy





# Operating on NumPy arrays

#### Assigning values
To assign values to a specific element in a `ndarray`, use the assignment operator.  **Note**: You cannot assign a value of the wrong type to a `ndarray` (e.g. strings), but you can define the type data using the `dtype` property (such as `int`,`float`, `complex`, `bool` etc)

>	y[0,0] = 10
>	y[0,0] = "Boston"
>	y = array([[1.1,2.2], [3.1,4.2]], dtype = float)


#### Indexing and slicing arrays
To extract elements of the NumPy arrays, use the bracket operator and the slice (i.e. colon) operator.  To slice specific elements in the array, use `dat[lower:upper:step]`. To extract the diagonal (and subdiagonal) elements, use `diag()`. 

>	dat = random.rand(3:3)
>	dat[0, :] 				# row 1
>	dat[:, 0] 				# column 1
>	dat[0:3:2, 0] 			# first and third elements in column 1
>	diag(dat, -1) 

>	x = np.arange(32).reshape((8, 4)) 	# returns an 8 x 4 array
>	x[0] 							# returns the first row
>	x[4:, :3] 						# returns rows 5 and down (excluding the last column)
>	x[[1, 5, 7, 2], [0, 3, 1, 2]] 			# selects elements (1, 0), (5, 3), (7, 1), (2, 2)


#### Element-wise transformations on arrays
There are many vectorized wrappers that take in one scalar and produce one ore more scalars (e.g. `np.exp()`, `np.sqrt()`) 

Function | Description 
--- | --- 
`np.abs(x)` | absolute value of each element
`np.sqrt(x)` | square root of each element
`np.square(x)` | square of each element
`np.exp(x)` | exponential of each element
`np.maximum(x, y)` | element-wise maximum from two arrays x and y
`np.minimum(x,y)` | element-wise minimum
`np.sign(x)` | compute the sign of each element: 1 (pos), 0 (zero), -1 (neg)
`np.subtract(x, y)` | subtract elements in y from elements in x
`np.power(x, y)` | raise elements in first array x to powers in second array y
`np.meshgrid(x, y)` | takes in two 1D arrays and produces two 2D matrices of all pairs (x, y)
`np.where(cond, x, y)` | ifelse statement


#### Subsetting arrays using a mask
You can subset for elements in an array using a conditional statement. 

>	z = np.array([i for i in range(11)])
>	my_mask = (2 < z) * (z < 8) # check is the elements of z are larger than 2 and less than 8
>	z[my_mask]

You can also use the `np.where()` function. 

>	np.random.rand(11)
>	np.where(my_mask, z, y) 		# Picks elements in x when `cond` is true, else elements in y

To determine the position index of a mask, use the `np.where()` function. The `take()` function is similar to the subsetting above

>	keep_indices = np.where(my_mask)
>	z.take(keep_indices)
>	take(z, keep_indices)

Finally, the `choose()	` function creates an array from picking elements from several arrays

>	which = [1, 0, 1, 0]
>	choices = [[-2,-2,-2,-2], [5,5,5,5]]
>	choose(which, choices)


#### Unique and set logic on arrays

Other useful functions in `numpy` include `np.unique()` and other set logic functions.  These are set operations for one-dimensional `ndarrays`.  

Function | Description
--- | --- 
`np.unique(x)` | Returns the *sorted*, unique values in  x
`np.intersect1d(x, y)` | Returns the *sorted*, common elements in x and y
`np.union1d(x, y)` | Returns the *sorted*, union of elements
`np.in1d(x, y)` | Returns a `bool` array indicating if each element of x is in y
`np.setdiff1d(x, y)` | Set difference of elements in x not in y
`np.setor1d(x, y)` | Set symmetric difference of elements in either array (but not both)



#### Iterating over array elements
Iterating over array elements is not suggested (very slow compared to vectorized operations), but sometimes they are unavoidable.  To iterate over array elements, use a `for` loop: 

>	z = np.arange(0, 10)
>	for elem in z:
>	    print elem


#### Linear algebra

Performing matrix and vector operations is very straightforward with NumPy.  Arithmetic operators (`+`, `-` , `*` ) can be used with arrays. 

>	A = np.array([ [n+m for n in range(5)] for m in range(5)])
>	A + 5
>	A * 10
>	A * A  # element wise multiplication 
>	np.dot(A.T, A) # or inner matrix product multiplication on arrays



# Creating NumPy matrices 

To convert a `ndarray` to a numpy `matrix`, use the `np.matrix()` function.  This allows the standard arithmetic operators (`+`, `-`, `*`) to use matrix algebra. 

>	x = np.matrix(A)
>	y = np.matrix(np.arange(0, 5))
>	yT = y.T # transposes array and makes it a column vector
>	x * x
>	x * yT
>	np.shape(x * yT)

Other useful matrix computations

Function | Description 
--- | --- 
`np.sum(x, axis = 0)` (or `x.sum()`) | Sum of the values (along a given dimension)
`np.prod(x + 1)` | Product of all values 
`np.cumsum(x)` | Cumulative sum
`np.mean(x[:, axis = 0])` | Mean of the first column
`np.std(x[0,:])` | Standard deviation of first row
`np.var(x[0, :])` | Variance of first row
`x.min()`, `x.min(axis=0)`, `x.min(axis=`1) | global min, min in each column (or row)
`x.max()`, `x.max(axis=0)`, `x.max(axis=`1) | global max, max in each column (or row)
`np.trace(x)` | Trace (Same as `diag(x).sum()`)
`np.transpose()` | Similar to using `.T` to transpose arrays, but accepts a tuple of axis numbers to permute the axes

In addition, the module `numpy.linalg` contains a set of functions for matrix decomposition and inverses

>	from numpy.linalg import inv, qr, det

Function | Description 
--- | --- 
`inv` | Returns the inverse of a square matrix
`det` | Returns the matrix determinant 
`diag` | Diagonal of square matrix
`dvd` | Singular value decomposition 
`qr` | QR decomposition 
`eig` | Returns the eigenvalues and eigenvectors of a square matrix
`solve` | Solves for $x$ in $Ax = b$ where $A$ is square
`lstsq` | Least squares solution 


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
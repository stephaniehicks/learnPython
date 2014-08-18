---
layout: page
title: SciPy
tagline: 
---
{% include JB/setup %}

Now that you know a little bit about [NumPy](numpy.html) and SciPy is a collection of mathematical and scientific modules built on top of NumPy.  For example, SciPy can handle multidimensional arrays, integration, linear algebra, statistics and optimization.  


# Import SciPy
To import the SciPy module, use 

>	from numpy import *
>	from scipy import *

SciPy includes most of NumPy, so importing SciPy should be generally OK. The main SciPy module is made up of many [submodules containing specialized topics](http://docs.scipy.org/doc/scipy/reference/). 

Favorite SciPy submodules | What does it contain? 
--- | --- 
`scipy.stats` | [statistics](http://docs.scipy.org/doc/scipy/reference/tutorial/stats.html): random variables, probability density functions, cumulative distribution functions, survival functions
`scipy.integrate` | [integration](http://docs.scipy.org/doc/scipy/reference/tutorial/integrate.html): single, double, triple integration, trapezoidal rule, Simpson's rule, differential equation solvers
`scipy.signal` | [signal processing tools](http://docs.scipy.org/doc/scipy/reference/signal.html): signal processing tools such as wavelets, spectral densities, filters, B-splines
`scipy.optimize` | [optimization](http://docs.scipy.org/doc/scipy/reference/optimize.html): find roots, curve fitting, least squares, etc 
`scipy.special` | [special functions](http://docs.scipy.org/doc/scipy/reference/tutorial/special.html): very specialized functions in mathematical physics e.g. bessel, gamma
`scipy.linalg` | [linear algebra](http://docs.scipy.org/doc/scipy/reference/linalg.html): inverse of a matrix, determinant, Kronecker product, eigenvalue decomposition, SVD, functions for matrices (beyond those in `numpy.linalg`)

If you want to import a SciPy submodule (e.g. the statistics submodule `scipy.stats`), use 

>	from scipy import stats
>	

# scipy.stats 
Let's dive a bit deeper in `scipy.stats`. The real utility of this submodule is to access probability distributions functions (pdfs) and standard statistical tests (e.g. $t$-test).  

#### Probability distribution functions
There is a large collection of [continuous and discrete pdfs](http://docs.scipy.org/doc/scipy/reference/stats.html) in the `scipy.stats` submodule.  The syntax to simulate random variables from a specific pdf is the name of the distribution  followed by `.rvs`. To generate $n$=10 $N(0,1)$ random variables, 

>	from scipy.stats import norm
>	norm.rvs(loc = 0, scale = 1, size = 10)


#### Statistical tests for significance


#### Resources

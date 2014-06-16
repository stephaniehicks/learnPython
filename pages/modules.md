---
layout: page
title: Python modules
tagline: Importing and using modules
---
{% include JB/setup %}

There are many modules in Python that you can import to access familiar functions.  

# Importing modules
There are two ways to import modules.  The first is to use the word `import` and the name of the module: 

> 	import math

This will import a module named math which containing functions such as log(), sin(), cos(), etc. To access this functions, you have to specify the name of the module and the name of the function separated by a dot (or period): e.g. `math.sin(x)`.  To access the value of $\pi$, use `math.pi`

The second way to import a module is with the words `from` and `import`. This allows you to use the name of the functions directly without having to type the name of the module and a period in front of the name of the function.   To import a specific function from the math module, use the first line. To import everything from a module, use the second line. 

> 	from math import pi
>	from math import *

Now you can use `pi` directly. 

# Modules in Python

### math module


### string module
* `string.punctuation()`
* `string.strip()`
* `string.replace()`
* `string.translate()`

### random module
The random module generates pseudorandom numbers. 

* `random.random()` = returns a random float between 0.0 and 1.0
* `random.randint(low, high)` = takes in a low and high integers and returns a random integer (including both)
* `random.choice(t)` = returns a random elements from the sequence t
* also generates random values from continuous probability distributions


### anydbm, pickle and shelve modules
The `anydbm` module is interfaces and updates database files. The two methods functions to open and close the databases `anydbm.open()` and `anydbmclose()`.  To work with this module, the database must have keys and values as strings!  

If your keys or values are not strings, you can use the `pickle` module to translate any object into a string which can be then stored in a database using the `pickle.dumps()` function.  When you want to access the database, the module will translate the string back into the original objects using the `pickle.loads()` function.  

This method of "pickling" the objects from the `pickle` module combined with the `anydbm` module has been implemented in the `shelve` module.  To open and close files using this module use `shelve.open()` and `shelve.close()` which uses the `pickle` module to open and store the objects. 

### urllib module
This module is useful to manipulate URLs and downloading information from the web.  

* `urllib.urlopen()` = opens a html file from the web
 
# Writing modules
Any file that contains Python code and ends in `.py` can be imported as a module.  If your file name is `cool.py`, you can import the program directly

>	import cool
>	print cool

which will print that the object 'cool' is a module from 'cool.py'.  The functions inside the module are accessed in same syntax as before: the name of the module, a dot (or period) and the name of the function.  

**Note**: If you import a module that has already been imported, Python will not re-read the file (even if it has changed!).  To reload the module, use the built-in Python function `reload`.  

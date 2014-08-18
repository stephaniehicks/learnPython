---
layout: page
title: Python modules
tagline: Importing and using modules
---
{% include JB/setup %}

A module in Python is a file (ending in `.py`) that contains a set of definitions (variables and functions) that you can use when they are imported. Modules are considered as objects, just as everything else is in Python. Many methods can operate on modules.  As [mentioned previously](basics.html), the `dir()` function can list all the objects imported and available to work with in your active Python session. The name of the module that contains all the built-in Python functions is called `__builtins__` and can be accessed: 

>	dir(__builtins__)

Another example of a method that can operate on modules is the `str()` function, returning a string representation of the module including the pathname on your local disk.  Outside of the `__builtins__` module, there are many modules in Python that you can import to access familiar functions. 

# Importing modules
There are two ways to import modules.  The first is to use the word `import` followed by the name of the module: 

> 	import math

This will import a module named math which containing functions such as log(), sin(), cos(), etc. To access this functions, you have to specify the name of the module and the name of the function separated by a dot (or period): e.g. `math.sin(x)`.  To access the value of $\pi$, use `math.pi`

The second way to import a module is with the words `from` and `import`. This allows you to use the name of the functions directly without having to type the name of the module and a period in front of the name of the function.   To import a specific function from the math module, use the first line. To import everything from a module, use the second line. 

> 	from math import pi
>	from math import *

Now you can use `pi` directly.  To see all the variables and functions available in the math module, use `dir()`. 

>	dir(math)

Going back to the `__builtins__` modules, you can think of Python automatically importing this module on the startup of your Python session: 

>	from __builtins__ import *


#### Reloading modules

When you import a module in python, all the variables and functions are stored in a namespace.  The next time you use `import`, the existing module will be loaded.  If the module has been changed, to force a reload, use `reload()`

>	import mymodule
>	reload(mymodule)

# Module attributes
Every Python class has a built-in class attribute `__module__` which is the name of the module in which the class is defined. For example, the following will tell us the function `sin()` came from the math module.  

>	sin.__module__



# Writing modules
Any file that contains Python code and ends in `.py` can be imported as a module.  If your file name is `cool.py`, you can import the program directly

>	import cool
>	print cool

which will print that the object 'cool' is a module from 'cool.py'.  The functions inside the module are accessed in same syntax as before: the name of the module, a dot (or period) and the name of the function.  

**Note**: If you import a module that has already been imported, Python will not re-read the file (even if it has changed!).  To reload the module, use the built-in Python function `reload`.  


# Other useful modules 

#### copy
* `copy.copy()` = function to duplicate any object (not create an alias)


#### types
This module can be used to compare the types of any object. 

>	import types
>	type(os) == types.ModuleType



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
* math
* 


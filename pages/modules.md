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


# Module attributes
Every Python class has a built-in class attribute `__module__` which is the name of the module in which the class is defined. For example, the following will tell us the function `sin()` came from the math module.  

>	sin.__module__



# Writing modules
Any file that contains Python code and ends in `.py` can be imported as a module.  If your file name is `cool.py`, you can import the program directly

>	import cool
>	print cool

which will print that the object 'cool' is a module from 'cool.py'.  The functions inside the module are accessed in same syntax as before: the name of the module, a dot (or period) and the name of the function.  

**Note**: If you import a module that has already been imported, Python will not re-read the file (even if it has changed!).  To reload the module, use the built-in Python function `reload`.  





# Modules in Python

### math module


### datetime module
The datetime module can be used to print out the date and time. the function `now()` will print out the current day and time. Some attributes inclue `year`, `month`, `day`, `hour`, `minute`, `second`. 

>	import datetime 
>	now = datetime.now()
>	print '%s/%s/%s' % (now.month, now.day, now.year)

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


 ### glob module and listing files in directories
The glob module is useful when listing directories, but you do not have the name of the files (just a wildcard e.g. *.txt).  The `glob()` function will match all the *.txt files in a directory and return the them as a list

>	import glob
>	glob.glob('*.txt')




### urllib module
This module is useful to getting information about and retrieving data from the web. The function `urlopen()` open a URL (similar to opening a file).  The file-like object has some of the methods as a file object.  For example, to read the entire HTML of the webpage into a single string, use the method `read()`. `readlines()` can read in the text line by line. 

>	import urllib
>	x = urllib.urlopen("http://diveintopython.org")
>	htmlSource = x.read()
>	x.close()
>	print htmlSource
 
Once you have the HTML source code, you have to parse it and clean it up.  
 
### sgmllib module 
The sgmllib module is a simple SGML (Standard Generalized Mark-up Language) parser.  The goal of the module is to process HTML code.  The main function is `SGMLParser` which parses HTML code into 8 kinds of data: 

Name | Definition | Example | SGMLParser function 
--- | --- | --- 
*start tag* | an HTML tag that starts a block | <html>, <head>, <body> | `start_tagname`, `do_tagname`
*end tag* | an HTML tag that ends a block | </html>, </head>, </body> | `end_tagname`
*character reference* | an escaped character referenced by its decimal | &#160; | `handle_charref`
*entity reference* | an HTML entity | \& copy; | `handle_entityref`
*comment* | an HTML comment | comments inclosed in <\|-- ... --> | `handle_comment`
*processing instruction* | an HTML processing instruction | instruction enclosed in <? ... > | `handle_pi`
*declaration* | an HTML declaration | DOCTYPE enclosed in <! ... > | `handle_dec1`
*text data* | a block of text | anything that does not fall into the other 7 categories | `handle_data`



### copy module
* `copy.copy()` = function to duplicate any object (not create an alias)


### types module
This module can be used to compare the types of any object. 

>	import types
>	type(os) == types.ModuleType



### re module
This module is used to manipulate regular expressions.  The function `sub()` searches a string (s) and replaces all the words that match the regular expression. 

>	import re
>	re.sub(regex, replacementword, stringtosearch)
>	re.search()
>	re.compile()

Useful regular expressions in Python

Expression | Interpretation 
--- | --- 
^ | matches the beginning of a string
$ | matches the end of a string
\b | matches a word boundary
\d | matches any numeric digit
\D | matches any non-numeric digit
x? | matches an optional x character
x* | matches x zero or more times
x+ | matches x one or more times
x{n, m} | matches x at least n times, but not more than m times
(a \| b \| c) | matches either a, b or c


 



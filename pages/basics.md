---
layout: page
title: Overview
tagline: Variables, Functions, Conditionals, Iteration
---
{% include JB/setup %}

Everything in Python is an object.  Think of an object as a data structure that contains both data as well as functions. These objects can be variables, functions, and modules which are all objects. We can operate on this objects with what are called **operators** (e.g. addition, subtraction, concatenation or other operations), define/apply functions, test/apply for *conditionals* statements, (e.g. `if`, `else` statements) or iterate over the objects. 

Not all objects are required to have **attributes** and **methods** to operate on the objects in Python, but **everything is an object** (i.e. all objects can be assigned to a variable or passed as an argument to a function).  A user can work with built-in defined classes of objects or can create new classes of objects.  Using these objects, a user can perform operations on the objects by modifying / interacting with them. 


# Variables and Operators

#### Variables
Variable names are case sensitive, can contain numbers and letters, can contain underscores, cannot begin with a number, [cannot contain illegal characters and cannot be one of the 31 keywords in Python](http://en.wikibooks.org/wiki/Think_Python/Variables,_expressions_and_statements#Variable_names_and_keywords): 

>	and, as, assert, break, class, continue, def, del, elif, else, except, 
>	exec, finally, for, from, global, if, import, in, is, lambda, not, or, 
>	pass, print, raise, return, try, while, with, yield


#### Operators
* Numeric operators are +, -, *, /, ** (exponent), % (modulus if applied to integers)
* String and list operators: + and * . 
* Assignment operator: =
* The augmented assignment operator `+=` (or `-=`) can be used like n += x which is equal to n = n + x 
* Boolean relational operators: == (equal), != (not equal), >, <, >= (greater than or equal to), <= (less than or equal to)
	* Boolean expressions will produce `True` or `False`
* Logical operators: `and`, `or`, and `not`. e.g. x > 1 `and` x <=5
	* Any nonzero number is interpreted as `True` 
	* Values are evaluated left to right. e.g. 'yes' and 'no' will return 'no' because 'yes' is evaluated as True AND 'no' is evaluated as True.
	* 0, ' ', [ ], ( ), { }, `None` are evaluated as False. 
	* Order of operations for logic operators: `not`, `and`, `or`. Use parentheses `( )`  to evaluate in order of preference.

#### Format operators
If % is applied to strings, this operator is the format operator.  It tell Python how to format a list of values in a string.  For example, 

* `%d` says to format the value as an integer
* `%g` says to format the value as an float
* `%s` says to format the value as an string


>	'In %d days I have eaten %g %s.'  % (2, 3.5, 'lobsters')

The above line will print 'In 3 years I have spotted 0.1 camels.' Note, the list of strings before the % symbol must be equal to the number defined formats (e.g. number of of %s). 


# Functions
Python contains a small list of very useful built-in functions. All other functions need defined by the user or need to be imported from [modules](modules.html) which will be discussed in a little bit. For a more detailed list on the built-in functions in Python, see [Built-in Python Functions](https://docs.python.org/2/library/functions.html)

## Really useful built-in functions: 

First, we'll discuss `type()`, `print()`, `dir()` and `str()`

#### type()

The first function we'll discuss, `type()`, reports the type of any object, which is very useful when handling multiple data types (**remember**, everything in Python is an object). Here are some the mains types you will encounter: 

	1. integer (`int`) 
	2. floating-point (`float`)
	3. string (`str`)
	4. list (`list`)
	5. dictionary (`dict`)
	6. tuple (`tuple`)
	7. function (`function`)
	8. module (`module`)
	9. boolean (`bool`): e.g. True, False
	10. enumerate (`enumerate`)

If we asked for the type of a string "Go Red Sox!"

>	type("Go Red Sox!")

This would return the `str` type. 

#### print()
The function `print` will accept an argument and print the argument to the screen. Print can be used in two ways: 

>	print("Go Red Sox!")
>	print "Wally the Green Monster"

**Note**: When writing a python script, you must use `print` to call the argument you want returned or the argument will be evaluated, but not printed.

#### dir()
The next function we'll discuss is called `dir()` which takes in an object and returns all the methods of that object. If there is no argument provided, `dir()` returns a list of all the objects currently imported and available to work with.  

>	dir()

Here is an example that returns all the **methods** (you can think of them as functions of objects) that operate on [string](strings.html) objects: 

>	dir("Three strikes and you're out!") 

Besides strings, the function `dir()` also can be applied to any other type of object. For example, [modules](modules.html) are another type of object in Python which can be imported into Python to access functions in that module. Applying the `dir()` function to a module called `nameofmodule`, will return a list of methods (or functions) available in that particular module. 

>	dir(nameofmodule)

We'll discuss [modules](modules.html) in a little bit.  I will note, above when you listed all the objects currently available to work with, one of the items was `__builtins__`, which is a special module that that is automatically imported on the startup.  To find a list of all the built in functions in Python, you can use the module name `__builtins__`. 

>	dir()
>	type(__builtins__)
>	dir(__builtins__)

#### str()
Another powerful built-in function is called `str()` which takes in an input and coerces the input to a string. Every datatype (or object) can be coerced into a string, even modules! 



## Other basic built-in Python functions

Function name | Description | Example use
--- | --- | ---- 
`callable()` | | 
`enumerate()` | accepts a string and returns an `enumerate` object type which is tuple containing a count (from start which defaults to 0) and the values obtained from iterating over string | `enumerate('myseq')`
`int()` | converts floats and strings to integers (but chops off the fraction part and doesn't round) | `int(3.75)` returns 3
`isinstance()` | verifies the type of of the argument | `isinstance(5, int)` returns `True`
`range(n)` | accepts an integer and returns a list of integers from 0 to n-1 | `range(5)`
`repr()` | accepts any input and returns the string representation of the object (helpful for debugging!) | `repr(range(5))`
`getattr()` | accepts any object as input and returns any attribute of that object; technically works on any object, except tuples have no methods | 
`bin()` | accepts an integer and returns the binary representation | `bin(8)`




#### Defining new functions
New functions can be defined using one of the 31 keywords in Python `def`.  

>	def new_world(): 
>	    print 'Hello world!'

The first line of the function (the header) must start with `def`, the name of the function (which can contain underscores), parentheses (with any arguments inside of it) and a colon.  The arguments can be specified in any order. 

The rest of the function (the body) always has an indentation of four spaces.  If you define a function in the interactive mode, the interpreter will print ellipses (...) to let you know the function isn't complete. To complete the function, enter an empty line (not necessary in a script).  

To return a value from a function, use `return`. The function will immediately terminate and not run any code written past this point.  

>	def squared(x):
>	    return x ** 2

#### The docstring
When defining new functions, you can add a `docstring` (aka documentation of function) at the beginning of the function that documents what the function does. The docstring is a triple quoted (multi-line) string. 

>	def love_chocolate(N):
>	    """ A function to explain how much I love 
>	    chocolate """
>	    print 'I' + 'love'*N + 'chocolate'

To print the `docstring` from `love_chocolate()` function, use `__doc__` which is one of the functions **attributes**.  

>	love_chocolate.__doc__
>	squared.__doc__ == None

Because everything in Python is an object, each object can have a set of built-in attributes and a set of built-in methods. All functions have a built-in attribute `__doc__` which returns the `docstring`.   

Variables can be defined over multiple lines with a backslash ("\\") as the line-continuation marker. 

The statement `raise` can be used in a function to raise an error message whenever the function fails to return a value.  This statement will print a traceback and an error message.  

Variables written inside of a function are considered **local** variables and will disappear when the function ends. Variables written outside of a function are considered **global** variables and will remain after the function ends. To change the value of a global variable inside of a function, you must **declare** the global variable before you use it using the syntax `global` nameofvariable.  The exception is if the global variable is mutable (e.g. lists, dictionaries), you can modify individual elements it without declaring it.  

Optional arguments can be provided to the functions where each optional argument has a specified default value. If another value is provided to the optional argument, it is over-written.  

>	def squaredShifted(x, shift = 10):
>	    return shift + (x ** 2)
>	squaredShifted(5, 20)

#### Recursive functions
Functions can call itself to allow for a recursive pattern. 

>	def fact(n): 
>	    if n ==0: 
>	        return 1
>	    else: 
>	        recurse = fact(n-1)
>	        result = recurse * n
>	        return result

Here the 'fact' function calculates the factorial of a given number in a recursive fashion by calling the 'fact' function within itself and returns the result. 

#### Lambda functions
Lambda functions are one-line functions. We defined the `squared()` function above using the following syntax.  

>	def squared(x):
>	    return x ** 2
>	squared(3)

To define this function using the `lambda` function, you do not need to include the `return` argument.  

>	f = lambda x: x**2
>	f(3)


# Conditional statements
Conditional statements allow us to check if a condition is true and then execute some portion of the function accordingly. 

#### If else statements
To define a statement with the `if` and `else` statement, we use a similar structure to defining functions by including a colon at the end of the header and four spaces indented for the body.  

>	if x == 0: 
>	    print 'x is equal to 0'
>	else: 
>	    print 'x is not equal to 0'

The body must contain at least one statement. The `pass` statement can be used in the body if no other statements are in the body

>	if x == 0: 
>	    pass  # ignore zeros

If there are more than two possibilities for the condition you are testing, use `if`, `elif` (short for `else if`) and `else`. You can also nest conditionals, but they must be indented appropriately. 

>	if x > 0: 
>	    if x < 10: 
>	        print 'x is bigger than 0 and less than 10'. 

A more succinct way of doing this is to use logical operators: 

>	if x > 0 and x < 10: 
>	    print 'x is bigger than 0 and less than 10'. 
	 

# Iteration 
Iterative loops can be written with the `for`, `while` and `break` statements. 

#### For loops
Defining a `for` loop is similar to defining a new function. The header ends with a colon and the body is indented with four spaces. The function `range(n)` takes in an integer n and creates a set of values from 0 to n - 1. 

> 	for i in range(4):
>	    print 'Hello world!'

`for` loops are not just for counters, but they can iterate through many types of objects.  For example, a `for` loop can iterate through a [dictionary](dictionaries.html).  

#### while loops
Defining a `while` loop is again similar to defining a `for` loop or new function. The header ends with a colon and the body is indented with four spaces

>	def countdown(n):
>	    while n > 0:
>	        print n
>	        n = n-1
>	     print 'Blastoff!'

To jump out of a loop, use `break`


## Other useful information about Python
* Comments in Python are with the pound symbol #
* There are three types of errors: 
	1. **syntax** errors = errors related to the structure of a program preventing the interpreter from executing a program. 
	2. **runtime** errors = error does not appear until after the program has started running
	3. **semantic** errors = the program will execute successfully, but it will not do the intended thing. For example, if you type an integer with a leading zero, Python interprets it as binary.  Another example of a semantic error is if you write the integer 1 million with commas between the zeros, Python interprets this as a comma-separated sequence of integers. 




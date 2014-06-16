---
layout: page
title: Overview
tagline: Variables, Functions, Conditionals, Iteration
---
{% include JB/setup %}


There are two modes you can write Python code in: **interactive mode** or **script mode**.  If you open up a UNIX command window and have a command-line interface, you can simply type `python` in the shell: 

>	python

and the **interactive mode** will open up.  If you store code in a file ending in `.py`, and execute the file in the **script mode** using 

>	python myscript.py


# Variables and Operators

#### Variables
Variable names are case sensitive, can contain numbers and letters, can contain underscores, cannot begin with a number, [cannot contain illegal characters and cannot be one of the 31 keywords in Python](http://en.wikibooks.org/wiki/Think_Python/Variables,_expressions_and_statements#Variable_names_and_keywords)

#### Operators
* Numeric operators are +, -, *, /, ** (exponent), $\%$ (modulus if applied to integers)
* String and list operators: + and * . 
* The augmented assignment operator `+=` can be used like n += x which is equal to n = n + x 
* Boolean relational operators: == (equal), != (not equal), >, <, >= (greater than or equal to), <= (less than or equal to)
	* Boolean expressions will produce `True` or `False`
* Logical operators: `and`, `or`, and `not`. For example, x > 1 `and` x <=5
	* Any nonzero number is interpreted as `True` 


#### Format operators
If $\%$ is applied to strings, this operator is the format operator.  It tell Python how to format a list of values in a string.  For example, 

* '$\%$d' says to format the value as an integer
* '$\%$g' says to format the value as an float
* '$\%$s' says to format the value as an string

If you run: 'In $\%$d years I have spotted $\%$g $\%$s.' $\%$ (3, 0.1, 'camels')

it will print 'In 3 years I have spotted 0.1 camels.'



# Functions
One of the basic built-in Python functions is `type()` which is a function that reports the type of variable.  A list of the types are: 

	1. integer (`int`) 
	2. floating-point (`float`)
	3. string (`str`)
	4. list (`list`)
	5. dictionary (`dict`)
	6. tuple (`tuple`)
	7. function (`function`)
	8. boolean (`bool`): e.g. True, False
	9. enumerate (`enumerate`) 


#### Basic built-in Python functions
* `print()` = print the argument to the screen; must use `print()` in script mode or the argument will be evaluated, but not printed. 
* `int()` = converts floats and strings to integers (but chops off the fraction part and doesn't round)
* `str() = converts values to strings
* `isinstance()` = verifies the type of of the argument (e.g. isinstance(5, int) would return True)
* `range()` = returns a list of indices from 0 to n-1.
* `enumerate('myseq')` = returns an `enumerate`object which is accepts a sequence and returns a tuple containing a count (from start which defaults to 0) and the values obtained from iterating over sequence
* `repr()` = takes in an argument and returns the string representation of the object (helpful for debugging!)

For a more detailed list on the built-in functions in Python, see [Built-in Python Functions](https://docs.python.org/2/library/functions.html)

#### Defining new functions
New functions can be defined using one of the 31 keywords in Python `def`.  

>	def new_world(): 
>	    print 'Hello world!'

The first line of the function (the header) must start with `def`, the name of the function (which can contain underscores), parentheses (with any arguments inside of it) and a colon.  The rest of the function (the body) always has an indentation of four spaces.  If you define a function in the interactive mode, the interpreter will print ellipses (...) to let you know the function isn't complete. To complete the function, enter an empty line (not necessary in a script).  

When defining new functions, you can add a `docstring` at the beginning of the function that contains the documentation for the function. The docstring is a triple quoted string which allows the line to span more than one line. 

>	def love_chocolate(N):
>	    """ A function to explain how much I love 
>	    chocolate """
>	    print 'I' + 'love'*N + 'chocolate'

To return a value from a function, use `return`. The function will immediately terminate and not run any code written past this point.  

>	def squared(x):
>	    return x ** 2

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


# Conditional statements
Conditional statements allow us to check if a condition is true and then change the direction of the function accordingly. 

#### If else statements
To define a statement with the `if` and `else` statement, we use a similar structure to defining functions by including a colon at the end of the header and four spaces indented for the body.  

>	if x == 0: 
>	    print 'x is equal to 0'
>	else: 
>	    print 'x is not equal to 0'

The body must contain at least one statement. The `pass` statement can be used in the body if no other statements are in the body

>	if x == 0: 
>	    pass		# ignore zeros

If there are more than two possibilities for the condition you are testing, use `if`, `elif` and `else`. You can also nest conditionals, but they must be indented appropriately. 

>	if x > 0: 
>	    if x < 10: 
>	        print 'x is bigger than 0 and less than 10'. 

A more succinct way of doing this is to use logical operators: 

>	if x > 0 and x < 10: 
>	    print 'x is bigger than 0 and less than 10'. 
	 

# Iteration 
Iterative loops can be written with the `for`, `while` and `break` statements. 

#### For loops
Defining a `for` loop is similar to defining a new function. The header ends with a colon and the body is indented with four spaces. The function `range(n)` takes in an integer n and creates a set of values from 1 to n - 1. 

> 	for i in range(4):
>	    print 'Hello world!'


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




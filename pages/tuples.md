---
layout: page
title: Tuples
tagline: Manipulating tuples
---
{% include JB/setup %}

A tuple is an **ordered** sequence of values (any type) which makes them similar to [list](list.html), but the difference is they are immutable (i.e. you cannot modify one of the elements of a tuple on the left side of the assignment operator). The downside of this is that tuples have no methods (e.g. `append()`, `remove()`, `index()`, etc), but the upside is tuples are faster to iterate through and have additional features such as tuple assignments and string formatting that are unique to just tuples.  Tuples are indexed by only integers similar to strings and lists. A tuple is defined by a sequence of comma-separated values (and can be enclosed in parentheses or not)

>	x = 'y', 'o'
>	x = ('y', 'o')
>	print x 

An empty tuple can be defined using `tuple()'

>	y = tuple()
> 	print y

which return an empty set of parentheses.  

If the argument of `tuple()` is a string, list or tuple, the output will be comma-separated values of the elements

>	x = tuple('yo')
>	print x  

The function `len()` can be used to calculate the number elements in the tuple.  

>	len(x)


## Tuple operators 
Similar to strings and lists, there are many tuple operators. For example, the operators + and * also work on tuples.  The operator + concatenate tuples  and the operator * repeats a tuple a given number of times. 

>	y = tuple('lo')
>	x + y

would make ('y', 'o', 'l', 'o') and 

>	z = (x + y) * 3

would make ('y', 'o', 'l', 'o', 'y', 'o', 'l', 'o', 'y', 'o', 'l', 'o'). 

#### Bracket operator
Elements of a tuple can be extracted using the bracket operator `[]`.  Tuple indices are similar to string and list indices: an integer can be used to return specific elements of a given tuple (starting with the first element as 0). If an index is negative, it returns the elements starting from the end of the tuple.  The slice operator (or colon) is used to extract multiple elements of a tuple. 

>	z[0:3]

#### In operator
Similar to strings, lists and dictionaries, the `in` (and `not in`) operator works with tuples. The operator will check if an element is in a given tuple and return a `True` or `False`: 

>	's' in z

#### Relational operators
The operator `is` can be used to test if two tuples are equal. The operators <, > can be used as well. Python starts by comparing the first element from each sequence. If they are equal, it goes on to the next elements, and so on, until it finds elements that differ. Subsequent elements are not considered (even if they are really big).


## Tuple assignment
A unique feature of tuples is the use of the **tuple assignment** which equates two sets of comma-separated values together across an `=` sign.  For example, if you want to split the string `www.google.com` by the periods and assign each of the three sections to unique variables, you could do use the string method `split()` which will return a list with three elements. 

>	url = 'www.google.com' 
>	start, middle, end = url.split('.')
>	print start

would return the string 'www'. 

Another example of tuples as return values is the built-in function `divmod` will take in two arguments (a numerator and denominator) and return two values: the quotient and a remainder as a tuple.  

#### Tuple assignments and string formatting 
The tuple assignment operator can also be very useful to format values into strings. If you have a tuple with two or more values and you want to format the values as strings and place in a specific order, you can do that. 

>	myfavs = ('chocolate', 'sprinkles', 'peanuts')
>	print "My favorite toppings are %s, %s, and %s" % myfavs

The first %s is replaced by the first value in the tuple and so forth.  String formatting also works with integers using the %d operator.  To format numbers, use the %f operator. 


## Tuples: gathering and scattering arguments
When defining functions with arguments, one day to define a variable-length argument is to use the `*` operator in front of the argument.  This operator will **gather** a variable-length set of arguments into into a tuple.  

>	def toppings(*args): 
>	    print args

On the other hand, if you have a variable-length set of values you would like to pass to a function as multiple arguments, you can again use the `*` operator to **scatter** the arguments.  

>	myfavs = ('chocolate', 'sprinkles', 'peanuts')
>	toppings(*myfavs)

which will pass the elements of the myfavs tuple to the toppings function as multiple arguments. 

## Zipping strings, lists and tuples
The function `list()` can convert a single tuple into a list.  

There is a built-in function `zip` which takes in two ore more arguments and "zips" them into a **list** of tuples where the first element of each argument are concatenated into one tuple, the second element of each argument are concatenated into one tuple, etc. You can zip together strings: 

>	zip('spot', 'tops')

which will return [('s', 't'), ('p', 'o'), ('o', 'p'), ('t', 's')]. You can zip together two lists: 

>	zip([1,3,5,7], [2,4,6,8])

which will return [(1, 2), (3, 4), (5, 6), (7, 8)].  You can zip together a string and a list: 

>	zip('spot', [2,4,6,8])

which will return [('s', 2), ('p', 4), ('o', 6), ('t', 8)].  

There is no limit on the number of arguments you can zip together.

#### Loop through zipped tuples and `enumerate`
You can access the elements of a tuple in a `for` loop and traverse two (or more) sequences at the same time. 

>	for a, b in zip('spot', [2,4,6,8]):
>	    print a, b

A `for` loop over an empty dictionary does not execute anything. 

The function `enumerate` is a built-in Python function that will allow the user to traverse a sequence of elements AND their indices. 

>	for index, value in enumerate('howdy')
>	    print index, value


## Tuples and dictionaries
You can create a dictionary from a list of tuples. 

>	d = dict(zip('spot', [2,4,6,8]))
>	print d

It's common to use tuples as the keys for a dictionary (mostly because you can't use lists which are mutable).  For example, you can use the first and last name as the key in a dictionary and map it to a phone number

>	names = {'John': 'Smith', 'Mark': 'Twain'}
>	nums = '888-888-1000', '888-555-2000'
>	directory = dict(zip(names.items(), nums))
>	for first, last in directory:
>	    print first, last, directory[first, last]

Combining the tuple assignment and list comprehension, you can loop through dictionaries easily. 

>	["%s=%s" % (k, v) for k, v in names.items()]
>	["%s=%s" % (k, v) for k, v in directory.items()]
 
In the first line, we loop through all the key-value pairs in the dictionary titled "names" using a `for` loop, use the tuple assignment operator to name the key-value pairs, and then use string formatting to print the pairs in a specific format.  

## Tuple methods
As stated above, because tuples are immutable, Python doesn't provide methods like `sort` and `reverse`, which modify existing lists. But Python provides the built-in functions `sorted` and `reversed`, which take any sequence as a parameter and return a new list with the same elements in a different order.

## Why use tuples over lists? 

* Tuples are faster than lists. If iterating over a set of values, use a tuple instead of lists. 
* Assures your data won't be altered in the processing of your data. 
* Dictionary keys must be immutable and tuples are immutable. Therefore tuples can be used as keys in a dictionary (but lists cannot).  
* Tuple assignments allow for **string formatting** (vs concatenating strings) and **number formatting**

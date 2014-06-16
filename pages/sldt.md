---
layout: page
title: Overview
tagline: Strings, Lists, Dictionaries, Tuples
---
{% include JB/setup %}

The four main types of objects you will work with are [strings](pages/strings.html), [lists](pages/lists.html), [dictionaries](pages/dictionaries.html) and [tuples](pages/tuples.html).  Knowing how to manipulate these objects is incredibly important in Python. Before discussing each object in detail, I wanted to give an overview of the four objects.  

| | strings | lists | dictionary | tuple | 
| --- | :---: | :---: | :---: | :---: |
| Immutable or mutable? | immutable | mutable | mutable | immutable |
| Indexed by? | integers | integers | any immutable type | integers |
| operators + and * ? | Yes | Yes | No | Yes | 
| `in` operator? | Yes | Yes | Yes | Yes |

Definitions: 

* A string is a sequence of characters. 
* A list a sequence of values which can be characters, integers or even another list (referred to as a nested list). 
* A dictionary is a more general version of a list and is made up a set of **keys** and **values** where there is a mapping between a given key and its corresponding value. There is no order to the set of keys and values. 
* A tuple is a sequence of values (any type) which makes them similar to lists, but the difference is they are immutable.  


Immutable vs mutable: 

* Strings are **immutable**. When using strings, bracket operators cannot be used on the left side of an assignment with the intention of changing that string. 
* Lists are **mutable**. Unlike strings, you can use the bracket operator on the left side of the assignment to change an element in a given list. 
* Dictionaries are 
* Tuples are **immutable**.  

The `in` operator: 

* The `in` operator is a boolean operator takes in two arguments that determines if the first argument is a substring or a element of the second argument.  
	* When comparing two strings, the operator searches if the first string appears as a substring in the second and returns a `True` or `False`. 
	* If the second argument is a list, the operator that can take in two a string and a list to see if the string appears as one of the elements in the list and returns a `True` or `False`. 


The function `len()` can be used to: 
* Calculate the length of a string
* Calculate the number of elements in a list
* Calculate the number of items in a dictionary
* Calculate the number elements in the tuple



# Sequences of sequences
In the subsequent pages, I will compare and contrast the similarities and differences of strings, lists, dictionaries and tuples in greater detail.  In general, lists are more common than tuples (mostly because they are mutable), but there are a few reasons why tuples may be preferable: 

1. In some contexts, like a return statement, it is syntactically simpler to create a tuple than a list. In other contexts, you might prefer a list.
2. If you want to use a sequence as a dictionary key, you have to use an immutable type like a tuple or string.
3. If you are passing a sequence as an argument to a function, using tuples reduces the potential for unexpected behavior due to aliasing.

Because tuples are immutable, they don?t provide methods like `sort` and `reverse`, which modify existing lists. But Python provides the built-in functions `sorted` and `reversed`, which take any sequence as a parameter and return a new list with the same elements in a different order.



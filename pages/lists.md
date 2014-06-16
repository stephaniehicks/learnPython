---
layout: page
title: Lists
tagline: Manipulating lists
---
{% include JB/setup %}

A list a sequence of values which can be characters, integers or even another list (referred to as a nested list). 
Lists are defined with brackets `[` and `]`.  

>	hobbies = ['running', 'baking', 'blogging']

You can create an empty list (or initialize a list) with an empty set of brackets.

>	emptylist = []

The function `len()` can be used to calculate the number of elements in a list.  

>	len(hobbies)

To convert a string to a list of characters use `list`

>	list(hobbies[0])


## List operators 
Similar to strings, there are many list operators. For example, the operators + and * also work on lists.  The operator + concatenate lists  and the operator * repeats a list a given number of times. 

>	a = [5, 10]
>	b = [26, 30]
>	a + b
>	a * 3


#### Bracket operator
As shown above, a list is define with the bracket operator `[]`.  List indices are similar to string indices: an integer can be used to return specific elements of a given list. If an index is negative, it returns the elements starting from the end of the list.  The slice operator (or colon) is used again similar to strings

>	hobbies[0:1]

#### In operator
Similar to strings, the `in` operator works with lists. The operator will check if an element is in a given list and return a `True` or `False`: 

>	'blogging' in hobbies

The `in` operator can be used in conditional statements such as `if` / `else` statements. 

>	if hob in hobbies: 
>	    print hob

#### Relational operators and aliases 
You can create an alias for a given list list which means you are creating more than one name of the same object.  You can test if two lists are aliases using the relational operator `is`.  The problem is because lists are mutable, if you alter one aliased object, you will alter the other aliased object.  

>	a = [5, 10]
>	b = a
>	b is a
>	b[0] = 20
>	print a

which will return a list [20, 10]. In general, it's best to avoid aliases and make copies instead.  

The operator `is` can be used to test if two lists are equal. The operators <, > can be used to test the alphabetical order of lists. 


## Loop through lists
To traverse through the sequence of elements in a list, you can use `for` loops combined with `len` and `range`: 

>	for i in range(len(a)):
>	    a[i] = a[i] * 2

A `for` loop over an empty list does not execute anything. 


## List methods
Similar to strings, there are set of list methods in Python that are useful to manipulate lists. The syntax is the name of the list followed by a dot (or period) followed by the name of the list method.  
If you want to delete a specific element in a list, you can use `del`

>	del a[1]
> 	print a




#### List of list methods
* `append()` = add a new element to the end of a list
* `extend()` = similar to append except, function can take in a list as an argument and appends all the elements
* `sort()` = arrange the elements of the list from low to high
	* sort(reverse=True) = tells sort to go in decreasing order
* `pop()` = deletes an element from the list and returns the element that was removed. If no index is provided as an argument, it deletes and returns the last element. 

>	a = [5, 10]
>	a.append(35)
>	a.extend(b)
>	a.sort()
>	k = a.pop(0)

* `split(delimiter)` = breaks a string into words. If no argument is provided it splits based on white spaces. If the delimiter is provided as an argument, it will split based on that parameter

>	newstring = "Howdy! How are you today?"
>	newstring.split()

* `join(delimiter)` = concatenates a set of strings with a given delimiter

>	delim = ' '
>	hobbies.join(delim)

It is important to note some of these methods modify the current list and other methods create new lists. For example the operators :, + and * create new lists, but `append`, `extend` and `sort` will modify the current list. In addition, if you try to assign the newly modified list to the same variable 

>	a = a.sort()
> 	print a

then nothing will be returned. 



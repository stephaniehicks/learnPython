---
layout: page
title: Strings and Lists
tagline: Manipulating strings and lists
---
{% include JB/setup %}

Knowing how to manipulate strings and lists are two incredibly important tools in Python.  

# Overview

* A string is a sequence of characters. A list a sequence of values which can be characters, integers or even another list (referred to as a nested list). 
* The bracket operator `[]` has multiple uses in Python. It can be used to subset characters in a given string. It is also used to define a list. 
* Strings are **immutable** and lists are **mutable**. 
	* When using strings, bracket operators cannot be used on the left side of an assignment with the intention of changing that string. 
	* Unlike strings, you can use the bracket operator on the left side of the assignment to change an element in a given list. 
* The `in` operator is a boolean operator takes in two arguments that determines if the first argument is a substring or a element of the second argument.  
	* When comparing two strings, the operator searches if the first string appears as a substring in the second and returns a `True` or `False`. 
	* If the second argument is a list, the operator that can take in two a string and a list to see if the string appears as one of the elements in the list and returns a `True` or `False`. 
* The function `len()` can be used to calculate the length of a string or the number of elements in a list. 
* The function `range()` can be used to return a list of indices from 0 to $n$-1$.




# Strings

## String operators


#### Bracket operator
To access a particular character in a string, you can use the bracket operator `[]`. In Python, the first character in a string starts at 0 (not 1). For example, the following would return the first character 'c' in the string 'chocolate':

>	dessert = 'chocolate'
>	dessert[0]

* To extract characters starting from the end of the string, use negative numbers (e.g. dessert[-1] for the last character and dessert[-2] for the second to last character, etc).  
* To extract multiple characters (or a segment), use the bracket operator with a colon (:) also known as a slice operator. For example, use `[m:n]` where m is the position to start and n is the position to end. If the n is missing, then the characters starting from position m to the end of the string are extracted (similar idea if m is missing). 
* The bracket operator can take in a third argument `[m:n:s]` which is the step size of s between characters. A step size of -1  goes through the word backwards. For example, the following will print 'chocolate' backwards: 

>	dessert[::-1]


#### In operator
If you want to search if one string is a substring of a second string, use the boolean string operator `in`: 

>	`late` in `chocolate`

The `in` operator can be used in conditional statements such as `if` / `else` statements. Here is a function to print all the letters in one word that appear in a second word: 

>	if letter in word: 
>	    print letter

#### Relational operators
The operator == (or `is` ) can be used to test if two strings are equal. The operators <, > can be used to test the alphabetical order of strings. 


## Loop through strings
To traverse through all characters in a given string, you can use `for` or `while` loops. Here we create the names of the duck statues in the Public Gardens in downtown Boston: Jack, Kack, Lack, Mack, Nack, Oack, Pack, Qack. 

>	prefixes = 'JKLMNOPQ'
>	suffix = 'ack'
>	for letter in prefixes:
>	    print letter + suffix

If you want to compare adjacent letters, you may want to use a `while` loop. For example, if you want to determine if a word is a palindrome: 

>	def is_palindrome(word):
>	    i = 0
>	    j = len(word) - 1
>	    
>	    while i < j:
>	        if word[i] != word[j]:
>	            return False
>	        i = i + 1
>	        j = j - 1
>	    
>	    return True

## String methods
There are a set of methods in Python that take in a string and return a value (similar to a function, but different syntax).  The syntax is the name of the string followed by a dot (or period) followed by the name of the method. 

#### List of string methods
* `upper()` = take in a string and return the string in all upper case letters
* `find()` = find all the substrings in a string
* `strip()` = gets rid of the white space in a string

For example, if you want to , use the word `upper` or find all the 'o''s in a word, use `find`: 

>	dessert.upper()
>	dessert.find('o')

The `find` method can also take in a starting position and a stopping position of where it should search, but remember it starts at 0. 






# Lists
* Lists are defined with brackets `[` and `]` and you can create an empty list with an empty set of brackets. 

>	hobbies = ['running', 'baking', 'blogging']

* List operators: + and * . The operator + concatenate lists  and the operator * repeats a list a given number of times. 

>	a = [5, 10]
>	b = [26, 30]
>	a + b
>	a * 3

* To convert a string to a list of characters use `list`

>	list(hobbies[0])



## List operators 

#### Bracket operator
List indices are similar to string indices: an integer can be used to return specific elements of a given list. If an index is negative, it returns the elements starting from the end of the list.  The slice operator (or colon) is used again similar to strings

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

The operator `is` can be used to test if two lists are equal. The operators <, > can be used to test the alphabetical order of strings. 


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
* `extend()` = takes a list as an argument and appends all the elements
* `sort()` = arrange the elements of the list from low to high
* `pop()` = deletes an element from the list and returns the element that was removed. If no index is provided as an argument, it deletes and returns the last element. 
* `split(delimiter)` = breaks a string into words. If no argument is provided it splits based on white spaces. If the delimiter is provided as an argument, it will split based on that parameter
* `join(delimiter)` = concatenates a set of strings with a given delimiter

>	a = [5, 10]
>	a.append(35)
>	a.extend(b)
>	a.sort()
>	k = a.pop(0)

>	newstring = "Howdy! How are you today?"
>	newstring.split()

>	delim = ' '
>	hobbies.join(delim)

It is important to note some of these methods modify the current list and other methods create new lists. For example the operators :, + and * create new lists, but `append`, `extend` and `sort` will modify the current list. In addition, if you try to assign the newly modified list to the same variable 

>	a = a.sort()
> 	print a

then nothing will be returned. 






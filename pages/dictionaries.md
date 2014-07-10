---
layout: page
title: Dictionaries
tagline: Manipulating dictionaries
---
{% include JB/setup %}

A dictionary is a more general version of a [list](list.html) because the index does not necessarily have to be an integer. A dictionary is defined by a set of *case-sensitive* **unordered** items (pairs of **keys** and **values**) where there is a mapping between a given key and its corresponding value. There is no order among the items in a dictionary.  To define a new dictionary, use the Python built-in function `dict()` or empty curly braces: 

>	names = dict()
>	names = {}
>	print names

The second line will return an empty set of curly brackets representing an empty dictionary.   

The function `len()` can be used to calculate the number **items** (i.e. key-value pairs) in a dictionary. 

>	len(names)

**Note about dictionary keys**: Though the keys (or indices for a dictionary) can be values other than integers, the keys must be immutable. Keys can be strings, integers or [tuples](tuples.html) which is discussed in the next section.  Items such as lists (which are mutable) cannot be used as keys in a dictionary, but lists can be values in a dictionary.  The reason is because a dictionary is implemented using a *hashtable* and the keys must be *hashable*.  

**Note about dictionary values**: Dictionaries values can be any type (strings, integers, other objects, or even other dictionaries).  

## Dictionary operators 
The operators + and * **do not** work on dictionaries.

#### Bracket / curly bracket operator
To add an item (key and value) to the dictionary, you can do one of the following ways: (1) use the bracket operator `[]` or (2) the curly bracket operator `{}`:

>	names['John'] = 'Smith'
>	names = {'John': 'Smith', 'Mark': 'Twain'}

In the second line, you can multiple items with commas separating the key and values where here the **key** is the first name 'John' and the **value** is the last name 'Smith'.  If you want to **lookup** a value given a dictionary and a key, you can use 

>	print names['John']

which will return the string 'Smith'. 

**Note**: You cannot have duplicate keys in a dictionary. Assigning a value to an existing key will over-write the old value. 

**Note**: You cannot **reverse lookup** a key (k) given a dictionary (d) and a value (v). There may be more than one key that maps to a given value, so you may have a list of keys that map to a given value.  

>	def reverse_lookup(d, v):
>	    for k in d:
>	        if d[k] == v:
>	            return k
>	    raise ValueError, 'value does not appear in the dictionary'

The last line uses the statement `raise` which can take in a detailed error message.  Here, if the value does not exist in the dictionary, then we 'raise' an error message.  

If you want to delete a specific item in a dictionary, you can use `del`

>	del names['Mark']
> 	print names


#### In operator
Similar to strings and lists, the `in` (and `not in`) operator works with dictionaries. The operator will if a **key** exists in a dictionary and return a `True` or `False`. 

>	'John' in names

To check if a value exists in a dictionary, you can use the dictionary method `values()`

>	printvals = names.values()
>	'Smith' in printvals



## Loop through dictionaries
To traverse through a set of keys in a dictionary, you can use `for` loops (similar to strings and lists): 

>	for keys in names:
>	    print names[keys]

A `for` loop over an empty dictionary does not execute anything. 

Another way to loop through the items in a dictionary is to use the dictionary method `items()` which lists all the key-value pairs in the dictionary. Here we assign a name to the keys and a names to the values and then print each parameter. 

>	for key, val in names.items():
>	    print key, val


## Dictionary methods
Similar to strings, there are set of dictionary methods in Python that are useful to manipulate dictionaries. The syntax is the name of the dictionary followed by a dot (or period) followed by the name of the dictionary method.  


#### List of dictionary methods
* `keys()` = returns all the keys as a list from a dictionary
* `values()` = returns all the values as a list from a dictionary
* `items()` = returns the list of items in the diction as a list of tuples

>	names.keys()
>	names.values()
>	names.items()

* `get()` = takes in a key and a default value as arguments and will return the value in the dictionary if the key exists or the second argument if the key does not exist. For example, 

>	names.get('John', 'Cooper')

will return 'Smith', but the following will return 'Cooper'

>	names.get('Jack', 'Cooper')

* `append()` =  
* `update()` = takes in a list of tuples and adds them to the dictionary as key-value pairs to an existing dictionary
* `clear()`= deletes all items from a dictionary

>	del names.clear()

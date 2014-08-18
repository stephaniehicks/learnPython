---
layout: page
title: Python modules
tagline: Cleaning data
---
{% include JB/setup %}

Modules to manipulate regular expressions and string manipulation

#### re
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

#### string 
* `string.punctuation()`
* `string.strip()`
* `string.replace()`
* `string.translate()`


#### collections
The [collections](https://docs.python.org/2/library/collections.html) module contains functions to expand upon Python's built in data types (`list`, `tuple`, `dict`, etc).  

`collections` class | Interpretation 
--- | ---
`namedtuple()` | a class similar to a `tuple` with named fields
`deque` | a class similar to a `list` that can quickly `append` and `pop` (on either end)
`Counter` | a subclass of `dict` that can be used for counting hashable objects
`OrderedDict` | a subclass of `dict` that remembers the order entries were added
`defaultdict` | a subclass of `dict` that allows for missing values


#### datetime
The datetime module can be used to print out the date and time. the function `now()` will print out the current day and time. Some attributes inclue `year`, `month`, `day`, `hour`, `minute`, `second`. 

>	import datetime 
>	now = datetime.now()
>	print '%s/%s/%s' % (now.month, now.day, now.year)




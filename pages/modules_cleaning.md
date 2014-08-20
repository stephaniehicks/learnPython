---
layout: page
title: Python modules
tagline: Cleaning data
---
{% include JB/setup %}

# Modules: parsing html and xml pages

#### pattern
The [pattern](http://www.clips.ua.ac.be/pages/pattern) module can be used to parse HTML and XML pages. The `pattern.web` module is a submodule of `pattern` which can be used to parse HTML [Document Object Model](http://en.wikipedia.org/wiki/Document_Object_Model) (DOM), strip HTML tags, and 

>	from pattern import web

The HTML DOM parser in `pattern.web` is very easy to use.  Use the `Element()` function to parse the text from the webpage.  For example, if we want to parse the text from google.com by `script`, we would 

>	r = requests.get("http://www.google.com")
>	dom = web.Element(r.text)
>	dom.by_tag('script')

This returns a list of nested `Element`s with a given tag name (e.g. `script`, `graph`, `meta`, `div`, etc). The typical use is to use a `for` loop to loop through this list. e.g. 

>	url = 'http://www.imdb.com/search/title'
>	params = dict(sort='num_votes,desc', start=1, title_type='feature', year='1950,2012')
>	r = requests.get(url, params=params)
>	
>	dom = web.Element(r.text)
>	for movie in dom.by_tag('td.title'):
>	    title = movie.by_tag('a')[0].content
>	    rating = movie.by_tag('span.value')[0].content
>	    print title, rating


#### BeautifulSoup
The [BeautifulSoup]() module is similar to parsing HTML and XML pages using [pattern](http://www.clips.ua.ac.be/pages/pattern). To import the module, use

>	from BeautifulSoup import BeautifulSoup

To extra the movie titles and ratings as above in the pattern module, use 

>	url = 'http://www.imdb.com/search/title'
>	params = dict(sort='num_votes,desc', start=1, title_type='feature', year='1950,2012')
>	r = requests.get(url, params=params)
>	
>	dom = web.Element(r.text)
>	for movie in bs.findAll('td', 'title'):
>	    title = movie.find('a').contents[0]
>	    rating = movie.find('span', 'value').contents[0]
>	    print title, rating



#### sgmllib 
The [sgmllib](https://docs.python.org/2/library/sgmllib.html) module is a simple SGML (Standard Generalized Mark-up Language) parser.  The goal of the module is to process HTML code.  The main function is `SGMLParser` which parses HTML code into 8 kinds of data: 

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



# Modules: parsing JSON objects

#### json
The [json](https://docs.python.org/2/library/json.html) module can be used to parse JSON (JavaScript Object Notation) objects to a Python dictionary. 

>	import json

The `json.loads()`function can be used to parse by line

>	path = 'myjsonfile.txt'
>	mydict = [json.loads(line) for line in open(path)]




# Modules to manipulate regular expressions and string manipulation

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




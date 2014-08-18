---
layout: page
title: Python modules
tagline: Scraping data from web
---
{% include JB/setup %}


#### urllib
This builtin Python module is useful to getting information about and retrieving data from the web. The function `urlopen()` open a URL (similar to opening a file).  The file-like object has some of the methods as a file object.  For example, to read the entire HTML of the webpage into a single string, use the method `read()`. `readlines()` can read in the text line by line. 

>	import urllib
>	x = urllib.urlopen("http://diveintopython.org")
>	htmlSource = x.read()
>	x.close()
>	print htmlSource
 
Once you have the HTML source code, you have to parse it and clean it up.  


#### requests
The [requests](http://docs.python-requests.org/en/latest/) module is a more user-friendly version of urllib with more features.  The function `requests.get()` creates a `request` object containing the information about a given webpage and the parameter `.text` downloads the text from the webpage. The parameter `.url` returns the url. 

>	import requests
>	url = 'http://www.google.com'
>	r = requests.get(url)
>	print r.text
>	print r.url 

The webpage is returned as a block of text which will then need to be parsed to extract the interesting information. 

If you do not want to explicitly type the URL, you can specify a base URL with a `get` dictionary

>	url = 'http://www.imdb.com/search/title'
>	params = dict(sort='num_votes,desc', start=1, title_type='feature', year='1950,2012')
>	r = requests.get(url, params=params)
>	print r.url 


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




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



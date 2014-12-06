---
layout: page
title: learnPython
tagline: Tutorial for data analysis in Python
---
{% include JB/setup %}

Python is a **high-level**, **object-oriented** programming language useful to know for anyone [analyzing data](http://lorenabarba.com/blog/why-i-push-for-python/).  The most important thing to know before learning Python, is that in Python, *everything* is an **object**.  There is no compiling and no need to define the type of variables before using them.  No need to allocate memory for variables. The code is very easy to learn and easy to read (syntax).  

There is a large scientific community contributing to Python. Three of the most widely used libraries in Python for data analysis are [numpy](http://numpy.scipy.org), [scipy](http://www.scipy.org), [pandas](http://pandas.pydata.org), and [matplotlib](http://www.matplotlib.org). In addition, users can use [IPython](http://ipython.org) which is an *interactive* command-line tool for the Python programming language. When performing data analysis with Python, the tasks will be (generally) broken up into the following categories: 

1. Scrapping data from web or reading from files / databases
2. Data cleaning, munging, transforming, reshaping
3. Exploratory data analysis e.g. histograms, scatterplots, boxplots
4. Applying statistical models e.g. performing some kind of estimation
5. Reporting results e.g. using graphics or tables

You may be familiar with another programming language such as [R](http://cran.us.r-project.org) or [Matlab](http://www.mathworks.com/products/matlab/), [SAS](http://www.sas.com/en_us/home.html), [SPSS](http://www-01.ibm.com/software/analytics/spss/), [Julia](http://julialang.org) or [Mathematica](http://www.wolfram.com/mathematica/), but [Python](https://www.python.org) is an essential language to know when it comes to [data analysis](http://seanjtaylor.com/post/39573264781/the-statistics-software-signal). As there are many other programming languages out there for data analysis / statistics, I wrote this tutorial (really an *expanded cheatsheet*) assuming the reader has some previous background in at least one programming language and some statistical background.  The idea *what* things like `for` loops are will not be discussed, but rather the syntax of `for` loops in Python will be discussed.  



I break down this tutorial into sections. The first section contains the essentials of how to program in the Python language.  The second section is more focused on actual data analysis in Python.  I also want to mention this tutorial is currently evolving and I will add material to it frequently over the next few months.  If there is a topic you would like to see included in this tutorial, I would love to hear your suggestions.  

### Essentials of programming in Python: 

* [Starting with Python](pages/startingPython.html)
* [Variables, functions, conditionals and iteration](http://nbviewer.ipython.org/github/stephaniehicks/learnPython/blob/gh-pages/pages/basics.ipynb)
* [Strings, lists, dictionaries and tuples](pages/sldt.html)
	* [Strings](http://nbviewer.ipython.org/github/stephaniehicks/learnPython/blob/gh-pages/pages/strings.ipynb)
	* [Lists](http://nbviewer.ipython.org/github/stephaniehicks/learnPython/blob/gh-pages/pages/lists.ipynb)
	* [Dictionaries](http://nbviewer.ipython.org/github/stephaniehicks/learnPython/blob/gh-pages/pages/dictionaries.ipynb)
	* [Tuples](http://nbviewer.ipython.org/github/stephaniehicks/learnPython/blob/gh-pages/pages/tuples.ipynb)
* [Classes: objects, attributes and methods](pages/classes.html)	
* [Import Modules](pages/modules.html)


### Data analysis for Python: 

* [IPython](pages/IPython.html)


Scrapping data from web. Reading data from files / databases. 

* [Import/export files and databases](pages/import.html)
* [Modules for scrapping data from web](pages/modules_scraping.html)
* [Modules for importing and exporting from databases](pages/modules_databases.html)


Data cleaning, munging, transforming, reshaping. Exploratory data analysis. Statistical models. 

* [NumPy](pages/numpy.html)
* [SciPy](pages/scipy.html)
* [Pandas](pages/pandas.html)
* [Exploratory data analysis](pages/modules_eda.html)
* [Probability and statistics modules](pages/modules_statistics.html)


### Further reading & other great resources: 

* [Resources](pages/resources.html)
* [Documentation](pages/documentation.html)

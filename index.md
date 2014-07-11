---
layout: page
title: learnPython
tagline: Tutorial for data analysis in Python
---
{% include JB/setup %}

Python is a useful **high-level**, **object-oriented** programming language to know for anyone analyzing data.  There are many reasons why Python is a useful programming language for data analysis and one of the better explanations is [here](http://lorenabarba.com/blog/why-i-push-for-python/). 

Everything is an **object** in Python: strings, lists, functions and even modules. Not all objects are required to have **attributes** and **methods** to operate on the objects in Python, but **everything is an object** (i.e. all objects can be assigned to a variable or passed as an argument to a function).  A user can work with built-in defined classes of objects or can create new classes of objects.  Using these objects, a user can perform operations on the objects by modifying / interacting with them. Another unique aspect of object-oriented programming is the **inheritance** property.  You can define new classes of objects that are a modified version of an existing class, therefore the new object will "inherit" all the properties of the existing class.  

You may be familiar with another programming language such as [R](http://cran.us.r-project.org) or [Matlab](http://www.mathworks.com/products/matlab/), [SAS](http://www.sas.com/en_us/home.html), [SPSS](http://www-01.ibm.com/software/analytics/spss/), [Julia](http://julialang.org) or [Mathematica](http://www.wolfram.com/mathematica/), but [Python](https://www.python.org) is an essential language to know when it comes to [statistical software for data analysis](http://seanjtaylor.com/post/39573264781/the-statistics-software-signal). As there are many other programming languages out there for data analysis / statistics, I wrote this tutorial (really an *expanded cheatsheet*) assuming the reader has some previous background in at least one programming language and some statistical background.  The idea *what* things like `for` loops are will not be discussed, but rather the syntax of `for` loops in Python will be discussed.  

I break down this tutorial into sections. The first section contains the essentials of how to program in the Python language.  The second section is more focused on actual data analysis in Python.  I also want to mention this tutorial is currently evolving and I will add material to it frequently over the next few months.  If there is a topic you would like to see included in this tutorial, I would love to hear your suggestions.  

#### Essentials of programming in Python: 

* [Starting with Python](pages/startingPython.html)
* [Variables, functions, conditionals and iteration](pages/basics.html)
* [Strings, lists, dictionaries and tuples](pages/sldt.html)
	* [Strings](pages/strings.html)
	* [Lists](pages/lists.html)
	* [Dictionaries](pages/dictionaries.html)
	* [Tuples](pages/tuples.html)
* [Classes: objects, attributes and methods](pages/classes.html)	
* [Import Modules](pages/modules.html)
* [Import/export files and databases](pages/import.html)

#### Data analysis for Python: 

* [IPython](pages/IPython.html)
* [NumPy and SciPy](pages/numpy_scipy.html)
* [Documentation](pages/documentation.html)


## Further reading & other great resources: 
The material for this tutorial was taken from various resources and tutorials found in books and on the web. I have provided a list of the ones that I have found to be most helpful.  

* [Think Python](http://www.greenteapress.com/thinkpython/thinkpython.html)
* [Dive Into Python](http://www.diveintopython.net)
* [Data analysis for Python](http://www.amazon.com/Python-Data-Analysis-Wrangling-IPython/dp/1449319793)
* [Learn Python The Hard Way](http://learnpythonthehardway.org/book/)
* [New Coder](http://www.newcoder.io)
* [Boston Python Puzzles](http://puzzles.bostonpython.com)
* [codeacademy](http://www.codecademy.com/)

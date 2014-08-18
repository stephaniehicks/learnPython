---
layout: page
title: Starting with Python
tagline: Opening Python and Running Python Scripts
---
{% include JB/setup %}

# Python

There are two modes you can write Python code in: **interactive mode** or **script mode**.  If you open up a UNIX command window and have a command-line interface, you can simply type `python` in the shell: 

>	$ python

and the **interactive mode** will open up.  You can write code in the interactive mode and Python will *interpret* the code using the **python interpreter**.  Another way to pass code to Python is to store code in a file ending in `.py`, and execute the file in the **script mode** using 

>	$ python myscript.py

To check what version of Python you are using, type the following in the shell:

>	$ python --version



# IPython

Python by itself is pretty cool, but there are some limitations that make it not very user-friendly.  For example, it lacks tab auto-completion, in-line editing of code, support for parallel processing, command history (with the up and down arrows).  [IPython](http://ipython.org) an *interactive* command-line tool that solves all of these problems.  Some of the features include tab completion, shell syntax, data visualizations, tools for parallel computing.  To start IPython, type `ipython` in the shell: 

>	$ ipython

If you use the argument `--pylab`, then a graphical environment for Python will also be loaded in the backend (e.g. `matplotlib`). 

>	$ ipython --pylab



# IPython notebook

One of the more popular features is the [browser-based IPython notebook](http://ipython.org/notebook.html) which can combine code (and evaluate it), text, equations and plots all in one environment.  To start an IPython notebook session, type `ipython notebook` in the shell: 

>	$ ipython notebook
>	$ ipython notebook <name_of_downloaded_file.ipynb>

If you have an python notebook that you want to open, place the name of the file after `ipython notebook`. Once you have started an IPython notebook server, the browser will display all the `.ipynb` files in the current working directory.   

I'll discuss more on [ipython and ipython notebook in a little bit](IPython.html). 

# Spyder 

The Scientific Python Development EnviRonment or [Spyder](https://code.google.com/p/spyderlib/) is another tool similar to using [Rstudio](https://www.rstudio.com) when writing code in the [R](http://cran.us.r-project.org) programming language. 


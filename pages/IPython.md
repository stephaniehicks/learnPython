---
layout: page
title: IPython
tagline: Installation and Implementation
---
{% include JB/setup %}

[IPython](http://ipython.org) is an *interactive* command-line tool for the Python programming language.  Some of the features include tab completion, shell syntax, data visualizations, tools for parallel computing. One of the more popular features is the [browser-based IPython notebook](http://ipython.org/notebook.html) which can combine code (and evaluate it), text, equations and plots all in one environment. The IPython notebook is similar to using [Rstudio](https://www.rstudio.com) when writing code in the [R](http://cran.us.r-project.org) programming language. 

To start ipython (or ipython notebook) in a command line, use the `ipython` (`ipython notebook`) command

>	$ ipython

Each ipython notebook is comprised of many "cells" which can have code or text in it. To evaluate a cell, click the "play" button at the top of the notebook or click Shift + Enter. 

### Evaluating code in ipython

* To evaluate code, use the `<return>` 
* Pressing <Ctrl-C> will interrupt any code running
* Use the `%run` command to evaluate a `.py` script inside of `ipython` (identical to running `python myscript.py` in command line)

>	%run myscript.py
>	%run -i myscript .py

The second line gives access to using variables defined in the ipython namespace

* Use the `%paste` magic function to take whatever text is on the clipboard and execute it as a single block in the shell (i.e. overcomes code with unexpected indents or new lines)
* Use the `%cpaste` magic function (similar to `%paste`) except you can paste as much code as you would like before evaluating it

### Getting help in ipython

* Tab completion can be used to complete any variables (objects, functions, modules, file paths)
* Use the question mark (`?`) before or after any variable to get help about the object or show the `docstring` (documentation)
* Use a double question mark (`??`) to show functions source code (if available)


### IPython magic commands

As you saw above, ipython has a set of *magic functions* which are special commands that make programming in ipython significantly easier.  To get help use `%quickref` or `%magic`. 

For example, to delete all variables in the interactive namespace use `%reset`.  To time a process use `%timeit`. To print the command input history, use `%hist`.  To create a bookmark to save aliases for common directories, use `%bookmark`

>	%bookmark db ~/Dropbox/



### Themes in IPython

* [Customizing and theming IPython in a single .css file](http://blog.henryhhammond.com/theming-ipython/)
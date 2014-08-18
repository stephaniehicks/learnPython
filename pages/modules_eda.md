---
layout: page
title: Exploratory Data Analysis
tagline: matplotlib
---
{% include JB/setup %}

[Matplotlib](http://matplotlib.org) is a module which is used for 2D and 3D plotting in python, IPython, or other interfaces such as IPython notebooks.    This module will do a lot of what you would expect from a tool to generate scientific figures.  For example you can use \LaTeX within the figure texts and can save the figures in many different formats such as `.eps`, `.png`, `.pdf`, etc.  

# Import matplotlib

We import the `pyplot` which is part of `matplotlib`. `pyplot` is a collection of functions that make `matplotlib` work like MATLAB.  

>	%matplotlib inline
>	import matplotlib.pyplot as plt
>	import matplotlib import rcParams # this module controls the default values for plotting in matplotlib

For example, to change the font size, line width and figure size, 

>	rcParams['font.size'] = 14
>	rcParams['lines.linewidth'] = 2
>	rcParams['figure.figsize'] = (10, 6)


**Note**: When you use matplotlib to plot figures in an IPython notebook, you can configure the figures to be embedded in the notebook (vs opening in a new window) using the `%matplotlib inline` option. 


# Plotting with pyplot
You provide a set of `pyplot` functions to change a figure and then we ask python to show us the figure.  

>	import numpy as np
>	x = np.arange(0, 5, 0.1)
>	y = np.sin(x)
>	plt.plot(x, y)

A slightly more complicated version is 

>	plt.plot(x, y, 'b-', x, y*2, 'rs, x, y*4, 'g^')
>	plt.legend(loc= "topright")
>	plt.legend("X axis")
>	plt.ylabel("Sine curve")
>	plt.title('Pretty since curve')
>	plt.show()

Here we plot three sine curves with different y values.  the string following each pair of (x,y) values represents the color and type of line plotted.  The first line is a blue line, the second is a sine wave represented by red squares, the third is a sine wave represented by green triangles.  

#### Other statistical graphs

Matplotlib function | Description
--- | ---
`plt.plot(x, y)` | Plot x, y values as lines
`plt.scatter(x, y)` | Scatter plots as dots
`plt.hist(x, bins)` | Histogram with defined bin cutoff values
`plt.bar(pos, heights)` | Bar plot 
`plt.barh(pos, heights)` | Bar plot (horizontal)
`plt.pie()` | Pie chart
`plt.boxplot([np.random.rand(1000), np.random.rand(1000) + 1])` | Boxplot



#### Customizing the matplotlib pyplot 

Matplotlib.pyplot function | Description
--- | ---
`plt.title()` | Title of plot
`plt.xlabel()`, `plt.ylabel()` | X and Y axis labels
`plt.xlim(a,b)`, `plt.ylim(a,b)` | X and Y axis limits
`plt.legend(name, loc="topright")` | Title and location of legend
`plt.xticks(loc, labels)`, `plt.yticks(loc, labels)` | X and Y axis ticks (locations and labels). (use option `rotation=45` to rotate 45 degrees)
`plt.grid()` | Controls the axis grids (on, off, colors, etc)
`plt.annotate()` | Create a piece of text referring to a data point (annotation)
`plt.subplot(brows, ncols, plot_number)` | Defines which subplot to plot next (e.g. `plt.subplot(121)` plots 1 row with 2 columns and the last number is the specific subplot 





#### Resources

* [Basic plots using matplotlib](http://www.loria.fr/~rougier/teaching/matplotlib/)
* [Using matplotlib to plot data in IPython](http://www.randalolson.com/2014/06/28/how-to-make-beautiful-data-visualizations-in-python-with-matplotlib)


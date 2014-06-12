---
layout: page
title:  Importing Data into Python
tagline: 
---
{% include JB/setup %}

# Keyboard input
To accept input from the keyboard, use the keyword `raw_input` (in Python 2) or `input` (in Python 3).

# Read in files

#### Read in files one line at a time
If you want to read in a file one line at a time, use the name of the file, dot (or period) and `readline()`. It will read in the characters from a file until it reaches a new line and returns the result as a string. To read in the next line, run the line again. 

>	fin = open('myfile.txt')
>	fin.readline()

If you want read in each line of a file and print each line to the screen, you can use a `for` loop: 

>	fin = open('myfile.txt')
>	for line in fin: 
>	    word = line.strip()
>	    print word


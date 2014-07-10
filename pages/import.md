---
layout: page
title:  Working with Data in Python
tagline: 
---
{% include JB/setup %}

To read or write to a file in the current working directory, you use the function `open()` to "open" the file. 

>	fin = open('myfile.txt')

With the mode `w` as a second parameters, you can write to the file. 

>	fout = open('myoutput.txt', 'w')

**Note**: If the file already exists, using `open()` will clear out everything in the file before writing to it. If the file doesn't exist, the function will create a new file. 



# Reading and writing files

As you have seen, everything is an object in Python.  When you define files such as `fin` and `fout` above, these are file objects have an associated set of methods.  

## Reading files 

>	fin = open('myfile.txt')
>	fin

#### Read in files one line at a time
If you want to read in a file one line at a time, use the methods function `readline()`.  The syntax is the name of the file, dot (or period) and `readline()`. It will read in the characters from a file until it reaches a new line and returns the result as a string. To read in the next line, run the line again. 

>	fin = open('myfile.txt')
>	fin.readline()

#### Current line position in file
The method `tell()` reports the current position of the open file.  When you open a file, the current position is the beginning of the file (position 0). 

>	fin.tell()

#### Read in file at a specific position
To start reading the file at a different position than the current position, use the `seek()` method. The second argument describes how to interpret the first argument (number of bytes) .  

Position | Meaning
--- | ----
`0` | move to absolute position (from start of file)
`1` | move to a relative position (from current position)
`2` | move to a position relative to the end of the file.

>	fin.seek(5, 0)


If you want read in each line of a file and print each line to the screen, you can use a `for` loop: 

>	fin = open('myfile.txt')
>	for line in fin: 
>	    word = line.strip()
>	    print word


#### Keyboard input
To accept input from the keyboard, use the keyword `raw_input` (in Python 2) or `input` (in Python 3).

>	raw_input("How tall are you?")

## Writing to files
To write to a file in Python, the argument must be a string.  If the argument is not a string, use the function `str()` to convert the argument to a string. 

The methods functions `write()` and `close()` will write data to a file and close the file when finished writing to it.  The syntax is the name of the file, a dot (or period), and the function `write()`.  

>	fin.close()
>	fin.closed

The method `closed` will test if the file has been closed returning a True or False. 

#### Writing to files one line at a time
To write to a file one line at a time, just recall `write` again and again. 

>	fout.write("This is my first line.")
>	fout.write("This is my second line.")
>	fout.close()

The last line tell Python you are done writing to the file, so it knows to close the file. Once a file has been closed




# Paths and directories 
To print the current working directory, use the function `getcwd()` from the module `os`. 

>	import os
>	cwd = os.getcwd()
>	print cwd

To find the absolute path to a file use `path.abspath()`: 

>	os.path.abspath('myfile.text')

To check if a file exists, use `path.exists()`:

>	os.path.exists('myfile.text')

To **split** the file and return a tuple containing the path and file name, use `path.split()`. To split the file and return a tuple containing the file name and the file extension, use `path.splitext()`. 

>	(pathdir, nameofile) = os.path.split('~/pathtofile/myfile.txt')
>	(nameofile, extension) = os.path.splitext('myfile.text')

To **join** a path and the name of a file, use `path.join()`

>	os.path.join("nameofnewpath", "myfile.txt")

To check if the argument is a file or a directory, use `path.isfile()` and `path.isdir()`: 

>	os.path.isdir('myfile.text')
>	os.path.isfile('myfile.text')

To list the files in a directory use `path.listdir()`: 

>	os.path.listdir(cwd)

To loop through the files in a directory, combine a `for` loop with `os.listdir()`: 

>	[os.path.join("~/nameofnewpath", elem) for elem in os.listdir(cwd)]


## Errors
* If a module doesn't exist and you try to import it, Python will raise an `ImportError` exception. 
* If a file doesn't exist, if you don't have permission to access a file or if you try to open a directory to read in, you will get an `IOError` exception. 
	* Tip: use functions like `os.path.exists()` and `os.path.isfile()` to test before reading in a file
	* Tip: use the `try` and `except` statements (similar to an `if` statement). 

>	try:
>	    fin = open('myfile.txt')
>	except IOError:
>	    print "This file does not exist."
>	print "File opened."

The line `except IOError` catches when the file does not exist and executes your own code. 


#### The glob module and listing files in directories
The glob module is useful when listing directories, but you do not have the name of the files (just a wildcard e.g. *.txt).  The `glob()` function will match all the *.txt files in a directory and return the them as a list

>	import glob
>	glob.glob('*.txt')


# Databases
A *database* is a specific type of file with a purpose of storing data.  For example, if you have created a dictionary with *keys* and *values*, you can create and update the dictionary database file.  To work with databases, import the Python module `anydbm`. 

To open a database (and create it if it doesn't already exist): 

>	import anydbm
>	db = anydbm.open('mydatabase.db', 'c')

where the 'c' means to create the database if it doesn't exist.  While interfacing with the database, if you add a key-value pair (i.e. item), then the module `anydbm` will update the database file.  After you are finished with the database, close it with the methods function `close()`. 

>	db.close()

#### Pickling a database
The module `anydbm` ONLY works with databases that have keys and values as strings. If your keys or values are not strings, you can use the `pickle` module to translate any object into a string which can be then stored in a database.  When you want to access the database, the module will translate the string back into the original objects.  

>	import pickle

The methods function `pickle.dumps()` takes in any object and returns the string representation and `pickle.loads()` will translate the string object back to the original representation: 

>	x = tuple('yolo')
>	xstring = pickle.dumps(x)
>	xoriginal = pickle.loads(xstring)
>	print xoriginal 

**Note**: pickling and unpickling the object is the same copying the object. It will have the same value, but it not the same object.  

#### Shelve module
The [module](http://python.wikia.com/wiki/Shelve) `shelve` has combined the function in the `anydbm` and `pickle` modules into one easy set of functions to use to interact with databases. 

>	import shelve
>	shelve.open('mydatabase.db')

To interact with this database, use the `shelve()` function

>	newVar = shelve['mykey']
>	shelve['mykey'] = newVar
>	shelve.close('mydatabase.db')




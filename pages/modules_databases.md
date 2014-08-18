---
layout: page
title: Python modules
tagline: Import/export from databases
---
{% include JB/setup %}

These are modules which can be used for importing and exporting databases, dataframes

#### anydbm, pickle and shelve
The `anydbm` module is interfaces and updates database files. The two methods functions to open and close the databases `anydbm.open()` and `anydbmclose()`.  To work with this module, the database must have keys and values as strings!  

If your keys or values are not strings, you can use the `pickle` module to translate any object into a string which can be then stored in a database using the `pickle.dumps()` function.  When you want to access the database, the module will translate the string back into the original objects using the `pickle.loads()` function.  

This method of "pickling" the objects from the `pickle` module combined with the `anydbm` module has been implemented in the `shelve` module.  To open and close files using this module use `shelve.open()` and `shelve.close()` which uses the `pickle` module to open and store the objects. 

#### glob and listing files in directories
The glob module is useful when listing directories, but you do not have the name of the files (just a wildcard e.g. *.txt).  The `glob()` function will match all the *.txt files in a directory and return the them as a list

>	import glob
>	glob.glob('*.txt')



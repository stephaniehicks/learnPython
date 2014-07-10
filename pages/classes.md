---
layout: page
title: Classes
tagline: Objects, functions, and methods
---
{% include JB/setup %}



# User-defined objects
In Python, there many built-in types (or **objects**) such as `int`, `float`, `str`, `list`, `dict`, `tuple`, etc and which were discussed in greater detail [here](basics.html).  In addition to the built-in objects in Python, you can also create your own object (or class).  One advantage of creating your own class of objects is the object is **mutable** which means you can change the object by modifying the attributes. 


A user can use the built-in types (or objects) provided by Python, or a user can create user-defined type (also known as a **class**).  To define a new class, the syntax is

>	class cookbookClass(object):
>	    """Description of new class object.""""

The header starts with the word `class` followed by the name of the new class (which is a kind of `object`) where `object` is a built in type.  The body is a `docstring` that describes what the class does.  

>	print cookbookClass

To create an object of the type `cookbookClass`, you call it like a function. To assign values (or *attributes* which are the elements of the object) to the `cookbookClass` object, you use the dot notation. 

>	x = cookbookClass()
>	x.topFoods = dict(zip(('spaghetti', 'salmon', 'tacos'), (1,2,3)))

To the `cookbookClass` object, I created a topFoods element which contains my top three favorite foods with their rank. The topFoods element is in a dictionary type, so I can recall the rank of each of my favorite foods.  The attributes of the new class can be listed in the `doctoring` when defining the new class: 

>	class cookbookClass(object):
>	    """Description of new class object.
>	    
>	    attributes: topFoods. 
>	    """"

To check if an object has a specific attribute, use the built-in function `hasattr` which return a `True`/`False` value if the the second argument (must be a string) is one of the attributes of the objects (listed as the first object). 

>	hasattr(x, 'topFoods')
>	hasattr(x, '__doc__')

To test if there is a doc string, test if one of the attributes of x is `__doc__`.


# User-defined methods
In addition to creating user-defined types (or objects), you can also create user-defined **methods** which are associated with a particular class of objects.  For example, there are a set of methods associated with strings, lists, dictionaries and tuples that we have already seen.  Methods associated with a specific type of object are similar to functions except: 

1. The syntax for invoking a method is different than the syntax for calling a function. 

2. User-defined methods are defined inside the class definition to make the relationship between the class and method explicit.  To define a method called `print_foods()` associated with our `cookbookClass` object: 

>	class cookbookClass(object):
>	    """Description of new class object.
>	    
>	    attributes: topFoods, 
>	    """"
>	    def print_foods(arg):
>	        print arg.topFoods.keys()
>

The usual way to call a function is the name of the module, followed by a dot (or period) and the name of the function (e.g. `math.pi()`).  To call a method called `print_foods()` on our `cookbookClass` object, you can do one of the following: 

>	x = cookbookClass()
>	x.topFoods = dict(zip(('spaghetti', 'salmon', 'tacos'), (1,2,3)))

>	cookbookClass.print_foods(x)
>	x.print_foods()

where x is the the argument (or **subject**) that the method `print_foods` is invoked on.  The second way is more concise and the more common way to invoke a method associated with a specific class.

#### The init and str method
The `__init__`) method is a method to initialize a set of optional parameters and assigns them as attributes.  

>	class Card(object):
>	    """Represents a standard playing card."""
>	    def __init__(arg, suit=1 rank=12):
>	        arg.suit = suit
>	        arg.rank = rank

We created a new `Card` class which used the `__init__` method to take in two optional parameters for each attribute. The default is the queen of diamonds.  

>	Card(1, 12)

You use this method inside the class definition of the new object. The `__str__` method is similar to the `__init__` method except will return a string representation of an object.  Almost all new classes start with writing `__init__` to initialize objects and `__str__` is useful for debugging.  

In addition to these built in methods, you can create your own special methods such as `__newmethod__`. 


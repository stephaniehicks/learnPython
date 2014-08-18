---
layout: page
title: Classes
tagline: Objects, functions, and methods
---
{% include JB/setup %}



# User-defined objects
In Python, there many built-in types (or **objects**) such as `int`, `float`, `str`, `list`, `dict`, `tuple`, etc and which were discussed in greater detail [here](basics.html).  In addition to the built-in objects in Python, you can also create your own objects with its own characteristics. These are called **classes** which is just a way of pro ducting objects with similar attributes and methods.  One advantage of creating your own class of objects is the object is **mutable** which means you can change the object by modifying the attributes. 


A user can use the built-in types (or objects) provided by Python, or a user can create user-defined type (also known as a **class**).  To define a new class, the syntax is

>	class Employee(object):
>	    """ Creates and Employee class object. """"

The header starts with the word `class` followed by the name of the new class (which is a kind of `object`) where `object` is a built in type.  The body of the class contains a `docstring` that describes what the class does.  

Next, when you define a class, you must **initialize** the objects that the class will create. This is done with the `__init__()` function which always takes at least one argument (by convention this is called `self`) which refers to the object being created.  This must be the first argument passed to `__init__()`.  Think of `__init__()` as the function that creates each object that the class creates.  

>	class Employee(object):
>	    """ Creates and Employee class object. """"
>	    def __init__(self, firstname, lastname, age):

There can be other parameters passed to `__init__()`.  Here, I pass the parameters `firstname`, `lastname` and `age` which are **attributes** of the class `Employee`.  The attributes of the new class can be listed in the `docstring` when defining the new class.  To access the attributes of the objects, use the dot notation.

>	class Employee(object):
>	    """ Creates and Employee class object. 
>	         Attributes: first name, last name, age. """"
>	    def __init__(self, firstname, lastname, age):
>	        self.firstname = firstname
>	        self.lastname = lastname
>	        self.age = age

Here we use the Employee class to store the information about each employee.  For each employee, we create an Employee object. 

>	sarah = Employee("Sarah", "Thomas", 32)
>	print "Employee: %s, %s.  Age %s" % (sarah.lastname, sarah.firstname, str(sarah.age))

Let's say Sarah Thomas got married and changed her last name.  To change the value of attribute of the `Employee` class object, use the dot notation again. 

>	sarah.lastname = "Hoppy"
>	print "Employee: %s, %s.  Age %s" % (sarah.lastname, sarah.firstname, str(sarah.age))


We can also use the `__repr__()` function which to include what we want printed to the console as output

>	class Employee(object):
>	    """ Creates and Employee class object. 
>	         Attributes: first name, last name, age. """"
>	    def __init__(self, firstname, lastname, age):
>	        self.firstname = firstname
>	        self.lastname = lastname
>	        self.age = age
>	    def __repr__(self):
>	        return 'Employee: %s, %s.  Age %s' % (self.lastname, self.firstname, str(self.age))

>	sarah = Employee("Sarah", "Thomas", 32)
>	sarah


To check if an object has a specific attribute, use the built-in attribute `hasattr` which return a `True`/`False` value if the the second argument (must be a string) is one of the attributes of the objects (listed as the first object). 

>	hasattr(sarah, 'age') # True
>	hasattr(sarah, 'eye_color') # False
>	hasattr(x, '__doc__') # True

To test if there is a doc string, test if one of the attributes of x is `__doc__`.


# User-defined methods
In addition to creating user-defined types (or objects), you can also create user-defined **methods** which are associated with a particular class of objects.  For example, there are a set of methods associated with strings, lists, dictionaries and tuples that we have already seen.  Methods associated with a specific type of object are similar to functions except: 

1. The syntax for invoking a method is different than the syntax for calling a function. 

2. User-defined methods are defined inside the class definition to make the relationship between the class and method explicit.  To define a method called `calculate_wage()` associated with our `Employee` object: 

>	class Employee(object):
>	    """ Creates and Employee class object. 
>	         Attributes: first name, last name, age. """"
>
>	    def __init__(self, firstname, lastname, age):
>	        self.firstname = firstname
>	        self.lastname = lastname
>	        self.age = age
>
>	    def calculate_wage(self, hours):
>	        self.hours = hours
>	        return hours * 20.00

The usual way to call a function is the name of the module, followed by a dot (or period) and the name of the function (e.g. `math.pi()`).  To call a method called `calculate_wage()` on our `Employee` object, use: 

>	sarah = Employee("Sarah", "Hoppy", 32)
>	sarah.calculate_wage(40)

where 40 (hours) is the the argument (or **subject**) that the method `calculate_wage` is invoked on.



#### The inheritance property. 
If you want to define a new class of objects that **inherit** all the properties of a previously-defined class, you can easily do that!  The syntax is the keyword `class` followed by the new name of the class and then in parentheses the name of the old class that the new class will inherit all its properties from.  For example, let's create a class called `PartTimeEmployee`.  The only difference is, we want the `calculate_wage()` function to use a different wage.  

>	class PartTimeEmployee(Employee):
>	    def calculate_wage(self, hours):
>	        self.hours = hours
>	        return hours * 12.00

Now we can define a new part time employee (Jack) and calculate his wage for the number of hours he worked (8). 

>	jack = PartTimeEmployee("Jack", "Roberts", 22)
>	jack.calculate_wage(8)



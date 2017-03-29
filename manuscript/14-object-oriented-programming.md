# Object oriented programming

The code we wrote till now was split into functions, this chapter is going to be about object oriented programming. It is a widely used programming paradigm.

We won't be covering OOP extensively, what we will be covering is the absolute basics so that you can then explore OOP in your own if you are interested in it.

When we write programs using OOP, we split them into `objects`. Objects are instances of classes. Till now, we used various classes without being aware of OOP, every data type which we used, right from integer to dictionary was an object of a class. 

## Class
Look around you, you might be sitting in a chair on a desk, the chair is the _object_ and _furniture_ is the class that the chair belongs to. You might be holding a _laptop_ or a _mobile_ with you, both of them are _objects_ of class _utilities_. You might be a child or an adult, _you_ are an object belonging to the _human_ class, the _human_ class is a subset of the _animal_ class.

As a class, we share certain characteristics, like walking, talking, drinking, we all have a name, height, address, hobbies. The actual details might be different, but we do have those _attributes_. Thus, we all are objects of some or the other class. Now, a class in itself can either be the absolute Global class, or it can be a _subclass_ of some class. For instance, our _class_ is human, a kitten belongs to the class _animal_, we humans are a subclass of Animal class.

Animal is the highest class. (Animal class has abstract things like "should have a name", "should either walk, run or crawl", "should eat by mouth")
Humans are a subclass of Animals. (we "inherit" things from our Parent class and we have our own attributes like greed, lust)
Felines are a subclass of Animals (they have things like "love of milk").

#### Define a class

```python
class Human:
    def __init__(self,name, age):
        self.name = name
        self.age = age
    
    def getname(self):
        return self.name
    
    def getage(self):
        return self.age

me = Human("Suraj", 99)
name = me.getname()
age = me.getage()
print("%s:%d"%(name, age))
```

###### Methods
Every function defined inside a class is called a _method_. Each method takes `self` as the first argument. The _self_ points to the object which calls the method during runtime. When we do a `me.getname()`, `self` is the `me` object.

###### Constructor
the `__init__` function is the constructor. It defines how many arguments are passed to the `me = Human()` function call. The `init` is an optional method, if we don't have an init method, then by default, there are no arguments to the class's initialization call.

If you have done OOP before, you'd notice the difference in Python that you do not have to define the variable properties of the class, for instance, it was in the init method that we defined the name and age variable and nowhere at the top of the class definition.

The methods which start and end with `__` are to be used _strictly_ inside the class, they are syntactically internal methods, albeit they can be used by objects outside of the class declaration, we strongly advice against usage of such _internal_ methods outside of the class declaration.

##### Operators as methods

```python
a = Human()
b = Human()
c = a+b
```

This code will result in a syntax error, for operators to work on our class declaration, we need to define the following methods.

There is one method for each operator, let's glance at few methods.

```python
class Human:
    def __init__(self,name, age):
        self.name = name
        self.age = age

    def __add__(self, b):
        return self.age + b.age

    def __sub__(self, b):
        return self.age - b.age

    def __mul__(self, b):
        return self.age - b.age
    
me = Human("Suraj", 99)
you = Human("Batman", 100)

print(me + you)
print(me - you)
print(me * you)

```

Output:

```
book $ python3 ../code/ch14/class-2.py
199
-1
-1
```

If you do not implement `__add__` and you try adding up `me` and `you`, then it won't work as it wouldn't be able to add both of them. For operations like that, the `__` method is invoked on the two objects.

## Printing

Whenever we use the print statement, print(object), where object is a list or a map, then the `__str__` method of that object is called. For this reason, it is essential for declaring an `__str__` method for our class, if we want a human friendly format of the print.

```
def __str__(self):
    return "This is a human of name "+ self.name + " and age "+ str(self.age)

print(me)
```

book $ python3 ../code/ch14/class-2.py
This is a human of name Suraj and age 99

### When to use OOP

It is a matter of taste, but the ideal condition in which we can use OOP is when we are encapsulating data related to objects which we can encapsulate as classes, for instance, if we have three lists, one containint 100 names and other two containing marks of those 100 students in two subjects, then we can create a `Student` class and perform operations on it by creating a list of `Student` objects.

We encourage you to write that program.

#### Docstring Comments

Read the [docs](https://docs.python.org/3/library/doctest.html)

Python does not support multiple line comments. Triple quotes can be used as 'docstrings', for documentation purposes of functions and classes. 

Triple quotes can either be made up of three single quote or three double quotes. They need to be closed appropriately, otherwise they result in an error. Unlike comments, which are ignored, docstrings are evaluated, **not ignored**.

Below is an example:

```python
>>> def function():
...     """ this is a function which does something"""
...     print("hello world")
...
>>> function.__doc__
' this is a function which does something'
```
> From the official docs:
A string literal which appears as the first expression in a class, function or module. While ignored when the suite is executed, it is recognized by the compiler and put into the `__doc__` attribute of the enclosing class, function or module. Since it is available via introspection, it is the canonical place for documentation of the object.


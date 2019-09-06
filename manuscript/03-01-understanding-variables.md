# Variables

Watch on [YouTube](https://www.youtube.com/watch?v=3_-W0S1VdLo) | Read the [docs](https://docs.python.org/3/reference/expressions.html#atom-identifiers)

Variables are used to store values in memory. When using variables in Python, we do not have to declare the datatype of the variable. Python is a dynamic typing language, which means that when the interpreter will execute the code, it will figure out the data type of the variables on it's own.

Every variable has these things:

1. Name: The variable name has to start with any valid unicode letter except those that have special significance like `\` or numbers.
1. Value: The content which is being stored in the variable.
1. Address: The location of the variable in the memory.

There are restrictions about the variable name, 

* They can't start with numbers or special characters. We can not name a variable `0b` or `\a `.
* They can not use reserved keywords (try, catch, if, for, while, except, in among others).

If you want to create a variable `i` with the value 1, type this in the interpreter:

```python
>>> i = 1 
```

This will create a variable `i` which:

1. Has the value 1.
1. Is of the data type integer.
1. Is located in some memory location.

#### Finding address of a variable.

To find out the address of the variable, we use the [id()](https://docs.python.org/3/library/functions.html?highlight=id#id) function.

```python
>>> print(id(i))
405911019
```

405911019 is the memory location of the variable `i`.

#### Finding data type of a variable.
`type` is a builtin function which returns the data type of the argument passed to it. Read the [docs](https://docs.python.org/3/library/functions.html?highlight=id#type)

```python
>>> print(type(1))
<class 'int'>
```

The type() function takes an argument and returns the data type of the argument.

## Taking input from the user.

At times, we want to take input from the user, we can use the `input()` function to do so.

```python
>>> name = input("enter your name: ")
enter your name: python

>>> print("Your name is ", name)
Your name is  python
```

This will take the name of the user as input and store it in variable `name`. `input` takes a string argument which is the message it should print while taking the input.

By default, `input` returns a string. We have to convert a variable from string to integer by using the `int()` function. Each data type provides a function for data type conversion, for instance, `str()` is used to convert a value from other data type to string.

```python
>>> age = input("enter your age: ")
enter your age: 23

>>> age = int(age)

>>> print(type(age))
<class='int'>
```

When we do `age = int(age)`, this is not a syntax error, because the interpreter is going to create a **new** integer variable with the name of age (and delete the old string variable).

## Exercise
1. Take the user's name, age and height and print it to the terminal.
1. Take a number from the user and print it.

```python
>>> i = 'Python'
>>> # Creates a string variable with value Python
>>> print(id(i))
505911019
>>> type(i) # variable i is of type string now.
<class 'string'> 
```

## Variable types

## Numeric 
Read the [docs](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex).

#### Integer

```python
>>> i = 0
>>> i = 10000
>>> i = 123333
>>> print(type(1))
<type 'int'>
```

#### Float

```python
>>> i = 1.1
>>> i = 3.3333344445
>>> print(type(1.0))
<type 'float'>
```

#### Complex

```python
i = complex(1,2) # 1+2j
i = complex(12,23) # 12 + 23j
```

#### String
Read the [docs](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str)

```python
i = "this string\n\t" # \n and \t are special values if used with "
i = 'this string\n\t' # \n and \t are special values if used with '
i = r'this string\n\t' # \n and \t do not hold special value if prepended with r, r stands for raw'
i = ''' multi line string
	which has
	multi lines'''
i = """
	a ridiculously multi line string
	"""
```

##### String validity

The location of the ending quotes doesn't matter, the only thing which matters is that **it should exist**. The value of a string is in between the starting and ending quotes, either single, double or triple.

`'this is a string', "this is a string", "'this is a string", '"this is a string', """ this is 'a string '""", '"""hi'`

All are *valid* strings, they start and end with the same quote. If a string starts and ends with a single quote, then any number of double quotes can be part of the string, the same is true vice versa. 

`'"python"` and `"python''` are invalid strings. Both of them do not start and end with the same quote.

#### Boolean

`True` and `False` are special values in Python3. In previous version of the language, we were allowed to create a variable of name True and False, but now they are reserved. 

Read the [docs](https://docs.python.org/3/library/stdtypes.html#boolean-values)

```python
>>> i = True
>>> j = False
>>> print(i)
True
```

### Sequence type

Read the [docs](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range)

#### List

List stores multiple values of any data type. 

```python
>>> i = [1,"Linux",3,"bash",[1,2,"sh"]]]
```
#### Tuples

Read the [docs](https://docs.python.org/3/library/stdtypes.html#tuple)

Tuples are lists from which elements can't be added/deleted/modified.

```python
>>> a = (1,2)
>>> a[0]=2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
```

```python
a = (1,2,3)
print(a)
```

#### Dictionary
Read the [docs](https://docs.python.org/3/library/stdtypes.html#dict)

Dictionaries are a collection of key value pairs, lists/tuples/sets are indexed sequences, dictionaries aren't.

Here, 'IN' and 'US' are the keys and 'India', 'United States' are the values. The values can be any Python data type, but keys can only be hashable data types (basic data types, int/float/string/complex).

```python
i = {'IN':'India', 'US': 'United States'}
print(i['IN'])
print(i['US'])
```

**Output:**
```
India
United States
```

#### Set
Read the [docs](https://docs.python.org/3/library/stdtypes.html#set-types-set-frozenset)

```python
i = set([1,2,3,4,5])
```

Sets are same as lists, but they don't allow duplicates. Only hashable elements are allowed as their members (int, float, string, complex, tuples).

### Immutability
When a data type is said to be immutable, the data type doesn't allow modifications.

### Hashing
Hashing is a complicated process, just remember, hashable data types = immutable data types.


##### Links

|[Next](03-02-operators.md) | [Previous](02-more-about-language.md) |  [Index](../SUMMARY.md)
| ----| ----| ----| 

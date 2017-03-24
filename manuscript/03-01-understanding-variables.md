# Variables

Watch on [YouTube](https://www.youtube.com/watch?v=3_-W0S1VdLo) | Read the [docs](https://docs.python.org/3/reference/expressions.html#atom-identifiers)

Variables are used to store values in memory. This chapter introduces us to variables, their types and usage. It is understandable if you can't recollect each and every type of data type, come back to this chapter until you remember each data type by heart.

Since Python is a dynamic language, we do not have to declare the data type of the variable. The interpreter will automatically deduce the data type during runtime. Python is a completely object oriented language (even data types are classes) hence all variables are objects. 

A variable has an address and a value.

Creating a variable is simple, the below block creates a variable named `i`, the data type of the variable is deduced by the interpreter as `int`.

```python
>>> i = 1
>>> print(i)
1
```

#### Finding address of variables.

id() is a function which returns the address of an object. You can read more in the docs [here](https://docs.python.org/3/library/functions.html?highlight=id#id).

```python
>>> i = 1
>>> print(id(i))
405911019
```

#### Finding data type of variables.
`type` is a builtin function which returns the data type of the argument passed to it. `type(1)` returns the data type of 1, which is an integer. Read the [docs](https://docs.python.org/3/library/functions.html?highlight=id#type)

```python
type(1) # <class 'int'>
type("this is a string") # <class 'str'>
type(1.2) # <class 'float'>
type("") # <class 'string'> 
# "" or '' is an empty string, equivalent of 0 of integer.
```

## isinstance

isinstance takes two arguments, object and class. If the object is an instance of the class, it returns True, otherwise, it returns False. Read the [docs](https://docs.python.org/3/library/functions.html?highlight=isinstance#isinstance)

```python
>>> isinstance('a string', str)
True
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
`<type 'int'>`
```

#### Float

```python
i = 1.1
i = 3.3333344445
print(type(1.0))
```

The output of `print(type(1.0))` is `<type 'float'>`.

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

#### Boolean

Read the [docs](https://docs.python.org/3/library/stdtypes.html#boolean-values)

```python
i = True
j = False
print(i)
print(i and j)
print(i or j)
print(not j)
```

### Sequence type

Read the [docs](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range)

#### List

List stores multiple values of heterogenous type. Lists can have lists as elements. List values are stored in a continuous order, we can access elements of a list by using idexes, which is the place of the item in the list, indexes start with 0.

```python
i = [1,"Linux",3,"bash",[1,2,"sh"]]]
```

#### Set

Read the [docs](https://docs.python.org/3/library/stdtypes.html#set-types-set-frozenset)

Sets stores "hashable" data types. You can remember this by remembering that sets allow you to store immutable data types (like integer, string, float, tuples). Basic data types like int, float and strings are immutable, when you perform any operation on them, python creates a new variable and does not modify the existing variable, for checking if a new variable is created, you can use the `id()` function described below.

### Immutability
`id()` returns the address of the variable, if two `id` function call return the same address, then it is the same variable, thus, mutable. Read the [docs](https://docs.python.org/3/library/stdtypes.html#immutable-sequence-types)

```python
>>> a = 1
>>> id(a)
4469201376
>>> a = a + 1
>>> id(a)
4469201408
```

 Hashing is the process of converting some large amount of data into a much smaller amount (typically a single integer) in a repeatable way so that it can be looked up in a table in constant-time (O(1)), which is important for high-performance algorithms and data structures. [1](http://stackoverflow.com/questions/2671376/ddg#2671398)

 Dictionary and List are not allowed, but Tuples are.

```python
i = set([1,2,3,4,5])
```

#### Tuples

Read the [docs](https://docs.python.org/3/library/stdtypes.html#tuple)

They are like lists but immutable. Once you create a tuple, you can't delete or add elements. Tuples typically are used when you want to store values which aren't going to change in the lifetime of a program.

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

Lists store multiple heterogenous values in an indexed order starting from 0 and increasing by one, dictionaries are to be used when there is no apparent order in the data, for instance the country acronym and the long form, we can't store that in a list because we would then require two lists, one to store acronym and one to store the full name.

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
##### Links

|[Next](03-02-operators.md) | [Previous](02-more-about-language.md) |  [Index](SUMMARY.md)
| ----| ----| ----| 

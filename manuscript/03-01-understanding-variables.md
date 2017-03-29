# Variables

Watch on [YouTube](https://www.youtube.com/watch?v=3_-W0S1VdLo) | Read the [docs](https://docs.python.org/3/reference/expressions.html#atom-identifiers)

Variables are used to store values in memory. We do not have to declare the datatype of the variable, the interpreter will evaluate the data type on automatically.

Creating a variable in Python is simple, below is a simple example of creating a variable named `i`.

```python
>>> i = 1 
>>> # creates an integer variable of value 1.
>>> print(id(i))
405911019
# address of the variable i
>>> type(1) # returns the data type of variable i.
<class 'int'>
>>> i = 'Python'
>>> # Creates a string variable with value Python
>>> print(id(i))
505911019
>>> type(i) # variable i is of type string now.
<class 'string'> 
```

Variable = address of memory location (returned by `id(i)` function call) + value (which we assign).

As we saw in the earlier example, we can use the same variable name for multiple data types, initially `i` was having value 1, later, it was having value Python. The interpreter does this conversion automatically.

#### Finding address of variables.

id() is a function which returns the address of an object. You can read more in the docs [here](https://docs.python.org/3/library/functions.html?highlight=id#id).

#### Finding data type of variables.
`type` is a builtin function which returns the data type of the argument passed to it. `type(1)` returns the data type of 1, which is an integer. Read the [docs](https://docs.python.org/3/library/functions.html?highlight=id#type)

```python
type(1) # <class 'int'>
type("this is a string") # <class 'str'>
type(1.2) # <class 'float'>
type("") # <class 'string'> 
# "" or '' is an empty string, equivalent of 0 of integer.
```

Now that we learned how to create a variable, find it's data type and it's address, let's have a brief overview of the data types, we will be looking at them in detail in the next chapter.

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

##### String validity

The location of the ending triple quote doesn't matter, the only thing which matters is that **it should exist**. The value of a documentation string is in between the starting and ending triple quotes.

Take the following strings as an example, `'this is a string', "this is a string", "'this is a string", '"this is a string', """ this is 'a string '""", '"""hi'`

These all are *valid* strings, they start and end with the same quote. If a string starts and ends with a single quote, then any number of double quotes can be part of the string, the same is true vice versa. 

But, when the string starts with a single quote, but has no ending single quote (or has more than one single quote), it is a syntax error. `'"sherlock"` is an invalid string, so is `"sherlock''`, because both of these strings do not start and end with the same quote.


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

List stores multiple values of heterogenous type. 

```python
i = [1,"Linux",3,"bash",[1,2,"sh"]]]
```

#### Set

Read the [docs](https://docs.python.org/3/library/stdtypes.html#set-types-set-frozenset)

Sets are same as lists, but they don't allow duplicates. Only hashable elements are allowed as their members (basic data types like int, float, string, complex).

### Immutability

When a data type is said to be immutable, the data type doesn't allow modifications.

`id()` returns the address of the variable, if two `id` function call return the same address, then it is the same variable, thus, mutable. Strings are immutable, as we can see in the below example.

Read the [docs](https://docs.python.org/3/library/stdtypes.html#immutable-sequence-types)

```python
>>> a = '1'
>>> id(a)
4469201376
>>> a = a + '1'
>>> id(a)
4469201408
```
### Hashing

 Hashing is the process of converting some large amount of data into a much smaller amount (typically a single integer) in a repeatable way so that it can be looked up in a table in constant-time (O(1)), which is important for high-performance algorithms and data structures. [1](http://stackoverflow.com/questions/2671376/ddg#2671398)

 Dictionary and List are not allowed, but Tuples are.

```python
i = set([1,2,3,4,5])
```

#### Tuples

Read the [docs](https://docs.python.org/3/library/stdtypes.html#tuple)

Tuples are immutable lists, that is, once a tuple is created, elements can't be added/deleted/modified.

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

Dictionaries are key value pairs, lists/tuples/sets are indexed sequences, dictionaries aren't.

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

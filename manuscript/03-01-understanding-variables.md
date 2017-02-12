# Variables

Watch on [YouTube](https://www.youtube.com/watch?v=3_-W0S1VdLo)

Variables are used to perform operations. Python is a dynamic language, thus, you don't have to define the data type o the variable, the interpreter will evaluate it correctly when it hits the execution, please do note that it happens **during the runtime**.

Python is a completely object oriented language, whenever you create a variable, you are creating an object of the class. 

#### Note:

id() is a function which returns the address of an object.

```python
i = 1
print(id(i))
```

If you type `i = 1`, it creates a variable i, it creates an object of type "int" and stores the address of the object in i.

###### Note:
type is a function which returns the data type of the value it is passed. `type(1)` returns the data type of 1, which is an integer.

```python
type(1) # <class 'int'>
type("this is a string") # <class 'str'>
type(1.2) # <class 'float'>
type("") # <class 'string'> 
# "" or '' is an empty string, equivalent of 0 of integer.
```

You can use `type` to check the data type of a variable. Let's say you want to print a message if a variable is a string.

```python
a = getSomething()

if type(a) == type(""):
	print("a is string")

if type(a) == type(1):
	print("a is integer")
```

`type(a)` is going to return the "str" class, `type("")` is going to return the "str" class. They both are same, thus comparison `==` (**Double equal signs!**) will return true.

## is

Like the `type()` functionn, we have the `is` operator can be used to check the data type of a variable. It can be used in function which accept only a particular data type, you can do `if a is str:` if you want to accept only strings.

```python
>>> a = False
>>> a is bool
False
>>> a is int
False
```
## isinstance

We can also use `isinstance` method for checking the data type.

```python
>>> isinstance('a string', str)
True
```

Variables can be of the following types:

#### Integer

```python
i = 0
i = 10000
i = 123333
```

#### String

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

#### Float

```python
i = 1.1
i = 3.3333344445
```

#### Complex

```python
i = complex(1,2) # 1+2j
i = complex(12,23) # 12 + 23j
```

#### Boolean

```python
i = True
j = False
print(i)
print(i and j)
print(i or j)
print(not j)
```

#### List

List stores an array of values of heterogenous type. Lists can have lists as elements.

```python
i = [1,"Linux",3,"bash",[1,2,"sh"]]]
```

#### Set

Sets stores "hashable" data types. You can remember this by remembering that sets allow you to store immutable data types (like integer, string, float, tuples). Basic data types like int, float and strings are immutable, when you perform any operation on them, python creates a new variable and does not.

### Immutability
`id()` returns the address of the variable, if two `id` function call return the same address, then it is the same variable, thus, mutable.

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

#### Dictionary

A key value pair.

```python
i = {'IN':'India', 'US': 'United States'}
```

#### Tuples

Like lists but immutable. Once you create a tuple, you can't delete or add elements. Tuples typically are used when you want to store values which aren't going to change in the lifetime of a program.


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

##### Links

|[Next](03-02-operators.md) | [Previous](02-more-about-language.md) |  [Index](SUMMARY.md)
| ----| ----| ----| 
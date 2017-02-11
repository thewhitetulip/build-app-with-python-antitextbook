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
i = 'this string\n\t' # \n and \t hold special value if used with '
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

```python
i = [1,2,3,4,5]
```

#### Set

```python
i = set([1,2,3,4,5])
```

#### Dictionary

```python
i = {'IN':'India', 'US': 'United States'}
```

##### Links

|[Next](03-02-operators.md) | [Previous](02-more-about-language.md) |  [Index](SUMMARY.md)
| ----| ----| ----| 
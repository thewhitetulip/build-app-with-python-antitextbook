# High level data structures

In the last chapter we saw the various data types present in Python, in this chapter we'll look at the high level data types in detail.

## List

Watch on [YouTube](https://www.youtube.com/watch?v=30S9LnvanwY) | Read the [docs](https://docs.python.org/3/library/stdtypes.html#list)

An ordered collection of n values (n >= 0)

Creating a list is simple:

```python
>>> l = [] # creates an empty list.
>>> l = list() # creates an empty list.
>>> l = [1, 2, 3]
```

Each element of a list has an index, indices in Python start with 0. 

Let's say we have a list of five values, `a = [11,22,33,44,55]`.

| Value | Positive Index  | 
| ----| ----| 
|11|0|
|22|1|
|33|2|
|44|3|
|55|4|

Indices can be negative. 

| Value |  Negative Index |
| ----|  ----| 
|11|-5|
|22|-4|
|33|-3|
|44|-2|
|55|-1|

List elements can be accessed using indices. 

```python
l = [11,22,33,44,55]
print(l[0]) # first value.
print(l[1]) # second value.
print(l[-1]) # last value.
print(l[-2]) # second last value.
print(l[-100]) # index out of range error.
```

List elements can be modified.

```python
l[0] = 12 # will replace the value at the 
         # index 0 to 12.
```

List elements can be used just like any other variable. 

```python
l[0]*12 # multiplies value at l[0] by 12.
```

## List Methods.

### append
The `append` function takes **one** argument and adds it to the end of the list. 

```python
>>> a = []
>>> a.append(1)
>>> a
[1]
>>> a.append("2")
>>> a
[1, '2']
# here '2' was added at the end of the existing list.
>>> a.append(1.11111)
>>> a
[1, '2', 1.11111]
>>> a.append([1,2,3])
>>> a
[1, '2', 1.11111, [1, 2, 3]]
# here, the entire list was inserted at the end of 
# the existing list.
```

### extend

```python
>>> a
[1, '2', 1.11111, [1, 2, 3]]
>>> b = [1,2,3]
>>> a.extend(b)
>>> a
[1, '2', 1.11111, [1, 2, 3], 1, 2, 3]
# All elements of the list b were added individually
# to the list a.
```	

### pop
pop deletes and returns one element. It takes one optional argument.

* No argument is passed: Deletes and returns the last element.

```python
>>> a
[1, '2', 1.11111, [1, 2, 3], 1, 2, 3]
>>> a.pop()
3
>>> a
[1, '2', 1.11111, [1, 2, 3], 1, 2]
```
* Valid index is passed: Deletes and returns the value at that index.

```python
>>> a
[1, '2', 1.11111, [1, 2, 3], 1]
>>> a.pop(0)
1
>>> a
['2', 1.11111, [1, 2, 3], 1]
```
### copy
`a.copy()` creates a new list with the values of list `a`.

```python
>>> a = [1, 2, 3, 4, 5, 6]
>>> b = a # a and b are pointing to same object.
>>> a[1]=-111 # when we change a, b also changes.
>>> a
[1, -111, 3, 4, 5, 6]
>>> b # b changed when a changed.
[1, -111, 3, 4, 5, 6]
>>> c = a.copy() # creates a new list object.
				 # having the values of list a.
>>> a
[1, -111, 3, 4, 5, 6]
>>> a[1]=999
>>> a
[1, 999, 3, 4, 5, 6]
>>> c # c didn't change when a changed.
[1, -111, 3, 4, 5, 6]
>>> b # b changed when a changed.
[1, 999, 3, 4, 5, 6]
```
#### Other functions
Learning a language requires self practice! If we explain each and every function, we will hinder your path of exploring the language, we encourage you to use the `help()` function to find out more about other functions which are allowed on Lists.

## Getting Help

We need to understand how to get help in Python.

* `help`: returns the documentation of the data type.
* `dir`: returns all the methods valid for that data type.

Example:

```python
help(1) # help about integer class.
help('') # help about strings.
help(1.1) # help about float.
help([]) # help about lists
```

### Output of `help`

```python
>>> help('')
Help on class str in module builtins:

class str(object)
	|  str(object='') -> str
	|  str(bytes_or_buffer[, encoding[, errors]]) -> str
	|
	|  Create a new string object from the given object. If encoding or
	|  errors is specified, then the object must expose a data buffer
	|  that will be decoded using the given encoding and error handler.
	|  Otherwise, returns the result of object.__str__() (if defined)
	|  or repr(object).
```

### Output of `dir`

```python
>>> dir('')
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__',
'__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', 
'__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', 
'__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 
'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 
'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 
'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
```

#### Slicing

Slicing is an easy way to fetch sub parts of them. Lists, strings and tuples allow Slicing.

The syntax of slicing is `l[start_index : end_index]`.

```
l: the list
start_index: Starting point with the element at this 
             index included; defaults to 0 if left blank.
end_index: Ending point, but this index is excluded;
           defaults to -1 if left blank.
```

Slicing returns a new object (list or string or tuple) from the `start_index` to the `end_index` without including `end_index`.

```python
>>> l = [0,1,2,3,4]
>>> l[0:3] # from 0 till 2nd element
	   # the element of index 3 is not returned
[0, 1, 2]
>>> l[1:3] # new list starting from 1 till 2nd element
	   # 3rd element is not returned
[1, 2]
>>> l[-1:] # new list containing the last element
[4]
>>> l[0:-1] # new list from 0 excluding last element
[0, 1, 2, 3]
>>> l[0:-2] 
[0, 1, 2]
>>> l[::-1] # returns a new list with values reversed
[4, 3, 2, 1, 0]
>>> for i in l:
...     print(i)
...
0
1
2
3
4
```

Slicing also works with strings and tuples. We invite you to try them out. Don't just read this book, execute code!

## Tuples

Read the [docs](https://docs.python.org/3/library/stdtypes.html#tuple) | Watch the [video]()

Tuples are read only lists. A tuple object, once created, doesn't allow us to add, delete or update an element. When we use the `dir` on a tuple object, we find that there are only two methods, `count` and `index`.

```python
>>> a = (1,2,3,4)
>>> type(a)
<class 'tuple'>
>>> 1 in a
True
>>> a[0]
1
>>> a[::-1]
(4,3,2,1)
>>> a[0:2]
(1,2)
```

### List vs Tuple
Lists are used when we are not sure how many values we'll be having.

Tuples are used when there is a fixed number of values to deal with.

## Set

Watch on [YouTube](https://www.youtube.com/watch?v=QmfDyjp0Z8E) | Read the [docs](https://docs.python.org/3/library/stdtypes.html#set-types-set-frozenset)

Sets are same as lists with the following limitations:

 1. Duplicate entries are not allowed
 1. Sets can only have basic data types as elements (lists/dictionary/set/tuple)
 1. Sets do not allow indexing

```python
>>> a = [1,2,3,4]
>>> b = set(a)
>>> b
{1, 2, 3, 4}
>>> type(b)
<class 'set'>
>>> b[0] # sets do not allow this.
TypeError: 'set' object does not support indexing
```

When we try to create a set from a list which has a list element, it is an error (only basic elements int, float, string are allowed) :

```python
a = [1,2,3,[2,3]]
set(a)
## Throws an error.
```
Sets allow various methods like add, copy, deepcopy, update, pop, remove.

```python
>>> a = set() # creates a blank set
>>> a.add("this")
>>> a.add("that")
>>> a.add("this and that")
>>> a
{'that', 'this and that', 'this'}
>>> a.remove("this")
>>> a
{'that', 'this and that'}
>>> a.pop()
'that'
>>> a
{'this and that'}
>>> a.add("zebra")
>>> a
{'zebra', 'this and that'}
>>> b = set([1,2,3,4,5])
>>> b
{1, 2, 3, 4, 5}
>>> b = set([1,2,3,4,5])
>>> c = b # c and b point to the **same** set object
>>> c
{1, 2, 3, 4, 5}
>>> b
{1, 2, 3, 4, 5}
>>> c.add(12) # changing c changes b
>>> b
{1, 2, 3, 4, 5, 12}
>>> c
{1, 2, 3, 4, 5, 12}
>>>
>>> d = b.copy() # creates a COPY of b
>>> d
{1, 2, 3, 4, 5, 12}
>>> b
{1, 2, 3, 4, 5, 12}
>>> b.add(1000) # changing b does NOT change d
>>> b
{1, 2, 3, 4, 5, 1000, 12}
>>> d
{1, 2, 3, 4, 5, 12}
```

## Dictionary

Read the [docs](https://docs.python.org/3/library/stdtypes.html#dict) | Watch on [YouTube](https://www.youtube.com/watch?v=pQV3wbSMBRI)

Dictionaries are key value pairs. Keys can only be hashable data types i.e. basic data types. There is no such restriction on the values.

Lists are indexed starting from 0, it is done by the interpreter itself. Dictionaries allow custom indexes i.e. keys.

> Note: the representation of both set and dictionary is by using curly braces, `{}`.

```python
>>> a = dict() # creates an empty dictionary
>>> a
{}
>>> a["IN"] = "India" # creates a new key value pair
>>> a
{'IN': 'India'}
>>> a["US"] = "United States of America" # new key value pair
>>> a
{'IN': 'India', 'US': 'United States of America'}
>>> a["ES"] = "Espanol"
>>> a
{'IN': 'India', 'US': 'United States of America', 'ES': 'Espanol'}
>>> a["IN"] # returns the value of "IN" key.
'India'
```

Dictionaries do not support slicing.

`keys()` and `values()` are two functions which return all the keys and values of the dictionary object. Since we can't use `for i in ` syntax to loop over dictionaries, we have to do this

```python
>>> a.keys()
dict_keys(['IN', 'US', 'ES'])
>>> a.values()
dict_values(['India', 'United States of America', 'Espanol'])
```

```python
>>> for i in a.keys():
...     print(i, ":", a[i])
...
IN : India
US : United States of America
ES : Espanol
```

We also encourage you to try out everything we did in this chapter, again! (on strings too)

Exercises:

1. Find the number of occurances of 1 in the list [1,2,1,2,1,2,3,4,1,2,3].
1. Find all the unique elements of a list. Input; a = [1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4]. Output; [1, 2, 3, 4].
1. Solve the above problem using a dictionary.
1. Find the count of each element of a list except "\n". a = [1, 2, 2, 3] should return this output. 1 : 1,, 2 : 2, 3 : 1.
1. Create a random dictionary and print key : value pair in ascending order of keys. Input: a = {"IN":"India", "ES":"Español"}, output: "ES"":"Español", "IN":"India". You have to use `dir` to find out the necessary functions.
1. The same example as above, print in descending order.
1. Given two list, find their
    1. common elements.
	1. elements present in list a but not in b.
	1. elements present in list b but not in a.
	hint: use sets.
1. Print a reverse of a list without using the `reverse` method.

##### Links

|[Next](05-constructs.md) | [Previous](03-02-operators.md) |  [Index](https://github.com/thewhitetulip/build-app-with-python-antitextbook/blob/master/SUMMARY.md)
| ----| ----| ----| 

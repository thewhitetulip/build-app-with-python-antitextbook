# High level data structures

In the last chapter we saw the various data types present in Python, in this chapter we'll look at the high level data types in detail.

## List

Watch on [YouTube](https://www.youtube.com/watch?v=30S9LnvanwY) | Read the [docs](https://docs.python.org/3/library/stdtypes.html#list)

An ordered collection of n values (n >= 0)

Creating a list is simple:

```python
l = [] # creates an empty list.
l = [1,2,3] # creates a list with integer values.
l = [1,2,3, 'sh', 'bm'] # creates a list with integer and string values. 
l = [1,2,3, [1,2,3]] # creates a list which contains a list as a member.
l = [ 1,1,1,1,1,1,1 ] # lists allow duplicates
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

Lists in Python can be negative.

| Value |  Negative Index |
| ----|  ----| 
|11|-5|
|22|-4|
|33|-3|
|44|-2|
|55|-1|

List elements can be accessed using indices. `l[0]` will return the first value of the list `l`. `0` is the index, if we try to access an index which doesn't exist, like `l[100]`, then it throws an error.

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

## Methods of the List datatype.

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
When we append sequences to a list, the entire sequence is inserted as one record at the end of the list.

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
pop deletes and returns one element. It takes one optional argument:

If no argument is passed: Deletes and returns the last element.

```python
>>> a
[1, '2', 1.11111, [1, 2, 3], 1, 2, 3]
>>> a.pop()
3
>>> a
[1, '2', 1.11111, [1, 2, 3], 1, 2]
```
If a valid index is passed: deletes and returns the value at that index.

```python
>>> a
[1, '2', 1.11111, [1, 2, 3], 1]
>>> a.pop(0)
1
>>> a
['2', 1.11111, [1, 2, 3], 1]
```

#### Other functions
Learning a language requires self practice! If we explain each and every function, we will hinder your path of exploring the language, we encourage you to use the `help()` function to find out more about other functions which are allowed on Lists.

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

Slicing works in the same was with strings and tuples as well, we invite you to try them out, we'd like to reiterate our stance here, we want you to program as much as you can while reading this book.

## Tuples

Read the [docs](https://docs.python.org/3/library/stdtypes.html#tuple) | Watch the [video]()

Tuples are read only lists. A tuple object, once created, doesn't allow us to add, delete or update an element. When we use the `dir` on a tuple object, we find that there are only two methods, `count` and `index`.

```python
>>> a = (1,2)
>>> type(a)
<class 'tuple'>
>>> 1 in a
True
>>> a[0]
1
>>> a[::-1]
(2,1)
```

### List vs Tuple
Lists are used when we are not sure how many values we'll be having, since lists support addition and deletion.

Tuples are used when there is a fixed number of values to deal with, since tuples don't support addition and deletion.

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

Lists are indexed starting from 0 onwards, it is done by the Interpreter itself. Dictionaries allow custom indexes i.e. keys.

```python
>>> a = {} # creates an empty dictionary
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

```python
>>> a.keys()
dict_keys(['IN', 'US', 'ES'])
>>> a.values()
dict_values(['India', 'United States of America', 'Espanol'])
```

`keys()` and `values()` are two functions which return all the keys and values of the dictionary object. Since we can't use `for i in ` syntax to loop over dictionaries, we have to do this

```python
>>> for i in a.keys():
...     print(i, ":", a[i])
...
IN : India
US : United States of America
ES : Espanol
```

We also encourage you to try out everything we did in this chapter, again! (on strings too)

##### Links

|[Next](05-constructs.md) | [Previous](03-02-operators.md) |  [Index](SUMMARY.md)
| ----| ----| ----| 

# High level data structures

In the last chapter we saw int, float, complex and strings. But that was just the basic introduction. Let's now take a look at the high level data structures in Python.

## List

Lists store multiple values in Python. Lists allow you to store values of any data type. Lists also allow duplicates

You can access elements of the list by using indices, 0,1,2,3. Indices always start with a 0 in Python. python also allows you negative indices, in that case, the values are returned in reverse order.


	l = [] # creates an empty list
	l = [1,2,3] # a list with values 1,2,3
	l = [1,2,3, 'sh', 'bm'] # a list contains 
	l = [1,2,3, [1,2,3]] # A list which contains a list as a member
	l = [ 1,1,1,1,1,1,1 ] # lists allow duplicates

	print(l[0]) # first value
	print(l[1]) # second value
	print(l[-1]) # last value
	print(l[-2]) # second last value

Lists are very powerful in Python, together with Sets and Dictionaries, they make Python a very powerful language.

Now, let's learn how to harness the help commands in Python.

Open up the interpreter.

If you see this, then you are in the interpreter

	Python 3.6.0 (default, Jan 13 2017, 22:22:15)
	[GCC 4.2.1 Compatible Apple LLVM 8.0.0 (clang-800.0.38)] on darwin
	Type "help", "copyright", "credits" or "license" for more information.
	>>>

## Getting Help

There are two ways to get help in Python, `help` or `dir`.

`help` is a function which takes an argument and returns the documentation of the data type.
`dir` is a function which takes an argument and returns all the methods valid for that data type.

Both help and dir don't care if you pass an empty object, for instance, if you want help for the string data type, pass '', if you pass 'hello', then also you get the same output, the reason for that is, whatever you pass to help and dir, the functions return **help for the class of that object**.

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

	
	>>> dir('')
	['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']

By making use of `dir` and `help`, we can get help in a better way in Python.

Now, try getting help and the list of functions out for the list data type, instead of `''`, pass `[]`. `[]` means an empty list.

Try typing this out in an interpreter, it is better to check this in the interpreter because that way, you'll understand things  in a better way and quickly.

If you looked into the interpreter, you'd have seen that there are various methods for lists

1. append

	>>> a = []
	>>> a.append(1)
	>>> a
	[1]
	>>> a.append("2")
	>>> a
	[1, '2']
	>>> a.append(1.11111)
	>>> a
	[1, '2', 1.11111]
	>>> a.append([1,2,3])
	>>> a
	[1, '2', 1.11111, [1, 2, 3]]
	
The `append` function takes **one** argument and adds it to the end of the list. If you want to merge two lists, then use `extend`

2. extend
	
	>>> a
	[1, '2', 1.11111, [1, 2, 3]]
	>>> b = [1,2,3]
	>>> a.extend(b)
	>>> a
	[1, '2', 1.11111, [1, 2, 3], 1, 2, 3]

here, the values of b were added individually at the end of the list `a`.

3. pop

	>>> a.pop()
	3
	>>> a.pop()
	2
	>>> a
	[1, '2', 1.11111, [1, 2, 3], 1]

pop deletes the last element by default, if you pass an index, it'll delete that element and return it's value.

	>>> a
	[1, '2', 1.11111, [1, 2, 3], 1]
	>>> a.pop(0)
	1
	>>> a
	['2', 1.11111, [1, 2, 3], 1]
	>>> a[1]
	1.11111


We are leaving the other functions as a homework. Learning a language requires self practice!

4. insert
5. copy
6. clear

#### Slicing

Lists and strings allow you to slice elements. It is an easy way to fetch sub parts of them. For instance, if you wanted just the first three elements from the list [1,2,3,4,5], this is the syntax in Python.

`# +ve indices     0,  1,  2, 3,  4`
`# -ve indices	 -5, -4, -3,-2, -1`

	>>> l = [1,2,3,4,5]
	>>> l
	[1, 2, 3, 4, 5]
	>>> l[0:3] # from 0 till 2nd element
	[1, 2, 3]
	>>> l[1:3] # new list starting from 1 till 2nd element
	[2, 3]
	>>> l[-1:] # last element
	[5]
	>>> l[0:-1] # new list from 0 excluding last element
	[1, 2, 3, 4]
	>>> l[0:-2] # new list starting from 0 till second last element
	[1, 2, 3]
	>>> l[::-1] # returns a new list with values reversed
	[5, 4, 3, 2, 1]
	>>> for i in l:
	...     print(i)
	...
	1
	2
	3
	4
	5

It is this simple to loop through a list or set. **On an interpreter, you have to hit enter twice before the expression is evaluated.**

Slicing for strings is the same, just try that out.

## Set

Sets are same as dictionaries with the following limitations

1. duplicate entries are not allowed.
2. sets are immutable, you can't append or delete elements to a set.
3. sets can't have lists/dictionary/set as an element. Basically, sets can only have basic data types as elements.

	>>> a = [1,2,3,4]
	>>> b = set(a)
	>>> a
	[1, 2, 3, 4]
	>>> b
	{1, 2, 3, 4}
	>>> type(b)
	<class 'set'>
	>>> type(a)
	<class 'list'>
	>>> a[1]
	2

Try creating a list which contains a list as an element and try creating a set out of it.
Use the `help` and `dir` to find out interesting information about sets and the methods that it allows us.	

## Dictionary

Dictionaries are key value pairs. When you use an array, they are indexed starting with 0. First element has index 0, second element has 1 and so on. But dictionaries are different, you choose the key and value BOTH, instead of just the value as in the case of the list.

Before we go any further, we recommend you to read the `help` and `dir` output of `{}`, this is an empty dictionary object. type `help({})`

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

Dictionaries do not support slicing.

	>>> a.keys()
	dict_keys(['IN', 'US', 'ES'])
	>>> a.values()
	dict_values(['India', 'United States of America', 'Espanol'])

`keys` and `values` are two functions which return all the keys and values of the dictionary object. Since we can't use `for i in ` syntax to loop over dictionaries, we have to do this

	>>> for i in a.keys():
	...     print(i, ":", a[i])
	...
	IN : India
	US : United States of America
	ES : Espanol

We encourage you to try which elements are not acceptable as keys inside dictionaries. Value fields can have anything, but there are restrictions on the keys.

We also encourage you to try out everything we did in this chapter, again! (on strings too)

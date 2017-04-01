# Understanding the program

## How to run Python code?

Watch on [YouTube](https://www.youtube.com/watch?v=wSqRUTS7uAg)

There are two modes of running Python code: Interactive and Batch.

#### Interactive mode
Code is typed inside an interpreter session which gets evaluated immediately. This mode is suitable for small edits. 

To start the interpreter, type `python3` or `python` on your machine, when the interpreter starts, it should look like this:

```
    Python 3.6.0 (default, Jan 13 2017, 22:22:15)
    Type "help", "copyright", "credits" or "license" for more information.
>>>
```

This shows that the default Python shell has started. `>>>` signifies the input location. 

```python
>>> print("hi")
hi
```

#### Batch Mode

Save the code in a file. if the file name is `file.py`, then we execute it like by typing `python3 file.py` in the command line **not** the interpeter.


#### Executing 3 vs 2
We are going to use `python3` to run the code, depending on your machine, you might need to use `python` instead of `python3` to execute code. 

Type `python --version` on your command prompt. 

    If it says Python 2, then you'll need to install python3 and execute code using `python3 file.py`.
    If it says Python 3, then you'll need to run all the code in this book as `python file.py`

## Installing packages

`pip` or `easy_install` is used for installing third party packages in Python. `pip` stands for Python installer package. The package that you are installing, needs to be hosted on the official packages repository.

 `pip install ipython` Installs the ipython package. This might work differently if you are on Windows, read the [docs](https://docs.python.org/3/installing/index.html) for more details.

## Comments

Watch on [YouTube](https://www.youtube.com/watch?v=oU1rHEnfgcM) | Read the [docs](https://docs.python.org/3/reference/lexical_analysis.html?highlight=comments#comments)

Comments in Python start with the # character. It can be present in any position of a line, the text **after** the # till the end of the line is the comment.

Comments are ignored by the interpreter. They are used for code readability & maintainability.

Non obvious code should have comments associated with it. 

Consider `a+=1`, there is no need to add a comment saying `increments the variable a by 1` because it is obvious. 

Now, consider `a = 4*c+4*d/6*c`. This is not obvious, thus, would warrant a comment. 

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


##### Links

|[Next](03-01-understanding-variables.md) | [Previous](01-intro-to-python.md) |  [Index](https://github.com/thewhitetulip/build-app-with-python-antitextbook/blob/master/SUMMARY.md)
| --------| --------| --------| 

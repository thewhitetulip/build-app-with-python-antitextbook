# Understanding the program

## Running code

Watch on [YouTube](https://www.youtube.com/watch?v=wSqRUTS7uAg)

There are two ways of running Python programs, 
1. Interpreter: In which you copy paste or type one line at a time and the code will be evaluate immediately
2. File: Save the code in one file and then execute the file.

#### Interactive mode

Typing `python3` or `python` on your machine will start the interpreter. You should see `Python 3.` on the next line, then you are good to go. If you don't, then you'll have to figure out how to run Python3.

This will start the Python interpreter. The `>>>` signifies the input location. We recommend using ipython instead of the default python interpreter as it is more powerful and feature rich.

#### Note: You'll have to hit the enter/return key twice only then does the interpreter evaluate a statement like the below statement.

```python
>>> if True:
...     print("hi")
...     print("another hi")
...
```

You need to hit the Enter or Return key **twice** to come out of the if block. You should see the `...` on the line and just hit enter again and the statement would be evaluated.
It is possible to type code directly into an interpreter session, but it carries its own risk considering that if the machine crashes, the code will be lost. The general practice is to use the Interpreter to run small blocks of code and then put it in our file.

##### Installing packages

`pip` or `easy_install` is used for installing third party packages in Python. `pip` stands for Python installer package. The package that you are installing, needs to be hosted on https://pypi.python.org and you can just call `pip install shbh` to install a package named shbh which is present on https://pypi.python.org. Read the [docs](https://docs.python.org/3/installing/index.html) for more details.

#### File Mode

File mode is another way of executing Python code. In this mode, you type all the code and save it in a text file. Later, we execute it as `python3 file.py`.

```python
import os
files = os.listdir()
for file in files:
	print(file)
```

After saving the code in `file.py`, you'll have to `cd` to that directory inside your terminal.

Assuming `$` is your terminal, just type

    $ python3 file.py

This will execute `file.py`. And, you'll see the list of all files and folders in the current working directory.

### Hybrid approach

The best approach is to use _both_, interactive mode and file mode. The interactive mode is to be used when you want to test a small block of code, later, you add it to the file. The reason it is a good practice is that we then split our code into easy to understand and test blocks rather than write one huge function with million if else blocks. In an era where computers also are capable of writing Python scripts, we need to be better than them!

## Comments

Watch on [YouTube](https://www.youtube.com/watch?v=oU1rHEnfgcM)

Read the [docs](https://docs.python.org/3/reference/lexical_analysis.html?highlight=comments#comments)

Comments are the lines which the interpreter will _ignore_, they are for those who will humans who maintain the project. If programming is a religion then Comments would be it's most powerful God capable of making or breaking lives. Every program which we write should be appropriately commented, it doesn't mean that we comment each and every line, only non obvious logic should have comments.

#### Single Line Comments

They start with a `#`. Can be present on any position in a line, any text written **after** the `#` till the end of the line is _ignored_ by the interpreter.
These are typically given to simple statements (and not functions/classes).

#### Docstring

Read the [docs](https://docs.python.org/3/library/doctest.html)

Python does not support multiple line comment, one can use triple quotes as docstrings. Either ''' or """. They need to be closed appropriately, otherwise they result in an error. Unlike comments, which are ignored, docstrings are evaluated, **not ignored**. These are typically given for functions, classes and modules (and not to statements).

From the official docs:

A string literal which appears as the first expression in a class, function or module. While ignored when the suite is executed, it is recognized by the compiler and put into the `__doc__` attribute of the enclosing class, function or module. Since it is available via introspection, it is the canonical place for documentation of the object.


```python
>>> def function():
...     """ this is a function which does something"""
...     print("hello world")
...
>>> function.__doc__
' this is a function which does something'
```

The location of the second ''' or """ doesn't matter, the only thing which matters is that **it should exist**. The value of a string is in between the triple quotes.

'this is a string', "this is a string", "'this is a string", '"this is a string', """ this is 'a string '""", '"""hi'

These all are *valid* strings, the reason being, they start with either single quote, double quote or triple quote, and they **end with the same quote**. It is legal to use double quote inside a single quote, or we can even have triple quotes inside single or double quotes. 

The only thing which matters is that when you start a string using quotes, you should **end** it using the **same** quote.

Doing this is a syntax error, '"sherlock", because it starts with a single quote but doesn't end with one.

## Indentation

Watch on [YouTube](https://www.youtube.com/watch?v=hhMDv0Q6Kps)

Python uses indentation as a part of the syntax. 

```python
if a > 1:
	print("In the scope of the IF block")
	print("In the scope of the IF block")
	print("In the scope of the IF block")
	print("In the scope of the IF block")
print("not in the scope of the IF block")
print("not in the scope of the IF block")
```

While evaluating the above if loop, this is how Python works.

##### Note:
This is not valid Python code, `[]` is used just to show the indentation.

```
if a > 1:
[   ]print("In the scope of the IF block")
[   ]print("In the scope of the IF block")
[   ]print("In the scope of the IF block")
[   ]print("In the scope of the IF block")
print("not in the scope of the IF block")
print("not in the scope of the IF block")
```

1. Does the statement require scoping (for, if, while, elif, else). Typically these statements have a colon at the end.
1. Calculate the number of spaces in the immediate second line. In this example, it is `four spaces`. The first `[]` block.
1. Every line below this line which has `four spaces` at the start until we get a line which **doesn't** have four spaces is in the if block.
1. Thus, the last two print statements are NOT in the if block since it doesn't have `four spaces`.

Having indentation **without** a if/for/while/elif block is a syntax error, for instance, you can't do the following:

```python
if a > 1:
	print("hi")
print("bye")
	print("hi")
```

The interpreter can't resolve which block the last print statement fits into.

We can have nested loops or structures like this

```python
if a > 1:
	if b < 1:
		print(" b is less than 1")
	print("a is greater than 1")
print("This is not in either of the above blocks")
```

#### Spaces vs tabs

Watch on [YouTube](https://www.youtube.com/watch?v=hhMDv0Q6Kps)

Indentation can be either done with spaces or tabs, there is no hard and fast rule, but if you choose one, please stick to it till the end, if you mix them, then it is a human error.

Standard is to use four spaces.

##### Note:
This is not valid Python code, `[]` is used just to show the indentation.

```
if a > 1:
[	]if b < 1:
[	][	]print(" b is less than 1")
[	]print("a is greater than 1")
print("This is not in either of the above blocks")
```

You can understand scoping better if you think in terms of blocks. In the above example, there are three lines with the first `[ ]` block. The third line contains two blocks of [ ], this means, it is a part of BOTH if blocks. Directly, it lies in the second if block, indirectly, it lies in the first if block.

When you have two layers of indentation, this is called nesting. You can have as many nesting blocks as you want, typically, it isn't recommended to go beyond four or five.

##### Links

|[Next](03-01-understanding-variables.md) | [Previous](01-intro-to-python.md) |  [Index](../SUMMARY.md)
| ----| ----| ----| 

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

> Note: When you type an if/for/while block in the interpreter, you need to hit the Enter or Return key **twice** for the block to be evaluated.

```python
>>> if True:
...     print("hi")
...     print("another hi") # hit enter twice here
...
```

#### Batch Mode

Code is written in a file from which it is executed.

Create a file named `file.py` and save the following lines in it.
```python
import os
files = os.listdir()
for file in files:
	print(file)
```

Open the terminal, change the directory to where you saved the above file and type the following to execute file.py.

Assuming `$` is your terminal.

    $ python3 file.py


###### Executing 3 vs 2
We are going to use `python3` to run the code. Type `python --version`, if this says 2, then you'll need to install python3 and execute code using python3.
If `python --version` gives you 3, then you'll need to run all the code in this book as `python file.py`

#### Hybrid approach
It is a better practice to use both interpreter and batch mode while writing Python scripts, that way, we can incrementally test small blocks and later add them to our file.

## Installing packages

`pip` or `easy_install` is used for installing third party packages in Python. `pip` stands for Python installer package. The package that you are installing, needs to be hosted on the official packages repository and you can just call `pip install ipython` to install a package named ipython. Read the [docs](https://docs.python.org/3/installing/index.html) for more details.

## Comments

Watch on [YouTube](https://www.youtube.com/watch?v=oU1rHEnfgcM) | Read the [docs](https://docs.python.org/3/reference/lexical_analysis.html?highlight=comments#comments)

Comments are the lines which the interpreter will _ignore_. The significance of comments lies purely for code readability. It makes  maintaining the project easier. If programming is a religion then Comment would be it's most powerful God capable of making or breaking lives. 

Each block of non obvious code should have appropriate comments associated with it. Consider `a+=1`, there is no need to add a comment saying `increments the variable a by 1` because it is ovious. 

Now, consider `a = 4*c+4*d/6*c`. This is not obvious, it might be Sarick's coefficient, and thus would warrant a comment. 

#### Single Line Comments

They start with a #. It can be present in any position of a line, the text **after** the # till the end of the line is _ignored_ by the interpreter.

Single line comments are used for statements other than functions/classes.

#### Docstring Comments

Read the [docs](https://docs.python.org/3/library/doctest.html)

Python does not support multiple line comments. Triple quotes can be used as 'docstrings', for documentation purposes of functions and classes. 

Triple quotes can either be made up of three single quote or three double quotes. They need to be closed appropriately, otherwise they result in an error. Unlike comments, which are ignored, docstrings are evaluated, **not ignored**.

Below is an example:

```python
>>> def function():
...     """ this is a function which does something"""
...     print("hello world")
...
>>> function.__doc__
' this is a function which does something'
```
> From the official docs:
A string literal which appears as the first expression in a class, function or module. While ignored when the suite is executed, it is recognized by the compiler and put into the `__doc__` attribute of the enclosing class, function or module. Since it is available via introspection, it is the canonical place for documentation of the object.

##### String validity

The location of the ending triple quote doesn't matter, the only thing which matters is that **it should exist**. The value of a documentation string is in between the starting and ending triple quotes.

Take the following strings as an example, `'this is a string', "this is a string", "'this is a string", '"this is a string', """ this is 'a string '""", '"""hi'`

These all are *valid* strings, they start and end with the same quote. If a string starts and ends with a single quote, then any number of double quotes can be part of the string, the same is true vice versa. 

But, when the string starts with a single quote, but has no ending single quote (or has more than one single quote), it is a syntax error. `'"sherlock"` is an invalid string, so is `"sherlock''`, because both of these strings do not start and end with the same quote.

## Indentation

Watch on [YouTube](https://www.youtube.com/watch?v=hhMDv0Q6Kps)

Python uses indentation as a part of the syntax. Either spaces or tabs can be used for indentation, typically, four spaces are used. It does not matter if we use tabs or spaces as long as we do not mix them. If we mix tabs and spaces then it causes an error.

Below is a simple if block:

```python
if a > 1:
	print("In the scope of the IF block")
	print("In the scope of the IF block")
	print("In the scope of the IF block")
	print("In the scope of the IF block")
print("not in the scope of the IF block")
print("not in the scope of the IF block")
```

#### Scoping

When we use indentation, we need to understand the scope of each block which we use. Each statement belongs to one or more "scopes", one direct scope and multiple indirect scopes. 

Plain if-else statement.

```python
if True:
    # statements here are in the 
    # scope of the if statement.
    print("Statement is true")
else:
    # statements here are in the 
    # scope of the else statement.
    print("Statement is false")
```
For visualization, let's draw `[]` around the spaces, so the code now looks like this:

> Note: This is not valid Python code, `[]` is used just to show the indentation.

```
if a > 1:
[   ]print("In the scope of the IF block")
[   ]print("In the scope of the IF block")
[   ]print("In the scope of the IF block")
[   ]print("In the scope of the IF block")
print("not in the scope of the IF block")
print("not in the scope of the IF block")
```
All lines except the last two are in the scope of the `if` block.

#### How to find scope?
1. After a construct which ends with a colon (if/for/while/try/except), calculate the number of spaces in the immediate next line. In this example, it is `four spaces`. The first `[]` block.
1. Every line below this line which has `four spaces` at the start until we get a line which **doesn't** have four spaces is in the if block.

> Note: Having indentation **without** an if/for/while/elif block is a syntax error, for instance, you can't do the following:

```python
if a > 1:
	print("hi")
print("bye")
	print("hi")
```

The syntax error is because the interpreter isn't able to find out what block the statement belongs to.

#### Nesting

We can have multiple if blocks inside an if block (same is true with for/while statements). This is called nesting. When we write nested if statements, then the same logic applies to indentation.

This is an example of two level nesting:

```python
if a > 1:
	if b < 1:
		print(" b is less than 1")
	print("a is greater than 1")
print("This is not in either of the above blocks")
```
Let's add `[]` to the code to understand scoping for nested blocks. 

Each `[ ]` can be considered as an indentation block, we can see that `if b < 1` has only one block, but this statement, `print(" b is less than 1")` has two blocks of spaces, the first one is to `if b < 1` which is the primary scope, the secondary scope is to `if a > 1`.

> Note: This is not valid Python code, `[]` is used just to show the indentation.

```
if a > 1:
[	]if b < 1:
[	][	]print(" b is less than 1")
[	]print("a is greater than 1")
print("This is not in either of the above blocks")
```
### Scoping for nested blocks

Here, the statements which lie in the inner if statement lie in two blocks, the inner if statement's block and the outer if statement's block.

```python
if True:
    # statements here are in the 
    # scope of the if statement.
    print("Statement is true")
    if True:
        # statements here are in the inner if
	# but overall, lie in the scope of 
	# the outer if. 
        print("Another statement")
else:
    # statements here are in the 
    # scope of the else statement.
    print("Statement is false")
    if True:
        # statements here are in the inner if
	# but overall, lie in the scope of 
	# the outer else.
        print("Another statement")
```

##### Links

|[Next](03-01-understanding-variables.md) | [Previous](01-intro-to-python.md) |  [Index](SUMMARY.md)
| --------| --------| --------| 

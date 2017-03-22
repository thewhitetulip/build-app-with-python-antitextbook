# Understanding the program

## How to run Python scripts?

Watch on [YouTube](https://www.youtube.com/watch?v=wSqRUTS7uAg)

There are two ways of running Python programs, 

1. Interactive mode: Type code which will be evaluate immediately, but you can't save it to a file.
2. Batch Mode: Save the code in one file and then execute the file.

#### Interactive mode
In the Interactive mode, you type python code inside an interpreter session which is evaluated immediately, it is suitable for short edits. To start the Python interpreter, type `python3` or `python` in the terminal. You should see something like this.

```bash
    Python 3.6.0 (default, Jan 13 2017, 22:22:15)
    Type "help", "copyright", "credits" or "license" for more information.
>>>
```
This shows that the default Python shell has started. The `>>>` signifies the input location. 

> Note: As you can seen below, you need to hit the Enter or Return key **twice** to come out of the if block. You should see the `...` on the line and just hit enter again and the statement would be evaluated.

```python
>>> if True:
...     print("hi")
...     print("another hi")
...
```
#### Batch Mode

In this mode, you type all the code and save it in a text file. Later, we execute it as `python3 file.py`.

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

#### Executing 3 vs 2
We are going to use `python3` to run the code. Type `python --version`, if this says 2, then you'll need to install python3 and execute code using python3.
If `python --version` gives you 3, then you'll need to run all the code in this book as `python file.py`

#### Hybrid approach
Typically, you'd want to use both the interactive mode and the batch mode. When you'll write small blocks of code, you would want to run it first in the interpreter and then add it to your file. It is a matter of taste.

##### Installing packages

`pip` or `easy_install` is used for installing third party packages in Python. `pip` stands for Python installer package. The package that you are installing, needs to be hosted on https://pypi.python.org and you can just call `pip install shbh` to install a package named shbh. Read the [docs](https://docs.python.org/3/installing/index.html) for more details.

## Comments

Watch on [YouTube](https://www.youtube.com/watch?v=oU1rHEnfgcM)

Read the [docs](https://docs.python.org/3/reference/lexical_analysis.html?highlight=comments#comments)

Comments are the lines which the interpreter will _ignore_. The significance of comments lies purely for code readability. It makes  maintaining the project an easier task. If programming is a religion then Comment would be it's most powerful God capable of making or breaking lives. 

Programs should have appropriate comments, typically, non obvious code should have a comment associated with it. 

Consider this line of code, `a+=1`, there is no need to add a comment saying `increments the variable a by 1` because it is ovious. 

Now, consider this line of code, `a = 4*c+4*d/6*c`. This is not obvious, it might be Sarick's coefficient, and thus would warrant a comment. There is no such thing as Sarick's coefficient.

#### Single Line Comments

They start with a `#`. Can be present on any position in a line, any text written **after** the `#` till the end of the line is _ignored_ by the interpreter.

These are typically given to statements and not to functions/classes.

#### Docstring Comments

Read the [docs](https://docs.python.org/3/library/doctest.html)

Python does not support multiple line comments. Triple quotes can be used as 'docstrings', for documentation purposes of functions and classes. 

Triple quotes can either be made up of ''' or """. They need to be closed appropriately, otherwise they result in an error. Unlike comments, which are ignored, docstrings are evaluated, **not ignored**. These are typically given for functions, classes and modules (and not to statements).

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

The location of the ending ''' or """ doesn't matter, the only thing which matters is that **it should exist**. The value of a documentation string is in between the starting and ending triple quotes.

Take the following strings as an example, `'this is a string', "this is a string", "'this is a string", '"this is a string', """ this is 'a string '""", '"""hi'`

These all are *valid* strings, they start and end with the same quote. If a string starts and ends with a single quote, then a double quote can be part of the string, the same is true vice versa. 

But, when the string starts with a single quote, but has no ending single quote, it is a syntax error. `'"sherlock"` is an invalid string, so is `"sherlock''`, because both of these strings do not start and end with the same quote.

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

Each `[ ]` can be considered as a block, we can see that `if b < 1` has only one block, but this statement, `print(" b is less than 1")` has two blocks of spaces, the first one is to `if b < 1` which is the primary scope, the secondary scope is to `if a > 1`.

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

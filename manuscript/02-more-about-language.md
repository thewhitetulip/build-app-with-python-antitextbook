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


#### Executing 3 vs 2
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

#### Syntax

They start with a #. It can be present in any position of a line, the text **after** the # till the end of the line is _ignored_ by the interpreter. They are used for statements other than functions/classes.

## Indentation

Watch on [YouTube](https://www.youtube.com/watch?v=hhMDv0Q6Kps)

Python uses indentation as a part of the syntax. Either spaces or tabs can be used for indentation, typically, four spaces are used. It does not matter if we use tabs or spaces as long as we do not mix them. If we mix tabs and spaces then it causes an error.

##### Links

|[Next](03-01-understanding-variables.md) | [Previous](01-intro-to-python.md) |  [Index](SUMMARY.md)
| --------| --------| --------| 

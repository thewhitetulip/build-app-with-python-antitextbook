# Understanding the program

We left the last chapter by listing all files in the current working directory. It was intentional to not get into details in the last chapter itself since it was supposed to be a gentle introduction to the language.

## Running code

Watch on [YouTube](https://www.youtube.com/watch?v=wSqRUTS7uAg)

There are two ways of running Python programs, either use the interpreter and copy paste or type one line at a time. the interpreter will evaluate each line as you type/paste it, OR, save all the code in one file and then execute the file.

#### Interactive mode

Type `python3` or `python` on your machine and if you see `Python 3.` on the next line, then you are good to go, otherwise, you'll have to figure out how to run Python3.

This will start the Python interpreter, which is basically an infinite loop which will run each statement you will throw at it. The `>>>` signifies the input location.

#### Note: Hit the enter/return key twice.

When you are working on the interpreter like below:

```python
>>> if True:
...     print("hi")
...     print("another hi")
...
```

You need to hit the Enter or Return key **twice** to come out of the if block. You should see the `...` on the line and just hit enter again and the statement would be evaluated.

You can easily run any large python program using just the interpreter without saving any code in any file, but that approach is too extreme because if your machine crashes, you'll be parting ways with all the hard work you've done, also, the default interpreter isn't really advanced. For that reason, we use `ipython`. `pip3 install ipython` or `pip install python`. 

### Installing packages

`pip` or `easy_install` is used for installing third party packages in Python. `pip` stands for Python installer package. The packages needs to be hosted on https://pypi.python.org and you can just call `pip install shbh` to install a package named shbh which is present on https://pypi.python.org

#### Using files

The other way, is to save everything to a file. Type the following code inside a text file and save it as `file.py`.

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

The best approach is to use _both_, interactive mode and file mode. The interactive mode is to be used when you want to test a small block of code, later, you add it to the file. The reason it is a good practice is that we then split our code into easy to understand and test blocks rather than write one huge function with million if else blocks. In an era where computers also are capable to write Python scripts, we need to be better than them!

## Comments

Watch on [YouTube](https://www.youtube.com/watch?v=oU1rHEnfgcM)
Comments are the lines in a python program which the interpreter will _ignore_. There are two types of comments:

1. Single line comments:
	They start with a `#`. Can be present on any position in a line, any text written **after** a `#` till the end of the line is _ignored_ by the interpreter.

2. Multi line comments:
	Using # is great if you want to have a single line comment, but what if you want to write a comment which is spread across two or more lines? You use a multi line comment. Multi line comments are three quotes (single or double). ''' or """. They need to be closed appropriately, otherwise they result in an error.

```python
""" 
This is 

a multi line

comment"""

'''
	
	this is another
	
	multi line comment

'''
```

The location of the second ''' or """ doesn't matter, the only thing which matters is that **it should exist**. The interpreter while evaluating strings inside python will consider the value of a string **between** single quotes or double quotes.

'this is a string', "this is a string", "'this is a string", '"this is a string', """ this is 'a string '""", '"""hi'

These all are *valid* strings, the reason being, they start with either single quote, double quote or triple quote, and they **end with the same quote**. It is legal to use double quote inside a single quote, or we can even have triple quotes inside single or double quotes. 

The only thing which matters is that when you start a string using quotes, you should **end** it using the **same** quote.

Doing this is a syntax error, '"sherlock", because it starts with a single quote but doesn't end with one.

## Indentation

Watch on [YouTube](https://www.youtube.com/watch?v=hhMDv0Q6Kps)
Python uses indentation as a part of the syntax. C/Java use braces `{`. In those languages, indentation is just a good practice that programmers are encouraged to follow. In python, indentation is the necessity, you can't write programs if you don't indent them properly.

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

*This block isn't syntax highlighted intentionally.*

```python
if a > 1:
[   ]print("In the scope of the IF block")
[   ]print("In the scope of the IF block")
[   ]print("In the scope of the IF block")
[   ]print("In the scope of the IF block")
print("not in the scope of the IF block")
print("not in the scope of the IF block")
```

1. Does the statement equire scoping (for, if, while, elif, else). Typically these statements have a colon at the end.
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

This statement results in a syntax error, because the interpreter can't resolve which block the last print statement fits under. The first print statement is in the IF block, the second statement is NOT in the if block and the third statement is an orphan, hence it is a syntax error.

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

	if a > 1:
	[	]if b < 1:
	[	][	]print(" b is less than 1")
	[	]print("a is greater than 1")
	print("This is not in either of the above blocks")

You can understand scoping better if you think in terms of blocks. In the above example, there are three lines with the first `[ ]` block. The third line contains two blocks of [ ], this means, it is a part of BOTH if blocks. Directly, it lies in the second if block, indirectly, it lies in the first if block.

When you have two layers of indentation, this is called nesting. You can have as many nesting blocks as you want, typically, it isn't recommended to go beyond four or five.


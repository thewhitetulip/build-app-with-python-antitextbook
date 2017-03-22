# Introduction

[Watch on YouTube](https://www.youtube.com/watch?v=7wuKDDMb3R4)

Python is an [open source](https://github.com/python/cpython), cross platform, interpreted language. As it is cross platform, a program written on any platform is guaranteed to run across any platform. There are many third party packages available on http://pypi.python.org. Python comes with a program called `pip`, through which you can install a package from https://pypi.python.org

Python can be used for doing virtually anything, YouTube, Quora, Hulu are just a few platforms written in Python. We can write command line applications, Linux's bootloader is written in Python, we can write webapps, we can control robots, we can write Machine Learning algorithms. There are many things which can be achieved by using Python.

There are few things which make Python an awesome language:

1. English like syntax
This makes for an excellent prototyping language, if you want to build a quick proof of concept, it'd be faster to write it in Python even though you'd throw everything later and implement it in Java or C. 

2. Less number of lines
Any program implemented in Python has significantly less number of lines as compared to other languages.

3. High level data structures
High level data structures like hashmaps, sets, lists make it really easy to write complex programs.

There is one drawback though, because it is a dynamically typed language, it is somewhat difficult to debug the programs written in Python. Thus the need to be extra careful while writing & designing them.


## Python 2 vs Python3

Python3 is the successor of Python2. In 2020 Python2 will be history. This tutorial is based on Python3 as it is the present and future of the language. Python3 is a backwards incompatible with Python2. There is a way of writing code which runs both on Python 2 and 3, but it is beyond the scope of this guide.


## Installation
1. Windows
Download the latest .exe file of Python3 from https://python.org and click on Next Next.
2. Android
Install Termux (https://termux.com/help.html), and then `apt-get install python3`..
3. Linux(sudo apt-get install python3 / sudo yum install python3 / use other package manager)
4. Mac (brew install python3).

You are not expected to understand everything in one go, but keep reading, till we reach the end of the book, you'll start writing Python code.

## Your first Python Script
Problem statement: List all text files in the current working directory.

Python doesn't use semi colons or braces for control flow (if/for/while), it uses **indentation**. It is mandatory to use indentation if you are using a `for`, `while`, `if` loop.

Create a folder for the code of this book, name it something. Save the following lines in a file ending with the `.py` extension.

```python
import os
files = os.listdir()
for file in files:
    if file.endswith(".txt"):
        print(file)

```

Create 2-3 .txt files, `touch file{1,2,3,4,5}.txt` will create file1.txt, file2.txt till file5.txt, but it works only on Linux or Mac.

After saving the above file and creating the dummy text files, we have to run the python script to see if we got the desired outcome.

Python scripts are executed by running `python3 file.py`, where file.py is the name of our script. 

###### Note:
If you get an error saying that python3 wasn't found, then type `python --version`, if it is 3 or above then just type `python file.py`. In machines where both Python2 and Python3 are installed, typing `python` refers to python2, in those cases, we have to specifically mention python3. However, when your machine has just python3 installed, then python will refer to Python3 and there is no need to type `python3 file.py` as it would turn into an error, in those cases, we run the code as `python file.py`.

If everything went well, you should see this as the output:

```
file1.txt
file2.txt
file3.txt
file4.txt
file5.txt
```
## Working of the script

```python
import os # imports a package which allows us to interact with the OS. It has lots of functions which we can use.
files = os.listdir() # Gets all the names of the files in the current working directory.
for file in files: # Loops through all the names of the files
    if file.endswith(".txt"): # If the file name ends with .txt
        print(file) # prints the file name
```

In UNIX, we have the `ls` utility, in five lines of code, we mocked a small subset of the ls utility, this is the power of Python.

#### Note:

It would be controversial to point a newbie to the documentation, but we strongly believe that if there is one thing that a newcomer should focus on, then it is the documentation, if we are well versed with the documentation, then we can be a great programmer, Googling only gets us so far. When we point you to the docs, you are not expected to remember everything, docs are there as a reference manual and not as a textbook, at any point of time, if you face an issue related to a library, then it'd be better to read the docs before searching over the Internet.

## Using glob
[glob](https://docs.python.org/3/library/glob.html) is part of the standard library and allows you to have advanced functions which save you from the usage of `os.listdir`.

#### Note: 
A block of code which starts with '>>>' means we are using the Interpreter, we'd recommend you to use `ipython`, it is a slightly advanced interpreter and you'd have to install it on your machine, use your package manager. `pip install ipython3`, `pip3 install ipython3`. pip = python2, pip3 = python3.

```python
>>> import glob
>>> files = glob.glob('*.txt')
>>> print(files)
['file1.txt', 'file2.txt', 'file3.txt', 'file4.txt', 'file5.txt']
```

The `glob` method does a regular expression match on the current directory. If you want to explore how to use regular expressions, check out [re](https://docs.python.org/3/library/re.html), part of the standard library.

As you advance your knowledge in Python, you'll feel the need to use as many stdlib functions as you can so as to reduce code duplication.

Exercise:

1. Write a program to print all `*.csv` files, create multiple `.csv` files first, without using glob.

##### Links

|[Next](02-more-about-language.md) | [Previous](README.md) |  [Index](SUMMARY.md)
| ---- | ---- | ---- |

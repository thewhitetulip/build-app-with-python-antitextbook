# Introduction

[Watch on YouTube](https://www.youtube.com/watch?v=7wuKDDMb3R4)

Python is an [open source](https://github.com/python/cpython), cross platform, interpreted language. Cross platform means that a program written on any platform is guaranteed to run across any platform which Python supports. It is a powerful language because there are many third party packages available. The official repository of those packages is http://pypi.python.org. Python comes with a tool called `pip` which allows downloading libraries from the official repository.

Python is widely used across major domains. YouTube, Quora, Hulu, Dropbox are just a few platforms written in Python. We can write command line applications Linux bootloader, Robots, Machine Learning algorithms, automate test cases, do system administration etc using Python, among other things.

There are few things which make Python an awesome language:

1. English like syntax: It takes very little time to learn the language and write code. This makes it an excellent prototyping language. Typically, Python is used to write prototypes which are later totally replaced with systems written in a compiled language.

2. Less number of lines: Any program implemented in Python has significantly less number of lines as compared to other languages.

3. High level data structures: High level data structures like hashmaps, sets, lists make it really easy to write complex programs.

Drawbacks:

1. Speed: Since it is an interpreted language, it is slower than most languages. 
2. Debugging: Being a dynamically typed language, it is somewhat difficult to debug the programs.

## Python 2 vs Python3

Python3 is the successor of Python2. In 2020 Python2 will be history. This tutorial is based on Python3 as it is the present and future of the language. Python3 is a backwards incompatible with Python2, which means, code written for Python2 is not guaranteed to run on Python3. There is a way of writing code which runs both on Python 2 and 3, but it is beyond the scope of this guide.


## Installation
1. Windows: Download the latest .exe file of Python3 from https://python.org and click on Next Next.
2. Android: Install Termux (https://termux.com/help.html), and then `apt-get install python3`..
3. Linux: sudo apt-get install python3 / sudo yum install python3 / use other package manager
4. Mac: brew install python3.
1. iOS: python 3 for ios (not free).


## Your first Python Script

This section will introduce you to your first Python script. Since this is the first script, you are not expected to understand everything in one go. Just keep reading and try to understand as much as you can, eventually, you will understand everything.

**Problem statement:** 

List all text files in the current working directory.

**Code:**

```python
import os
files = os.listdir()
for file in files:
    if file.endswith(".txt"):
        print(file)

```

> Note: Create a folder for the code of this book, name it something. Type/copy paste the above lines exactly as it is in a file ending with the `.py` extension.


Python doesn't use semi colons or braces for control flow (if/for/while), it uses **indentation**. It is mandatory to use indentation if you are using a `for`, `while`, `if` loop.


Create 2-3 ".txt" files, `touch file{1,2,3,4,5}.txt` will create file1.txt, file2.txt till file5.txt on Linux or Mac.

Now, in the terminal, execute the script. Python scripts are executed by running `python3 file.py`, where file.py is the name of our script. 

> Note: If you get an error saying that python3 wasn't found, then, you might not have Python3 installed. Check the output of `python --version` on the terminal, if you see that it is 3, then run all the code in this book as `python file.py`, because your default python version is 3.

**Output:**

```
file1.txt
file2.txt
file3.txt
file4.txt
file5.txt
```

**Explanation:**

```python
import os # imports a package which allows us to interact with the OS. 
          # it has lot of functions which we can use.
files = os.listdir() # Gets all the names of the files in the current working directory.
for file in files: # Loops through all the names of the files
    if file.endswith(".txt"): # If the file name ends with .txt
        print(file) # prints the file name
```

For our first program, we implemented the basic functionality of the `ls` utility. This is how powerful Python is.

> Note: It would be against the general opinion to link the documentation in a newcomers book, but we strongly believe that you can't possibly be an expert in Python unless you learn how to read the documentation. While looking for help, please look at the documentation first, Internet, later. Searching the Internet for "how to open a file in Python" will never make you a good programmer.

## Using glob
[glob](https://docs.python.org/3/library/glob.html) is part of the standard library and allows you to have advanced functions which save you from the usage of `os.listdir`.

> Note: Code starting with '>>>' means we are using the Interpreter. To start the interpreter in the terminal type python3 or python (depending on the version you are using).


```python
>>> import glob
>>> files = glob.glob('*.txt')
>>> print(files)
['file1.txt', 'file2.txt', 'file3.txt', 'file4.txt', 'file5.txt']
```

The `glob` method does a regular expression match on the current directory to return all the matching file names.

Exercise:

1. Write a program to print all `*.csv` files, create multiple `.csv` files first, without using glob.

##### Links

|[Next](02-more-about-language.md) | [Previous](README.md) |  [Index](SUMMARY.md)
| ---- | ---- | ---- |

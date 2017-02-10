# Introduction

[Watch on YouTube](https://www.youtube.com/watch?v=7wuKDDMb3R4)

Python is an open source, cross platform, interpreted language. Since it is open source, you can distribute the language in any commercial software, since it is cross platform, you can write programs on Mac and they'll run exactly the same way on any other platform which Python supports. 

Python has been around for more than 30 years and that is the reason there are many third party packages available, it is advisable to check out http://pypi.python.org before you start writing your package, because the changes are that someone already has written a package for that. There are millions of Python programmers out there, and python can be used for doing virtually anything, YouTube, Quora, Hulu are just a few platforms written in Python. We can write command line applications, linux's bootloader is written in Python, we can write webapps, front end apps and just about everything that you want to build.

Python is dynamic typed language, which means that you don't have to define the data type of an object. It is a fully object oriented language. Because of it's English like syntax, Python makes for an excellent prototyping language, any program implemented in Python has significantly less number of lines as compared to Java, but because it is a dynamically typed language, it is somewhat difficult to debug the programs written in Python or we need to be extra careful while writing them. The reason for that is if you have a 100 line program and you define `i=1` at the first line and by mistake you do `i = '1'` somewhere in between the lines, then it won't complain that `i is an integer you can't assign string to it`, it'll just run the rest of the code assuming the new value of i.

Along with this, what makes Python powerful is the presence of high level data structures like hashmaps, sets, lists.

## Python 2 vs Python3

Python3 is the successor of Python2. In 2020 Python2 will be history. This tutorial is based on Python3 as it is the present and future of the language. The reason why they created python3 was that there were some shortcomings to the python language which weren't addressed for almost 30yrs and now, the authors decided that they should address them, while addressing them, it occurred to them that they have to create backwards incompatible changes to the language and thus python3 was created. If you write programs in Python3, there is no guarantee that it'll work in Python2, same is true vice versa, if you want your programs to work in both Python2 and Python3, then you have to write them specifically to run in both versions. It is beyond the scope of this tutorial, but you will find  lots of resources on the Internet which teach you how to write programs compatible with both versions.

## Installation

If you are on Windows, please go to https://python.org and download the latest .exe file of Python3. For Android, please download TermUX (https://termux.com/help.html). If you are on Mac (brew install python3), if you are on Linux, depending on your distro (apt-get install python3 or yum install python3)


Enough theory.

Let's write programs now. Make sure you have Python installed.

## Example: List all `*.txt` files
We are going to print the list of all files which end with '.txt'.

#### Note:

Python doesn't use semi colons or braces for control flow of the programs, it uses **indentation**. It is mandatory to use indentation if you are using a `for`, `while`, `if` loop.

```python
import os
files = os.listdir()
for file in files:
    if file.endswith(".txt"):
        print(file)
```

Save this in `file.py`. Create 2-3 .txt files. `touch file{1,2,3,4,5}.txt` will create file1.txt, file2.txt till file5.txt, but it works only on Linux or Mac.

After saving `file.py`, execute the program by typing `python3 file.py`

###### Note:
If you get an error saying that python3 wasn't found, then type `python --version`, if it is 3 or above then just type `python file.py`. Because in that case, you have Python3 installed and calling python will call python3.

If everything went well, you should see this as the output:

```
file1.txt
file2.txt
file3.txt
file4.txt
file5.txt
```

This is the beauty of the language, its syntax is very easy to understand and that's the reason the language is very powerful.

If you want to list all the .txt files, you can use the unix utility `ls`, `ls *.txt`. We saw here, how to implement one feature of the `ls` utility in less than 5 lines. This is the power of Python.

Exercise:

1. Write a program to print all `*.csv` files, create multiple `.csv` files first.
1. Install ipython using easy_install or pip. Be careful about the version of pip you use.

# Understanding the program

## How to run Python code?

Watch on [YouTube](https://www.youtube.com/watch?v=wSqRUTS7uAg)

There are two modes of running Python code: Interactive and Batch.

#### Interactive mode
Code is typed inside an interpreter session which gets evaluated immediately. This mode is suitable for small edits. 

To start the interpreter, type `python3` or `python` on your terminal or command prompt.

#### python3 vs python
You have to figure out what to use while invoking the interpreter (python3 or python) based on the following:

Type `python --version` on your command prompt. 

    If it says Python 2, then you'll need to install python3 and execute code using `python3 file.py`.
    If it says Python 3, then you'll need to run all the code in this book as `python file.py`


The Interpreter looks like this when it starts:

```
    Python 3.6.0 (default, Jan 13 2017, 22:22:15)
    Type "help", "copyright", "credits" or "license" for more information.
>>>
```

If you see `>>>`, this means that the interpreter has started and is waiting for your input. Type `print("Hello Python!")`.

```python
>>> print("Hello Python!")
Hello Python!
```

The interpreter evaluates each line which you type. The `print` function is used to print content on the terminal. This is why you saw "Hello Python!" printed immediately on the next line.

### Using the Interpreter

Start a new interpreter session and type this.

```python
>>> 1 + 1
2
```

`1 + 1` is called an expression. 

`+` will calculate the sum of two numbers (1 and 1) and return the result.

```python
>>> 1 - 1
0
```

`-` will calculate the subtraction of 1 and 1 and return the result. 

```python
>>> 10 * 10
100
```

`*` multiplies 10 with 10 and return the result.

```python
>>> 10 ** 2
100
```

`**` is called the power operator, it returns 10 to the power of 2.

### Operator Types

In the above expressions, `+`, `-`, `*` are called operators, they operate on numbers (which are called operands).

In general, there are three types of operators:

1. Unary operators: Require one operand to operate on. 
1. Binary operators: Require two operands to operate on. Most of the operators are binary (`-, +, *, **` etc)
1. Ternary operators: Require three operators to operate on. 

We won't be looking at unary and ternary operators now, we need to understand the language before jumping to ternary operators.

#### Batch Mode
The interpreter makes it difficult to write big programs. The best you can do in an interpreter is type lines of code. But, when you want to write programs and build applications, it is better to use the batch mode. In this, you create a text file who's name ends with `.py` like `file.py` and save it to your machine on some folder. We then run the file as `python3 file.py`.

To execute the program, you'd need to use the `cd` program to change folders.

For this book, create a folder. Open the terminal and type this.

Mac/Linux (Applications -> Terminal)

1. `mkdir ~/antitextbookpy`
You will save all the code files in this folder. You have to do this only once.

2. `cd ~/antitextbookpy`
This will change the current working directory to `~/antitextbookpy`, you have to do this every time you open a new terminal window or tab.

Windows: (open the Command Prompt)

1. `mkdir antitextbookpy`
1. `cd antitextbookpy`

You would need to create a file in this folder, save it by giving it a `.py` extension then run it like `python file.py` from the command line. If it says file not found, then you might have to check if you followed the above steps (of changing directories).

##### Links

|[Next](03-01-understanding-variables.md) | [Previous](01-intro-to-python.md) |  [Index](https://github.com/thewhitetulip/build-app-with-python-antitextbook/blob/master/SUMMARY.md)
| --------| --------| --------| 

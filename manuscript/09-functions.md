# Functions

Functions are used to save code duplication. When we want a block of code duplicated across multiple locations, rather than physically copy pasting the code, it is better to declare a function and use it wherever we require it.By doing this, we write easy to edit code, because when our logic changes, we have to make changes only to the function definition and not everywhere the block is present.

###### file: func.py

The following is the typical function definition on Python, def is the keyword. 'function\_name' is the name to be given to the function.

Functions support zero or more arguments.

```python
def function_name(argument1, argument2):
    <statements>
```

Let's write a simple program to print the square of a number passed to it as an argument.

### Invoking functions.

```python
def square(number1):
    print(number1**2)
```

Save the file and run it. 

You will notice that the program didn't give any output, and that is because we just defined a function. When the interpreter comes across the def block, it will create a function of that name, taking some arguments and performing some action. 

It will not execute the function, if we want the function to be used, we need to invoke it.

Add `square(2)` to the end of the above file. Save and run the program again. This time, you'll see the output. This is called function invocation.

Here, 2 is an argument which is stored in number1 during the function invocation. Just because an argument is defined doesn't mean that we have to use it, we can ignore it altogether if we want.

### Default arguments

Now that we wrote the square function, we want to generalize it to calculate power. This function will take two arguments, number and the power, and return number \*\* exponential.

###### file: defaultargs.py

```python
def power(number, exp=2):
    print(number ** exp)

power(2, 3) # value of exp is 3.
power(2) # since no value of exp
	 # is given, defaults to 2.
```

Some or all arguments in Python can be optional. When an argument is optional, the default value of the argument is used.

The rule with default arguments is that they need to be at the right most side of the argument listing, after all the mandatory arguments.

The following block of code will result in a SyntaxError.
```python
def do(var1=2,var2):
    print("hi")

do(1)
```

## Return
In the above examples, we saw function which prints the output. A function can also return the its output to the caller. This is helpful when processing data which we do not want to print.

There is no restriction on the number of values that can be returned. Values are returned using the return statement and it is not a part of the function signature, a return statement should be directly added in the function definition.

```python
def add(name, mode):
    return name+mode, name-mode

one, two = add('this', 'that')
print(one, two)
```

Here, we have a function which returns two values. The two values are then printed after the function call.

##### Links

|[Next](10-task.md) | [Previous](08-exception.md) |  [Index](SUMMARY.md)
| ----| ----| ----| 

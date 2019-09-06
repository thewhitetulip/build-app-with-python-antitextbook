# Exception handling

When something goes wrong, Python throws an an exception object. `Exception` is a class from which other exceptions are derived. The name of the child classes usually end with Error like FileNotFoundError.

Read the [docs](https://docs.python.org/3/tutorial/errors.html#errors-and-exceptions)

#### file: exception.py
```python
i = 0
j = 100/i
print("This is the print statement")
```

This code won't run, it would throw the ZeroDivisionError exception.

The problem with exceptions is that your program is killed the moment it throws an exception. When writing large scale software in Python, this becomes an issue. This is where exception handling comes into picture. We want our programs to be resilient about errors that might happen during the runtime and we do not want our code to exit for any such reasons.

#### file: exception2.py

```python
i = 0
try:
    j = 100/i
except:
    print("Can't divide by 0!!")
```

When you run this program, you'll see that it doesn't kill the program.

A try catch block is to be used for lines which we suspect that something might go wrong, for instance if you are trying to open a file, there are many things which could go wrong, for instance, the disk space would go full, the file might not exist or a million other things, thus, we wrap the `open` function call in a try catch block.

The `try` block contains all the lines where we suspect that something might go wrong, the `except` block is where the damage control lines are present. What we do for handling exceptions is upto us, we can just print on the terminal or we can send emails to the respective teams, or just log that there was an exception.

```python
i = 0
try:
    j = 100/i
except ZeroDivisionError as e:
    print(e)
except Exception as e:
    print(e)
finally:
    print("this block always gets executed")
```

The try-catch block allows you to handle multiple exceptions, they must be in the reverse order of generality. For instance, if you want to handle every kind of exception, just use ` except Exception`, the smallest exception statement should be at the top.

#### Finally

The finally block gets executed every time a try block gets executed. You can put the statements in this block which you want to be executed every time.

You'd be doing this when you do handle errors for file handling programs.

```python
try:
	f = open("lines.txt", "r")
except Exception as e:
	print(e)
```

Of course, you can pick up something other than the Exception class. If you want to handle some specific scenario like FileNotFoundError, use it instead of the Exception as e class. When you use `Exception as e`, you get the exception thrown by the code into an object `e`, you can print the object or write it to a file. If you don't care for that, just use `except Exception:`, skip the `as e`.

##### Links

|[Next](09-functions.md) | [Previous](07-examples.md) |  [Index](../SUMMARY.md)
| ----| ----| ----| 

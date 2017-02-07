# Exception handling

Python throws an `exception` if something goes wrong. `Exception` is a class from which other exceptions are derived. The child classes of Exception usually end with Error like FileNotFoundError.

#### file: exception.py

	i = 0
	j = 100/i
	print("This is the print statement")

Run this file [`python3 exception.py`] , it'll stop execution at the second line, as it will throw `ZeroDivisionError: division by zero`. The problem with exceptions is that your program is killed the moment it throws an exception. Clearly, this is not a good sign. We have the `try-catch` block to handle these exceptions.

#### file: exception2.py

	i = 0
	try:
	    j = 100/i
	except:
	    print("Can't divide by 0!!")
	print("This is the print statement")



When you run this program, you'll see that it doesn't kill the program, it also executes the last print statement, which was not the case when we had not used the try catch block.

Exception handling is done so that our program doesn't quit execution, we want our code to be robust. Think for a moment that you are building some web service that someone uses, if by some mishap, the code doesn't have read access on some folder, it will exit from the execution and your service would be unreachable.

Rather than your service being unreachable, you handle the exceptions so that you are good to go. When you handle the exceptions, your service will **not** exit at such code point, it will continue execution while executing the `except` block.

A try catch block is to be used for lines which we suspect that something might go wrong, for instance if you are trying to open a file, there are many things which could go wrong, for instance, the disk space would go full, the file might not exist or a million other things, thus, we wrap the `open` function call in a try catch block.

	
	i = 0
	try:
	    j = 100/i
	except ZeroDivisionError as e:
	    print(e)
	except Exception as e:
	    print(e)
	finally:
	    print("this block always gets executed")
	print("This is the print statement")

the try-catch block allows you to handle multiple exceptions, they must be in the reverse order of generality. For instance, if you want to handle every kind of exception, just use ` except Exception`, the smallest exception statement should be at the top.

#### Finally

The finally block gets executed every time a try block gets executed. You can put the statements in this block which you want to be executed every time.

You'd be doing this when you do handle errors for file handling programs.

	try:
	    f = open("lines.txt", "r")
	except Exception as e:
	    print(e)

Of course, you can pick up something other than the Exception class. If you want to handle some specific scenario like FileNotFoundError, use it instead of the Exception as e class. When you use `Exception as e`, you get the exception thrown by the code into an object `e`, you can print the object or write it to a file. If you don't care for that, just use `except Exception:`, skip the `as e`.

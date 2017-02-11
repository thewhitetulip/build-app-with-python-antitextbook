# Using modules

In the last chapter, we left off by creating three functions for our core functionality. In this chapter, we'd split the functions into two packages, 

1. the main package
1. the todo package (which we'll create)

The `todo` package is going to contain everything related to our todo manager and the main package is just going to be the executable program.

The first thing we do, is create a `main.py` file, and cut paste our main function inside it and remove the invocation at the bottom of the `tasks.py` file.

So now our code is split into two files, in Python3 a file can be imported as a package directly, it should just be present in the same directory.

    import tasks as t

By doing this, we can access all the members of the `tasks.py` file by appending 't.', like `t.list_task()`.

Replace the three functions according to this rule. If we had not given the alias t to the library, as is the keyword used to give alias, then we'd have to write `tasks.list_task()`, but since we are lazy, we prefer to give it an alias to call it like `t.list_task()`.

Modules are one of the most important aspects of Python. When we import a module, the interpreter **executes** the file which points to module.py (if we import a module named module). 

This is the way any module is imported:

1. The interpreter first goes to the stdlib folder and tries to find the .py file
1. If found, it executes it
1. If not found, it looks in the current directory
1. If found, it executes it
1. If not found, it complains as ModuleNotFoundError: No module named ""

Special care needs to be taken so that we give the same name as a stdlib package, the humans reading the code would surely get confused, even if Python won't!

As an example, try creating a file `sys.py` in the current folder. Add one line to that file, `print("something")`. Add an import statement `import sys` and later run `python3 tasks.py`, you'll see that it doesn't print "something", it refers to the stdlib package called 'sys'.

## Make Code Great Again!

There are many ways that we can make our code great again (ahem), there are lots of features we can add, a partial list can be as below:

1. add a "task status" field
1. change the formatting to show a checkbox like 
    [ ] Do this and that (for incomplete)
    [x] Do this and that (for complete) 
1. ability to search
1. ability to set deadline
1. log the time of operations
1. show graphs based on task completion.

But since this is not a perfect world, we'd not be doing all that, in this tutorial we hoped to teach you the way to develop an app, so you can build everything any feature you want, make sure that you ping me if you upload it to Github!

Now, we will make a few changes to our tasks library. We do not want the open() call three times, so we will wrap it in an function of our own, that'll save us multiple open calls.

```python
def open_file(name, mode):
    try:
        file = open(name, mode)
    except IOError as e:
        print(str(e))
        sys.exit(1)
    return file
```

This will be our function which wraps the file open statement for now.

Why would we need such a thing? Why would we bother to wrap the open in an abstract function? The reason behind this is that by doing so, we have migrated the entire try-catch block inside one function. Now, if we were to change something there, we just have to change one block. Hence, the UNIX philosophy, one program does one thing well.

### The case of the `__name__`

Since packages are executed as just another python program when they are imported, there is this case that we need to handle.

At the end of tasks.py, add a print statement.

    print("this is some print statement")

Save the file and run the main file.

    ch12 $ python3 main.py
    this is some print statement
    Invalid arguments!

You can see that the print statement got executed, as we said, a module when imported is executed like just another python program. The solution to this problem is to add an if block.

    if __name__ == "__main__":
        print("this is some print statement")

    ch12 $ python3 main.py
    Invalid arguments!

Now we can see that the output is the way we want it. The `__name__` is the variable which stores the way the file was executed, if we run it like `python3 file.py` then `__name__` stores the value '__main__', otherwise, it stores how it was invoked, in this case, it was invoked as "import tasks", thus `__name__` stores the value tasks.

This example of course was basic, but when we write test cases for the functions of that module, they need to be inside this if block, so that we don't accidentally run the entire suite of test cases whenever we import the package.

To check the value of `__name__`, add 

        
    print(__name__)

    if __name__ == "__main__":
        print("this is some print statement")

At the bottom of `tasks.py` NOT in the if block, if you add it to the if block then it won't be executed unless the file was executed.

##### Links

|[Next](13-examples.md) | [Previous](11-function-tasks.md) |  [Index](SUMMARY.md)
| ----| ----| ----| 
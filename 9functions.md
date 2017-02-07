# Functions

Functions are used to save us from code duplication. At times, we require to implement the same functionality in multiple locations. At such times, it is better to create a function and use it elsewhere rather than code duplication.

We encourage you to execute the code from this point on in a file.

###### file: func.py


def doSomething(var1,var2):
     print("This function does something")

doSomething(1,2)

The first line defines a function, and the last line invokes it. Now, comment the last line and run the code again.

The output would be blank, because you just defined a function but you didn't invoke it. This is very important concept in Python (or rather any other scripting language), if you use functions, you have to make sure that you call at least one of them, typically, the name of such function is `main`, but it can be anything. There is no special significance to the naming of a function.

Functions support arguments, you can have as many of them as you want, they are evaluated from left to right. You have a choice of using them, you can use them, it is all right if you don't use them at all.

### Default arguments

###### file: defaultargs.py

def doSomething(var1, var2="sh"):
    print("does something")
    print(var2)

doSomething(1,"hi")
doSomething(1)

When we use default arguments, we are providing a default value for an argument, so that when we invoke the function, it isn't a mandatory variable.

When we see the two invokations of doSomething, the first one sends 1 and "hi", var1 is going to be 1 and var2 is going to be "hi".

But the second invokation is missing the value for var2. Since we have already given the value for var2 in the function definition, the value of var2 would be "sh".

One important point that we have to note is that default arguments need to be at the end. We need to have them after mandatory arguments.

def do(var1=2,var2):
    print("hi")

do(1)

If you run this file, you'll get a `SyntaxError: non-default argument follows default argument`. The default argument should be the last argument in the list.

## Recursion

A function calling itself is recursion, recursion is great for theoretical exercise, but it leads the code to be a little obscure, when we write code, we should write robust code which is readable and maintainable.
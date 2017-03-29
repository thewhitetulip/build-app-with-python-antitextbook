# Constructs

### del

`del` can be used to delete any variable, it de-allocates a variable. After you run `del a`, the variable `a` was deleted, so we can't access it.

```python
>>> a
['2', 1.11111, [1, 2, 3], 1, 2, 3]
>>> del a
>>> a 
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    a
NameError: name 'a' is not defined
```


### if-else statment

Read the [docs](https://docs.python.org/3/reference/compound_stmts.html#the-if-statement) | Watch [video 1](https://youtu.be/fbCsCFuj6zE)| Watch [video 2](https://youtu.be/YjUo6TQ2EzE)

if-else statement is for conditional branching. 

```python
if <condition>:
    # statements here are in the 
    # scope of the if statement.
    print("condition is true")
else:
    # statements here are in the 
    # scope of the else statement.
    print("condition is false")
```

###### Evaluation

`condition` is an expression which evaluates to True or False. 

When the condition of the `if` block evaluates to False, it will go to the `elif` blocks until it finds a condition which evaluates to True, when no condition evaluates to True, then the else block is executed.

Try running this block:

```python
if True:
   print("The if block.")

if False:
   print("The if block.")
else:
   print("The else block.")

if True:
   print("The if block.")
else:
   print("The else block.")
```
**Output:**

```
The if block.
The else block.
The if block.
```

**Explanation:**

The statements in the `if` block get executed if the condition evaluates to `True`.

The statements in the `else` block get executed when the `if condition` evaluates to `False`.

#### elif

The `elif` block is special, it gets evaluated if the parent `if` block has been evaluated to False.

```Python
a = 10
if a > 100:
    print("A is greater than 100")
elif a < 100:
    print("A is less than 100")
else:
    print("A is equal to 100")
```

**Output:**
```
A is less than 100
```

**Explanation:**

Is a greater than 100? -> A is greater than 100.

Is a less than 100 (and not greater than 100)  -> A is less than 100.

Both of above conditions are False? -> A is equal to 100.

## Indentation and scoping

The above examples were simple if-else statements, when we start writing complex programs, scoping comes into picture.

```python
if a > 1:
	print("In the scope of the IF block")
	print("In the scope of the IF block")
	print("In the scope of the IF block")
	print("In the scope of the IF block")
print("not in the scope of the IF block")
print("not in the scope of the IF block")
```

#### Scoping

When we use indentation, we need to understand the scope of each block which we use. Each statement belongs to one or more "scopes", one direct scope and multiple indirect scopes. 

For visualization, let's draw `[]` around the spaces, so the code now looks like this:

> Note: This is not valid Python code, `[]` is used just to show the indentation.

```
if a > 1:
[   ]print("In the scope of the IF block")
[   ]print("In the scope of the IF block")
[   ]print("In the scope of the IF block")
[   ]print("In the scope of the IF block")
print("not in the scope of the IF block")
print("not in the scope of the IF block")
```
All lines except the last two are in the scope of the `if` block.

#### How to find scope?
1. After a construct which ends with a colon (if/for/while/try/except), calculate the number of spaces in the immediate next line. In this example, it is `four spaces`. The first `[]` block.
1. Every line below this line which has `four spaces` at the start until we get a line which **doesn't** have four spaces is in the if block.

> Note: Having indentation **without** an if/for/while/elif block is a syntax error, for instance, you can't do the following:

```python
if a > 1:
	print("hi")
print("bye")
	print("hi")
```

The syntax error is because the interpreter isn't able to find out what block the statement belongs to.

#### Nesting

We can have multiple if blocks inside an if block (same is true with for/while statements). This is called nesting. When we write nested if statements, then the same logic applies to indentation.

This is an example of two level nesting:

```python
if a > 1:
	if b < 1:
		print(" b is less than 1")
	print("a is greater than 1")
print("This is not in either of the above blocks")
```
Let's add `[]` to the code to understand scoping for nested blocks. 

Each `[ ]` can be considered as an indentation block, we can see that `if b < 1` has only one block, but this statement, `print(" b is less than 1")` has two blocks of spaces, the first one is to `if b < 1` which is the primary scope, the secondary scope is to `if a > 1`.

> Note: This is not valid Python code, `[]` is used just to show the indentation.

```
if a > 1:
[	]if b < 1:
[	][	]print(" b is less than 1")
[	]print("a is greater than 1")
print("This is not in either of the above blocks")
```
### Scoping for nested blocks

Here, the statements which lie in the inner if statement lie in two blocks, the inner if statement's block and the outer if statement's block.

```python
if True:
    # statements here are in the 
    # scope of the if statement.
    print("Statement is true")
    if True:
        # statements here are in the inner if
	# but overall, lie in the scope of 
	# the outer if. 
        print("Another statement")
else:
    # statements here are in the 
    # scope of the else statement.
    print("Statement is false")
    if True:
        # statements here are in the inner if
	# but overall, lie in the scope of 
	# the outer else.
        print("Another statement")
```
### for loop.

Read the [docs](https://docs.python.org/3/reference/compound_stmts.html#the-for-statement)

`for` statement is used to cycle over a list/set/tuple. 

```python
l = [1,2,3,4,5]
for i in l:
    print(i)
```
**Output:**
```
1
2
3
4
5
```

**Explanation:**

The program goes through five iterations

Iteration 1: Value of i is 1; loop prints 1;

Iteration 2: Value of i is 2; loop prints 2;

Iteration 3: Value of i is 3; loop prints 3;

Iteration 4: Value of i is 4; loop prints 4;

Iteration 5: Value of i is 5; loop prints 5;

In a `for` loop, we can perform other operations too, for the sake of simplicity, we just printed the value of the variable i.

#### Another approach.

```
for i in range(len(l)):
    print(l[i])
```
**Output:**
```
1
2
3
4
5
```

**Explanation:**
`range` returns a list [0,1,2,3,4].

The execution of this program is exactly the same as above, we have five iterations and we are printing the values of a list based on the by fetching elements of the list by index.

#### The Else Block

`for` has an else block. It is strange at first glance, but it is quite helpful in certain cases, like finding if a number if prime or not.


```python
for i in [1,2,3]:
    print(i)
else:
    print("out of for loop")
```

**Output:**
```
1
2
3
out of for loop
```

**Explanation:**
This is same as the else block of the `if` statement. The above program executes in three iterations

1'st iteration: value of i is 1

2'nd iteration: value of i is 2

3'rd iteration: value of i is 3

4'th iteration: goes to the else block since all values have been consumed.


### while loop.

Read the [docs](https://docs.python.org/3/reference/compound_stmts.html#the-while-statement)

`while` is used when you have to loop for a specific condition. If you don't have a condition, you can use `True` and that would result in an infinite loop.

```python
i = 100
while i >= 0:
    print(i)
    i = i - 1
```

**Output:**
```
100
```

**Explanation:**
`while` is a looping statement like `for`, it is going through iterations, just the difference lies in the condition. The `while` statement will loop on the condition, until the condition evaluates to `False`. The loop exits when the condition becomes False.

###### Syntax

```python
while condition:
	<code>
```

> Note: The `while` statement also has an else block, we encourage you to play with it to understand it better.

#### break, continue, pass

#### break

Read the [docs](https://docs.python.org/3/reference/simple_stmts.html#break)

The break statement kills the current loop. If we have nested loops, then we have to position the `break` properly to kill the correct loop.

```python
for i in range(100):
    if i == 4:
        break
    print(i)
```

The above block will print all the numbers until it hits 4. The moment it hits 4, the for loop will stop executing.

#### continue

Read the [docs](https://docs.python.org/3/reference/simple_stmts.html#continue)

The continue statement takes the execution to the next iteration.

```python
for i in range(100):
    if i == 4:
       continue
    print(i)
```

The above block will print all numbers **except** 4. It continues to the next iteration.

#### pass
Pass can be used as an empty placeholder in places where you don't have anything to add.

```python
if a > 1:
    pass
else:
    print("TODO")
```

For instance, in the above if-else block, you really don't know what logic you are going to put, so you can either use `print("TODO")`, or use the pass statement. pass doesn't print anything. You can use pass in any loop.

#### try - except - finally
Read the [docs](https://docs.python.org/3/reference/compound_stmts.html#the-try-statement)

try-except is used for exception handling, we'll take a look at it in a later chapter. 

#### with 
Read the [docs](https://docs.python.org/3/reference/compound_stmts.html#the-with-statement)

The with block was added in [PEP 343](https://www.python.org/dev/peps/pep-0343/). support of the [Resource Acquisition Is Initialization](http://en.wikipedia.org/wiki/Resource_Acquisition_Is_Initialization) idiom commonly used in C++. It is intended to allow safe acquisition and release of operating system resources.

Resources are created within a scope/block, resources are cleanly released whether the block exists normally or because of an exception.

```python
with open('file.py') as ip, open('op.txt','w') as op:
    for line in ip.readlines():
    op.write(line)
```
**Output:**
```
10
1
21
19
30
20
```

Because of scoping, the `input_file` and `output_file` variables are only available within the with clause. This can result in some clean code, but it is upto you totally. I like to use try-except-finally.

We encourage you to read more about the `range` function. Please **do not use the Internet**, use the `help` function. The faster you get familiar to using the documentation, the better programmer you become. In a world full of people Googling "how to create a string in Python", we really need to be self sufficient as to using the documentation that a language provides to differentiate from others. The mark of a great programmer isn't in how much things she can store in her memory, it is in the mastery of the tools she uses, documentation and the help command are among the tools.

##### Links

|[Next](06-file-handling.md) | [Previous](04-list-set-dict.md) |  [Index](SUMMARY.md)
| ----| ----| ----| 

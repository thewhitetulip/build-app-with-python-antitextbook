# Constructs

> Note: If you don't remember the indentation rule, you might want to go back and read the previous chapter.

### if-else statment

Read the [docs](https://docs.python.org/3/reference/compound_stmts.html#the-if-statement) |Watch [video 1](https://youtu.be/fbCsCFuj6zE)| Watch [video 2](https://youtu.be/YjUo6TQ2EzE)

if-else statement is for conditional branching. The syntax of the if statement is:

```python
if condition:
	<code>
elif condition:
	<code>
else:
	<code>
```

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
The output is:

```
The if block.
The else block.
The if block.
```

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
Output:
```
A is less than 100
```
Explanation:
Is a greater than 100? -> A is greater than 100.
Is a less than 100 (and not greater than 100)  -> A is less than 100.
Both of above conditions are False? -> A is equal to 100.

## for loop.

Read the [docs](https://docs.python.org/3/reference/compound_stmts.html#the-for-statement)

`for` statement is used to cycle over a list/set/tuple. 

```python
l = [1,2,3,4,5]
for i in l:
    print(i)
```
Output:
```
1
2
3
4
5
```

Explanation:
The above for loop will print each item in the list `l`. During the loop's execution, each value of the list is stored in the variable `i`, on which we can perform operations. Here, we are just printing the variable `i`, but we can do a host of other things.

An another way to print all the values of a list is this:

```
for i in range(len(l)):
    print(l[i])
```
Output:
1
2
3
4
5

Explanation:
`range` returns a list of numbers starting from 0 to the length of the list. In this case, it returns [0,1,2,3,4], we then print the respective index of the list.

#### The Else Block

`for` has an else block. It is strange at first glance, but it is quite helpful in certain cases, like finding if a number if prime or not.


```python
for i in [1,2,3]:
    print(i)
else:
    print("out of for loop")
```

Output:
```
1
2
3
out of for loop
```

The `else` block of the `for` statement is same as the else block of the `if` statement. The first block of statements are executed when the counter is iterating on the variable used after `in`. The moment it finishes iteration the `else` block is executed.

## while loop.

Read the [docs](https://docs.python.org/3/reference/compound_stmts.html#the-while-statement)

while is used when you have to loop for a specific condition. If you don't have a condition, you can use `True` and that would result in an infinite loop.

```python
>>> i = 100
>>> while i >=0:
...     print(i)
...     i = i - 1
...
100
```

If you want to print all numbers from 100 till 0, you'd use the above code. Of course, you can use `for` with `range(100,0)`, but for the sake of a while loop, we used one.


This is the syntax of a while loop

```python
while condition:
	<code>
```

The `while` statement also has an else block, we encourage you to play with it to understand it better.

The condition should evaluate to a Boolean True, the moment it hits False, we get out of the loop.

There are more constructs which we will look at later.

#### break, continue, pass

Run the below code in the interpreter, first see the output of the code, try to visualize how it works and then read the description.

1. break

Read the [docs](https://docs.python.org/3/reference/simple_stmts.html#break)

When you use the break statement, you kill the current loop.

```python
for i in range(100):
	if i == 4:
		break
	print(i)
```

The above block will print all the numbers until it hits 4. The moment it hits 4, it'll kill the for loop.

2. continue

Read the [docs](https://docs.python.org/3/reference/simple_stmts.html#continue)

When you use the continue statement, you move to the next iteration

```python
for i in range(100):
	if i == 4:
		continue
	print(i)
```

The above block will print all numbers **except** 4. It continues to the next iteration.

3. pass
Pass can be used as an empty placeholder in places where you don't have anything to add.

```python
if a > 1:
	pass
else:
	print("TODO")
```

For instance, in the above if-else block, you really don't know what logic you are going to put, so you can either use `print("TODO")`, or use the pass statement. pass doesn't print anything. You can use pass in any loop.

4. try - except - finally
Read the [docs](https://docs.python.org/3/reference/compound_stmts.html#the-try-statement)

try-except is used for exception handling, we'll take a look at it in a later chapter. The logic behind this is that sometimes there might be exceptional scenarios which can make our program crash, we use try-except block to handle them.

5. with 
Read the [docs](https://docs.python.org/3/reference/compound_stmts.html#the-with-statement)

The with block was added in [PEP 343](https://www.python.org/dev/peps/pep-0343/). support of the [Resource Acquisition Is Initialization](http://en.wikipedia.org/wiki/Resource_Acquisition_Is_Initialization) idiom commonly used in C++. It is intended to allow safe acquisition and release of operating system resources.

Resources are created within a scope/block, resources are cleanly released whether the block exists normally or because of an exception.

```python
>>> with open('file.py') as ip, open('op.txt','w') as op:
...     for line in ip.readlines():
...         op.write(line)
...
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

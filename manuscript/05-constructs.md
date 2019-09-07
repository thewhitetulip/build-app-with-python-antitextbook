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

### Exercise:

1. Given that a = [1,2,3,4,[5,6,7]]
    1. Delete the first value.
    2. Delete the second value of the list present at index 4.
    1. Delete the variable a.
    1. Take an input value from the user and delete it (if it is present), print "value not present" if the value is not present in the list.
1. Given that a = {"IN":"India", "ES":"Espanol"}
    1. Delete the key "IN".
    1. Delete the key "ES"
    1. Delete the variable a.


### if-else statment

Read the [docs](https://docs.python.org/3/reference/compound_stmts.html#the-if-statement) | Watch [video 1](https://youtu.be/fbCsCFuj6zE)| Watch [video 2](https://youtu.be/YjUo6TQ2EzE)

Let's say we work for a school and we are asked to write a program to print out if a student has passed or failed for a particular exam. `a` is the score that the student scored in a subject, `b` is the maximum marks for the subject. Passing percentage is 35.

```python
a = 67
b = 100
percent = (a/b)*100 # calculating percentage marks.

if percent < 35:
    # block executes if percent is less than 35.
    print("Failed.")
else:
    # block executes if percent is greater than 35.
    print("Passed! Keep it up!")
```
**Output:**

```
Passed! Keep it up!
```

## Indentation

Python uses spaces for indentation. Either spaces or tabs can be used for indentation, but not both. Usage of four spaces is recommended.

```python
a = 67
b = 100
percent = (a/b)*100 # calculating percentage marks.

if percent < 35:
    # block belongs to the if statement.
    print("Failed.")
    print("Please appear for exams again.")
else:
    # block belongs to the else statement.
    print("Passed!")
    print("Study for the next exams now.")
print("END")
```

#### Scoping

Each statement belongs to one or more "scopes", one direct scope and multiple indirect scopes. 

For visualization, let's draw `[]` around the spaces, so the code now looks like this:

> Note: This is not valid Python code, `[]` is used just to show the indentation.

```
if percent < 35: # global scope
[    ]print("Failed.")
[    ]print("Please appear for exams again.")
else:
[    ]print("Passed!")
[    ]print("Study for the next exams now.")
print("END") # global scope
```

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

The error is because the interpreter isn't able to find out what block the statement belongs to.

#### elif

The `elif` block is special, it gets evaluated if the parent `if` block has been evaluated to False. 

In our school, we now want to print the grades of students.

    F: percentage < 35
    C: 35 < percentage <= 50
    B: 50 < percentage <= 70
    A: 70 < percentage <= 90
    A+ 90 < percentage 

> Note: `elif` and `else` can't exist without a corresponding `if` block. Only the `if` block can exist independently.

```python
a = 67
b = 100
percent = (a/b)*100 # calculating percentage marks.

if percent < 35:
    # block belongs to the if statement.
    print("F")
elif percent <= 50:
    print("C")
elif percent <= 70:
    print("B")
elif percent <= 90:
    print("A")
else:
    print("A+")
```

**Output:**
```
B
```

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

## Exercise
1. Take the name, age and score of the user as input. Print their percentage. If the percentage is less than 60, print F, if percentage is between 60 and 70 print B and if percentage is greater than 70 print A. Marks are out of 100.
1. Take a number from the user and print if it is even or odd.
1. Take two numbers from the user and print which number is largest.
1. Take two numbers from the user and print which number is smallest.
1. Take three numbers from the user and print largest and smallest number.
1. Take four numbers from the user and create a list.
1. Take four numbers from the user and create a set.

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
`range(5)` returns a list [0,1,2,3,4].

#### The Else Block

`for` has an else block. It is strange at first glance, but it is quite helpful in certain cases, like finding if a number if prime or not.

We will take a simple example where we want to find out if an element is present in a list or not.

```python
l = [1,2,3,4,5]
val = 99

for i in l:
    if i == val:
        # for understanding break
        # check the below section.
        break
else:
    print("Not present")
```

**Output:**
```
Not present
```

**Explanation:**
The loop is killed by using a `break`, if the loop does not get killed, then the value is not present in the list.

### Exercise:

1. Print all numbers till 100.
1. Print all numbers from 20 to 100.
1. Print all even numbers less than 100.
1. Print all odd numbers less than 100.

#### break, continue, pass

#### break

Read the [docs](https://docs.python.org/3/reference/simple_stmts.html#break)

The break statement kills the current loop. If we have nested loops, then we have to position the `break` properly to kill the correct loop.

```python
for i in range(10):
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

> Note: break and continue work with loops only, either `for` or `while`.

## Exercise:
1. Print all numbers from 0 till 10 except 4 and 5.
1. Print all numbers from 0 till 20 except those divisible by 3.
1. a = [1,2,3,4,5], take an integer as input from the user. Print all numbers which are less than the input number using break.

#### pass
Pass can be used as an empty placeholder in places where you don't have anything to add.

```python
if a > 1:
    pass
else:
    print("TODO")
```

For instance, in the above if-else block, you really don't know what logic you are going to put, so you can either use `print("TODO")`, or use the pass statement. pass doesn't print anything. You can use pass in any loop.


### while loop.

Read the [docs](https://docs.python.org/3/reference/compound_stmts.html#the-while-statement)

`while` is used when you have to loop for a specific condition. If you don't have a condition, you can use `True` and that would result in an infinite loop.

```python
i = 10
while i >= 0:
    print(i)
    i = i - 1
```

**Output:**
```
10
9
7
6
5
4
3
2
1
0
```

**Explanation:**
The `while` statement will loop on the condition, until the condition evaluates to `False`. The loop exits when the condition becomes False.

> Note: The `while` statement also has an else block, we encourage you to play with it to understand it better.

### Exercise:

1. Print all numbers till 100 using while.
1. Print all numbers from 100 to 1 using while.
1. Print all even numbers less than 100 using while.
1. Print all odd numbers less than 100 using while.
1. For a list [1,2,3,4,5], write a program which checks if 6 is present in the list, using while.
1. Print all numbers from 0 to 10 except 4 and 5.

#### try - except - finally
Read the [docs](https://docs.python.org/3/reference/compound_stmts.html#the-try-statement)

try-except is used for exception handling, we'll take a look at it in a later chapter. 

#### with 
> Note: requires the knowledge of file handling, you can come back to this chapter after reading the file handling chapter.

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

|[Next](06-file-handling.md) | [Previous](04-list-set-dict.md) |  [Index](../SUMMARY.md)
| ----| ----| ----| 

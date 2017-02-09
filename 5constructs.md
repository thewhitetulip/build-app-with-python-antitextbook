# Constructs

There are following constructs in Python. We will use the interpreter in this chapter too.

For these statements, you'll use the indentation rule which we looked in the second chapter, refresh the chapter if you can't recollect indentation!

### Note: 
Please do not copy paste the code below, we encourage you to type the code.

1. if else

if-else statement is for conditional branching.
```Python
>>> a = 10
>>> if a > 10:
...     print("A is greater than 10")
... elif a < 10:
...     print("A is less than 10")
... else:
...     print("A is equal to 10")
...
A is equal to 10

```

If a is greater than 10, then the first print statement is executed.
If a is NOT greater than 10 and is less than 10 then the second statement.
If both of the above are false, then the last.

The way the if statement works, is 

```python
if condition:
	<code>
elif condition:
	<code>
else:
	<code>
```

The `condition` here is something that evaluates to a Boolean True. If it evaluates to a boolean False, then it doesn't execute.

Try running these blocks

```python
>>> if True:
...    print("This is the true block")

>>> if False:
...    print("This is the false block")
```

2. for

For is the looping construct used for looping definitely. For instance you have a dictionary containing n elements, you'll loop through the keys of the dictionary and print the values, or you have a list and you want to print all the values, in these cases, you'll use the for construct.

If you have a list [1,2,3,4,5] there are two ways in which you can loop on the list

```python
>>> l = [1,2,3,4,5]
>>> for i in l:
...     print(i)
...
1
2
3
4
5
>>> for i in range(len(l)):
...     print(l[i])
...
1
2
3
4
5
```

`for` has an else block. It is strange at first glance, but it is quite helpful in certain cases, like finding if a number if prime or not.


```python
>>> for i in [1,2,3]:
...     print(i)
... else:
...     print("out of for loop")
...
1
2
3
out of for loop
```

The logic of the `else` block in the `for` statement is the same as the `else` of the `if` statement. The first block of statements are executed when the counter is iterating on the variable used after `in`. The moment it finishes iteration the `else` block is executed.

Range returns the next value to the for statement whenever it gets executed, it is lazy loading. It returns an iterable object, you are highly encouraged to loop up "Iterable objects in Python" on any search engine, preferable https://duckduckgo.com, we find that DDG returns better results for coding questions. (I am not getting paid for suggesting you to use DDG, it is that good)

3. while

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
When you use the break statement, you kill the current loop.

```python
for i in range(100):
	if i == 4:
		break
	print(i)
```

The above block will print all the numbers until it hits 4. The moment it hits 4, it'll kill the for loop.

2. continue
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

4. try - except
5. with 

We encourage you to read more about the `range` function. Please **do not use the Internet**, use the `help` function. The faster you get familiar to using the documentation, the better programmer you become. In a world full of people Googling "how to create a string in Python", we really need to be self sufficient as to using the documentation that a language provides to differentiate from others. The mark of a great programmer isn't in how much things she can store in her memory, it is in the mastery of the tools she uses, documentation and the help command are among the tools.

# Building a todo list manager

From this chapter on, we will start building an application. The end goal is going to write a command line todo list manager.

The functionality is going to be something like this:

```bash
$ python tasks.py add "title of the task" "content of the task"
new task added

$ python task.py remove "title of the task"
task deleted

$ python task.py list
task_one content_of_1
task_two content_of_2
```

The software design phase is the most critical phase of software development, writing software is a cakewalk when the design is done properly.

Before we can write the code, we have to:

1. Identify the input source.
    Our input source will be command line arguments.
1. Define the functionality of the program.
	Program will support adding/removing/listing todo items.
1. Identify where to store data. 
	Program will store content in a flat file.
1. Identify what will be the output.
	Program will print data on the terminal.

## Input

The user is going to give input in the command line arguments.

The 'sys' package has the command line arguments stored into a variable called 'argv'.

###### file: tasks1.py

```python
import sys
print(sys.argv)
```

Try running the code, you will see something like this

```
ch10 $  python3 tasks.py
['tasks.py']

ch10 $  python3 tasks.py "title" "content"
['tasks.py', 'title', 'content']
```

For the interpreter, tasks.py, title and content are all command line arguments, this is what you see as the output of the above script.

## Output

The output of the program is going to be on the command line. 

## Formatting output

#### file: tasks2.py

```python
import sys
for i, item in enumerate(sys.argv):
    print("{0} {1}".format(i, item))
```

Enumerate takes a sequence and returns (index,value) for each value.

## Formatting.
Starting from Python3.6, we can do this:

```python
print(f"{i} {sys.argv[i]}")
```
Where, `i` and `sys.argv[i]` are variables. Read the [docs](https://docs.python.org/3/whatsnew/3.6.html#pep-498-formatted-string-literals)

Try running tasks2.py with various command line arguments.

	ch10 $ python tasks2.py
	0 tasks2.py

We didn't give any parameter, since we know that the 0'th argument is going to be the file name itself, there are no suprises here.

	ch10 $ python tasks2.py title content
	0 tasks2.py
	1 title
	2 content

We passed title and content, and the index 1 is title, index 2 is content.

	ch10 $ python tasks2.py add  title content
	0 tasks2.py
	1 add
	2 title
	3 content

We passed "add title content" as the command line argument, and we get the expected output.

## Adding commands

##### file: tasks3.py

```python
import sys
args = sys.argv

command = args[1]

if command not in ("add","remove","list"):
	print("Invalid command, Use add/remove/list")

if command == "add":
	print("adding")
elif command == "remove":
	print("removing")
elif command == "list":
	print("listing")
else:
	print("invalid command!")
```

You'll get this output when you run the code, this is an `exception`.

	ch10 $ python3 tasks3.py
	Traceback (most recent call last):
	File "tasks3.py", line 5, in <module>
		command = args[1]
	IndexError: list index out of range

What went wrong? 

We encourage you to try to figure out what went wrong, before moving ahead.

## Handling errors

In the earlier file, we tried to access an list index which didn't exist. This raised an exception, we saw in the chapter about exceptions that a try-catch block is used to handle exceptions.

Update the `command = args[1]` line in the file to this block:
```python
try:
	command = args[1]
except IndexError:
	print("Invalid arguments!")
	sys.exit(1)
```

### Exit
`exit` kills the program execution with the ID of what we pass in as an argument, 0 is successful exit, anything greater than 0 is unsuccessful exit 

We catch IndexError exception. If there is an IndexError exception that means that the user has not given the appropriate arguments.

Save and run the file. The output should be this:

	ch10 $ python tasks3.py
	Invalid arguments!

We have handled the scenario where the user gives less input than what is required. Now let's move ahead and type an invalid command.

	ch10 $ python tasks3.py random
	Invalid command
	Use add/remove/list
	invalid command!

We can see that the "invalid command" message is being repeated twice, we have to do something about that.

We add another exit call after printing Invalid command. The reason being there is no need to go any further when we have established that the user has given us the invalid command.

```python
if command not in ("add","remove","list"):
	print("Invalid command\n Use add/remove/list")
	sys.exit(1)
```

	ch10 $ python tasks3.py random
	Invalid command
	Use add/remove/list

Now, let's test the `list` command.

	ch10 $ python tasks3.py list
	listing

## Storing user data

Now that we have finished getting started with our menu driven program, let's go ahead and create a list. We need a variable to store the task list. When the program would be used the additions and deletions would be done on this list object, which would be written to the file when the output is required.

Add this line after `args = sys.argv`

```python
tasks = []
```

This will create a variable by the name `tasks` which is visible in this file to all functions.

In the `list` block, we want to now print the values stored inside `tasks` variable. If the values aren't present, we should print "No tasks present", if there are tasks, then we should print the elements inside `tasks`.

We have to use the `len()` function to check if there is nothing in the variable.

Update this block.

## Listing tasks

```python
# This is a snippet
# can't have elif without parent if
elif command == "list":
	if len(tasks) == 0:
		print("there are no tasks!")
	else:
		for task in tasks:
			print(task)
```


We now simulate data, before we let the user have the ability to add a task, we will populate the task variable by ourselves.

For simplicity, we choose this format, the title and content would be concatenated by a | character.

update the `tasks = []` to this line, `tasks = ["title|content"]`.

And the else block of len(tasks) to this

```python
for task in tasks:
	title, content = task.split('|')
	print("{0} {1}".format(title, content))
```

## Adding a task

We will now work on adding a new task. The input would be taken from the command line argument.

```python
if command == "add":
	print("adding")
```

This block is changed to:

```python
if command == "add":
	title = args[2]
	content = args[3]
	task = title + content
	tasks.append(task)
```

But changing this does nothing, this is because the `tasks` variable is stored during the runtime. It gets reset to the default variable when the program quits. We need to add file handling feature to store the task list.

Replace the `tasks` line to this to store an empty variable.

```python
tasks = []
```

The if-else block should look like this:

```python
if command == "add":
	title = args[2]
	content = args[3]
	task = title + content
	file = open("tasks.txt", "a")
	file.write(task+"\n")
	file.close()
elif command == "remove":
	print("removing")
elif command == "list":
	file = open("tasks.txt", "r")
	tasks = file.readlines()
	if len(tasks) == 0:
		print("there are no tasks!")
	else:
		for task in tasks:
			title, content = task.split('|')
			print("{0} {1}".format(title, content))
	file.close()
```

## Our first bug!

If you run this file, you'll get an IOError saying that tasks.txt doesn't exist. This is because we have not handled this scenario in the `open` function. We need to wrap that in a try-except block.

	ch10 $ python tasks3.py list
	Traceback (most recent call last):
	File "tasks3.py", line 28, in <module>
		file = open("tasks.txt", "r")
	IOError: [Errno 2] No such file or directory: 'tasks.txt'

In the elif block of list, we make the following modifications:

```python
try:
	file = open("tasks.txt", "r")
except IOError as e:
	print(str(e))
	sys.exit(1)
tasks = file.readlines()
```

Now when we run the code, 

	ch10 $ python tasks3.py list
	[Errno 2] No such file or directory: 'tasks.txt'

This is a graceful handling of the scenario where we aren't able to access the file due to an I/O (Input/Output) operation error.

	ch10 $ python tasks3.py add "new task" "new content"

Now, let's list the tasks.

	ch10 $ python tasks3.py list
	Traceback (most recent call last):
	File "tasks3.py", line 38, in <module>
		title, content = task.split('|')
	ValueError: need more than 1 value to unpack

Now, we run the add command and try to list the values. We get an error, we can't add a try-except block to everything, so it is necessary to figure out what the issue is. Here, when we do `cat tasks.txt`, we come to know that the content of the file is this.

	ch10 $ cat tasks.txt
	new tasknew content

We don't have a | character between the title and content! We did a mistake when we concatenated title and content. Remove the file by doing `rm tasks.txt`, or, delete the file manually if you are on windows.

Instead of `task = title + content`, we need this, `task = title + "|" + content`.

This is the output now

	ch10 $ python tasks3.py add "new title" "new content"
	ch10 $ python tasks3.py list
	new title new content

This is great! We now are able to add and list the tasks.

#### Note:
When giving input over the command line, if you want to give multi word input, please enclose them in either single or double quote. For instance, we gave the input "new title", because our title contained a space. If we had given tasks2.py add new title, "new" would be considered the title because space is the delimiting character for any command line input, hence the "new title" enclosed in quotes.

	ch10 $ python tasks3.py add "Finish Python book" "Working on 10'th chapter"
	ch10 $ python tasks3.py list
	new title new content

	Finish Python book Working on 10'th chapter

You can see that the output of the list command isn't particularly good, so let's use the advanced features of the print function for this.

Replace the else block of `if len(tasks)==0` by this.

```python
print("|-----{0}----{1}----|".format("title", "content"))	
tasks = [task.strip() for task in tasks]
for task in tasks:
	title, content = task.split('|')
	print("|-{0}----{1}-|".format(title, content))
```

Format specifiers enable us to control the layout of the print, we encourage you to try various things out.

The final code should look like this.

```python
import sys

args = sys.argv

tasks = []

try:
	command = args[1]
except IndexError:
	print("Invalid arguments!")
	sys.exit(1)

if command not in ("add","remove","list"):
	print("Invalid command\n Use add/remove/list")
	sys.exit(1)


if command == "add":
	title = args[2]
	content = args[3]
	task = title + "|" + content
	file = open("tasks.txt", "a")
	file.write(task+"\n")
	file.close()
elif command == "remove":
	print("removing")
elif command == "list":
	try:
		file = open("tasks.txt", "r")
	except IOError as e:
		print(str(e))
		sys.exit(1)
	tasks = file.readlines()
	if len(tasks) == 0:
		print("there are no tasks!")
	else:
		print("|-----{0}----{1}----|".format("title", "content"))
		tasks = [task.strip() for task in tasks]
		for task in tasks:
			title, content = task.split('|')
			print("|-{0}----{1}-|".format(title, content))
	file.close()
else:
	print("invalid command!")
```

## Removing tasks

To remove tasks, we have to change the way we structure our data. We either can accept deletion on the basis of the title of the task, or we can render index for each task, since deletion from the title is not exactly scalable (two tasks can have the same title but different content), we choose to modify our program to show index for each task, that way, the user can just give the index of the task which they want to delete.

#### file: tasks4.py

We first need to modify the way we represent our tasks to the user, instead of showing just the title and content, we will show the index too. For this, we need to make the following changes.

We can't loop like `for task in tasks`, we need to loop using `range`, `for i in range(len(tasks))` is the way to go. The only difference is that we have to then fetch the task as `tasks[i]` rather than just `task`, because now, there is no such variable as `task`.

```python
## Snippet, else can't exist without parent if
else:
	print("|-{0}----{1}----{2}----|"%("index", "title", "content"))
	tasks = [task.strip() for task in tasks]
	for i in range(len(tasks)):
		title, content = tasks[i].split('|')
		print("|-{0}--{1}----{2}-|" %(i, title, content))
```

In the actual delete block, we will use the del keyword which will simplify our task greatly.

```python
# Snippet
elif command == "remove":
	task_id = args[2]
	del tasks[task_id]
```

	ch10 python3 tasks4.py remove 0
	Traceback (most recent call last):
	  File "tasks4.py", line 27, in <module>
	    del tasks[task_id]
	TypeError: list indices must be integers or slices, not str

###### Note:
We are not validating if the user has given appropriate input, let's say the user gives `python tasks4.py remove` instead of `python tasks4.py remove 0`, then our program should complain about an error, the same is the case with add, if the user doesn't give both title and content, that's an error and it should be handled appropriately.

We can see that "list indices must be integers" is the error we got for the del statement, the reason for that is that as we said, all shell operations are string based, so when the user gave us the input 0, it was '0', thus a string. We will typecast the `task_id` variable to an integer. Change it to this below statement.

We also need to read the file, for each instance, we read the file or appended it as required.

```python
del tasks[int(task_id)]
```

We also need to write the updated `tasks` variable to our file, we add a "\n" to each element using the list comprehension mechanism.

Now try running the code.
```python
## snippet
elif command == "remove":
	try:
		file = open("tasks.txt", "r")
	except IOError as e:
		print(str(e))
		sys.exit(1)
	
	file.close()
	tasks = file.readlines()
	tasks = [task.strip() for task in tasks]
	task_id = args[2]
	del tasks[int(task_id)]

	file = open("tasks.txt", "w")
	tasks = [task + "\n" for task in tasks]
	file.writelines(tasks)

```

Output:

	ch10 $  python3 tasks4.py remove 0
	ch10 $  python3 tasks4.py remove 1

###### Note:
We do not print confirmation like "task deleted", "task added", but you can add them if you want.

We have a fully working todo list manager as of now, what we need to do, is to reduce the redundancy. That'll be undertaken in the next chapter.

## Homework
Translate this todo list app to use sqlite3 database which comes inbuilt with Python. Please do not use the Internet, use the sqlite3 documentation.

##### Links

|[Next](11-function-tasks.md) | [Previous](09-functions.md) |  [Index](SUMMARY.md)
| ----| ----| ----| 

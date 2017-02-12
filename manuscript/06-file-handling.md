# File handling

File handling is one of the most important features of any programming language. As always, python makes it very easy to handle files.

*Note: this is the interpreter*

```python
>>> f = open("zfile.txt","w")
>>> f
<_io.TextIOWrapper name='zfile.txt' mode='w' encoding='UTF-8'>
>>> f.write("Hello world") # returns the number of characters written
11
>>> f.close()
>>> import os
>>> files = os.listdir(".")
>>> # below line is called list comprehension
>>> files = [file for file in files if file == "zfile.txt"]
>>> print(files)
['zfile.txt']
```
	
There are various modes you can open a file:

1. read
```python
f = open("file.txt", "r")
```

Used for files which are already created. You can read data from it. You can't write to a file opened in read mode. It throws an error if you try to open a file which doesn't exist. The error is in the form of an exception which we handle using the try-except block. Doesn't allow you to write to the file.

2. write

```python
f = open("file.txt", "w")
```

Creates a file if it isn't present. Overwrites a file if it is present. Use the write mode only if you are very sure that the file doesn't exist already or if you don't care if you lost the contents of the original file. Doesn't allow you to read content from the file.

3. append

```python
f = open("file.txt", "a")
```

Creates a file if it isn't present. Adds content to the end of the file, doesn't overwrite the file as the write mode does. Doesn't allow you to read content from the file.

4. binary

```python
f = open("file.txt", "b")
```

The above modes are all text based, if you want to open a binary file and read or write to it, use the binary mode.

You can also club the modes, if you want to read a binary file, use "rb". In another case, if you want to read and append to a file, use the "ra" mode. If you want to read and write "rw".

We encourage you to try out various modes in the interpreter.


1. write the first 100 even numbers to a file named even.txt

Save the following code in a .py file and run it from the command line. Try opening the even.txt file in any text editor and check what is the output.

```python
f = open("even.txt", "w")
for i in range(100):
	if i % 2 == 0:
		f.write(i)
f.close()
```

The first error you will get is 

	Traceback (most recent call last):
	  File "<stdin>", line 3, in <module>
	TypeError: write() argument must be str, not int

Change `f.write(i)` to `f.write(str(i))`.

All read or write operations on files are done via strings. It is mandatory to **close** the file. When the close function is called, only then does the content you wrote gets actually written to the file, until the `close` is called, it is just stored in the memory. The close function calls the `flush` function and closes the file. If you want output to get instantaneously written ot your file, call `f.flush()` after your `f.write()`.

Try running the code again, this time, it will succeed. After opening it in a text editor, you'll notice that it wrote numbers in one line. This is where file handling differs from printing on the terminal. On the terminal, the print() statement adds a "\n" newline at the end by default, but when it comes to files, you have to handle the new line characters by yourself.

Create a new file using notepad or any other text editor and write four lines to it, anything you want. Use the file name "lines.txt".

```python
f = open("lines.txt") # mode is optional, defaults to read
lines = f.readlines()
print(lines)
```

The textual representation of a new line is \n, thus, when you read the file in python, you'll see \n at the end of each new line. When you write to a file in Python, you have to append "\n" to the end of each line, only then will you see a new line, otherwise it'll just keep writing to the file.

```python
f = open("even.txt", "w")
for i in range(100):
	if i %2 == 0:
		f.write(str(i) + "\n")
f.close()
```

Now open the even.txt file, you'll see everything printed into the file on a new line.

#### Note

`str(i)` converts anything that is stored in the variable i to string. There are other functions like `int()`, `list()`, `dict()`, `set()` which do type conversions, but they convert specific types and don't work with anything you throw at them.

One essential part of working with files is removing the \n.

```python
f = open("lines.txt")
lines = f.readlines()
print(lines)
lines = [line.strip() for line in lines] # list comprehension
print(lines)
```


List comprehension is a shortcut way of working with lists. They work if you want to filter the list or perform some operation on the entire list.

	lines = [line.strip() for line in lines]

this line can be replaced with a normal for statement as 

```python
for i in range(len(lines)):
	lines[i] = lines[i].strip()

lines = [line.strip() for line in lines]
```
	[ condition for i in <list> if <another condition>]

List comprehension returns a new list based on the current list, the first argument `list.strip()` would be the elements of the list. The second argument is the for loop, the third argument is optional, you can have an `if` block there.

```python
a = ["a.txt", "b.txt", "c.tct", "j.txt"]
# list comprehension to remove *.tct
b = [f for i in a if not a.endswith(".tct")]
# write another list comprehension to remove all .txt files
```

There are various functions for File IO

1. read()
Takes an argument as number of bytes to be read. When you open a file for reading, the pointer is at the 0'th position. if you do `f.read(1)`, the pointer moves to 1. If you do `f.read(1)` again, the pointer would return the 2nd character of the file and not the first one.

All the read functions returns characters based from the current pointer, you can know where the pointer is located currently by using `f.tell()`.

```python
>>> f = open("lines.txt")
>>> f.tell() # pointer is at 0th position
0
>>> f.read(1) # returns the first character
'f'
>>> f.tell() # pointer shifted to 1st character
1
>>> f.read(20) # reads 21 characters after 1
'irst line\n second li'
>>> f.tell()
21
>>> f.read(10000) # reads 22 char after 10000
'ne \n third line \n'
>>> f.tell() # pointer on 38
38
>>> f.read(10) # read 10 more char
'' 
>>> f.tell() # this is the last position!
38
>>> f.seek(0) # pointer is now at start of file
0
>>> f.read(1)
'f'
```

In this example, you hit the end of the file, there are only 38 characters in it, "\n" also is a character. If you read beyond the max characters of a line, it will return you blank strings. but there might be cases in which you would want to start reading the file again from any other position. 

You can use `seek` function to reset the pointer at any position of your choice. Let's say that you want to re-read the file again

```python
>>> f.seek(0)
```

This will reset the pointer and you should be able to read it from the first character of the file!

2. readline()
Returns the current line that the pointer is at.

```python
>>> f.seek(0)
0
>>> f.readline()
'first line\n'
>>> f.readline()
' second line \n'
>>> f.readline()
' third line \n'
```

You can try doing `f.seek(0)` and reading the lines again, you'll get the same output as above.

3. readlines()
Returns all the lines of the file as a list. Depends on the pointer, if the pointer is on 0 then it retuns the entire file, otherwise it returns all lines after the pointer.

```python
>>> f.seek(13)
13
>>> f.readlines()
['econd line \n', ' third line \n']
>>> f.seek(0)
0
>>> f.readlines()
['first line\n', ' second line \n', ' third line \n']
```

4. write()
Writes the **string** argument which you pass on the pointer. We need to be careful of the pointer, otherwise writing to the file can be dangerous. You are responsible for adding the "\n" character if you want to a new line, by default it'll write at the position the pointer is currentl `f.tell()`.

5. writelines()
If you want to write a list to a file, you'll use writelines. Even here you are responsible for adding \n wherever you feel necessary.

```python
j = ["\nthis is something\n", "another line\n"]
f.writelines(j)
f.close()
```	

We encourage you to try out file IO on your own, please refer to help(f) for any details regarding file, do not search "how to open a file in Python" on the internet.

##### Links

|[Next](07-examples.md) | [Previous](05-constructs.md) |  [Index](SUMMARY.md)
| ----| ----| ----| 
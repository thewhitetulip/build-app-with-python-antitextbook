# File handling

Managing files is one of the most important features of any programming language. Python supports file handling via the io module's TextIOWrapper class, [docs](https://docs.python.org/3/library/io.html#io.TextIOWrapper)

Modes in which a file can be opened:

###  read

```python
f = open("file.txt", "r")
```

* The second argument to the `open` function should be `r`.
* Files which are already existing can be read.
* An exception is thrown if the file doesn't exist.
* Writing or appending the file is not allowed.

### write

```python
f = open("file.txt", "w")
```

* The second argument should be `w`.
* Creates a file if it isn't present. 
* If a file is present, it gets overwritten. If a file is overwritten, all the data is lost and is unrecoverable.
* Doesn't allow the file to be read.

### append

```python
f = open("file.txt", "a")
```

* The second argument should be `a`.
* Creates a file if it isn't present. 
* Adds content to the end of the file.
* Does not overwrite the file like the write mode.
* Doesn't allow file to be read.

### binary

```python
f = open("file.txt", "b")
```

r, w, a are modes for working with textual files. Python allows manipulation of binary files by using the binary mode, the second argument to the open function should be `b`.

Python allows modes to be clubbed.

* Read a binary file: "rb".
* Write a binary file: "wb".
* Read and append to a file: "ra".
* Read and write: "rw".

### Sample file handling programs

1. write the first 100 even numbers to a file named even.txt

```python
f = open("even.txt", "w")
for i in range(100):
	if i % 2 == 0:
		f.write(i)
f.close()
```
Save this program in a file and run it.

The first error you will get is 

```
Traceback (most recent call last):
File "<stdin>", line 3, in <module>
TypeError: write() argument must be str, not int
```

Change `f.write(i)` to `f.write(str(i))`.

**Explanation:**

All read or write operations on files are done via strings, when we tried `f.write(i)`, we were trying to write an integer to the file, which is a syntax error since the `write` method expects a string argument and not an integer. 

When we work with files, it is mandatory to close the file when we are done with it. It helps in saving system resources. There is another reason for closing a file: buffering. 

When we write anything to a file, it gets written to a buffer and not directly to the underlying file. The buffer is flushed to the underlying file after we call the close method. 

However, the buffer can be bypassed by using `flush()` immediately after a `write` call, that way, everything is written down to the underlying file and not just in the buffer.

Try running the code again, this time, it will succeed. 

Open the output file in a text editor. You'll notice that it wrote the numbers in a single line. This is where file handling differs from printing on the terminal. On the terminal, the print() statement adds a "\n" newline at the end by default, but when it comes to files, you have to handle the new line characters by yourself.

Create a new file with the name "lines.txt" and write four random lines to it. After that, save the following code in a file in the same directory and run the file.

```python
f = open("lines.txt") # mode is optional, defaults to read
lines = f.readlines()
print(lines)
```

The output you'll see would have "\n" after each line in the list. This is because the textual representation of a new line is `\n`, thus, when you read the file in python, you'll see `\n` at the end of each new line. When you write to a file in Python, you have to append `\n` to the end of each line, only then will you see a new line, otherwise it'll just keep writing to the file.

```python
f = open("even.txt", "w")
for i in range(100):
    if i %2 == 0:
        f.write(str(i) + "\n")
f.close()
```

Now open the even.txt, you'll see everything printed into the file on a new line.

#### Note

`str(i)` converts anything that is stored in the variable i to string. There are other functions like `int()`, `list()`, `dict()`, `set()` which do type conversions, but they convert specific types and don't work with anything you throw at them.

One essential part of working with files is removing the `\n`.

```python
f = open("lines.txt")
lines = f.readlines()
print(lines)
lines = [line.strip() for line in lines] # list comprehension
print(lines)
```

#### List comprehension 
It is a shortcut of working with lists, to perform filter or some other operation on the entire list.

	lines = [line.strip() for line in lines]

List comprehension replaces the following block:

```python
for i in range(len(lines)):
    lines[i] = lines[i].strip()

lines = [line.strip() for line in lines]
```
##### Syntax

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

> Note: This is a session for the Interpreter.

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

# File handling

Managing files is one of the most important features of any programming language. Python supports file handling via the io module's TextIOWrapper class, [docs](https://docs.python.org/3/library/io.html#io.TextIOWrapper)

There are two basic modes in which we can manipulate files, Text and Binary.

1. Write all even numbers till 100 to a file named "even.txt" and write all odd numbers to "odd.txt".

```python
# The second argument should be `w`.
# Creates a file if it isn't present. 
# If a file is present, it gets overwritten. 
# If a file is overwritten, all the data is lost and is unrecoverable.
# Doesn't allow the file to be read.
even_file = open("even.txt", "w")
odd_file = open("odd.txt","w")

for i in range(100):
    if i % 2 == 0:
	    # All IO operations happen via strings.
		# so argument of write should be a string.
	    even_file.write(str(i))
		even_file.write("\n")
	else:
	    odd_file.write(str(i))
		odd_file.write("\n")

even_file.close()
odd_file.close()
```

**Why close a file?**

It is mandatory to close the file after use to free system resources. When we write anything to a file, it gets written to a buffer and not directly to the underlying file. The buffer is flushed to the underlying file after we call the close method. However, the buffer can be bypassed by using `flush()` immediately after a `write` call, that way, everything is written down to the underlying file and not just in the buffer.

Run the above code by removing the `write("\n")` method call. After that, open "even.txt" in a text editor. You'll notice that it wrote the numbers in a single line. This is where file handling differs from printing on the terminal. On the terminal, the print() statement adds a newline ("\n") but the `write` method does not.

Create a new file with the name "lines.txt" and write four random lines to it. After that, save the following code in a file in the same directory and run the file.

```python
f = open("lines.txt") # mode is optional, defaults to read
lines = f.readlines()
print(lines)
```

The output would be a list of four items, with each item ending with a "\n". This is because the textual representation of a new line is `\n`, thus, when you read the file in python, you'll see `\n` at the end of each new line. When you write to a file in Python, you have to append `\n` to the end of each line, only then will you see a new line, otherwise it'll just keep writing to the file in a single line.

```python
f = open("even.txt", "w")
for i in range(100):
    if i %2 == 0:
        f.write(str(i) + "\n")
f.close()
```

Now open the even.txt, you'll see everything printed into the file on a new line.

2. Read all the content from the file "even.txt" and print it to the terminal

```python
# The second argument to the `open` function should be `r`.
# then the file is opened in read mode.
# Files which are already existing can be read.
# An exception is thrown if the file doesn't exist.
# Writing or appending the file is not allowed.
input_file = open("even.txt", "r")

# readlines reads the complete file and returns a list
# of all lines.
lines = input_file.readlines()
for line in lines:
    print(line)
```

While reading a file, we need to deal with the "\n" present at the end of each line. There is a shortcut to remove the "\n".

```python
f = open("even.txt")
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
# write another list comprehension to remove all .tct files
```

3. Write even numbers from 100 to 200 in a file "even.txt" which already contains even numbers from 0 to 100.

```python
# The second argument should be `a`.
# Creates a file if it isn't present. 
# Does not overwrite the file like the write mode.
# Adds content to the end of the file.
# Doesn't allow file to be read.
file = open("even.txt", "a")

for i in range(100, 200):
    if i % 2 == 0:
	    file.write(str(i))
		file.write("\n")

file.close()
```

When we use the above modes (read/write/append), they mean text files unless we use the binary mode.


### Binary Mode

```python
f = open("file.txt", "rb")
```

Python allows us to manipulate binary files, we have to club the modes, `b` stands for binary, along with `b`, we can use any of r/w/a.

Clubbing can be done without using the binary mode:
	
	* Read a binary file: "rb".
	* Write a binary file: "wb".

> Note: One essential part of working with files is removing the `\n` or adding it when it is required.


## Other methods

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
>>> f.read(20) # reads 20 characters after 1 ('\n' is considered as single character)
'irst line\n second li'
>>> f.tell()
21
>>> f.read(10000) # reads 17 char after 21
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

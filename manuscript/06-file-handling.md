# File handling

Managing files is one of the most important features of any programming language. Python supports file handling via the io module's TextIOWrapper class, [docs](https://docs.python.org/3/library/io.html#io.TextIOWrapper)

There are two basic modes in which we can manipulate files, Text and Binary.

## Writing files
Write all even numbers till 100 to a file named "even.txt" and write all odd numbers to "odd.txt".

```python
# open() opens a file and returns the address of the object
# To be able to write to a file, the second
# argument should be w.
even_file = open("even.txt", "w")
odd_file = open("odd.txt","w")

# Opening file in write mode
# Creates a file if it isn't present. 
# If a file is present, it gets overwritten and data is lost.
# write mode doesn't allow the file to be read.

for i in range(100):
	if i % 2 == 0:
	    # All IO operations happen via strings.
	    # so argument of write should be passed a string.
	    even_file.write(str(i))
	    even_file.write("\n")
	else:
	    odd_file.write(str(i))
	    odd_file.write("\n")

# A file should always be closed
# to free system resources.
even_file.close()
odd_file.close()
```

**Why close a file?**

When we write anything to a file, it gets written to a buffer and not directly to the underlying file. `flush()` method can be used to immediately write to the file. The `close()` method internally calls the `flush()` method, thus, in most of the cases, it is enough to just call the `close()` method.

## Reading files 

Read all the content from the file "even.txt" and print it to the terminal

```python
# To be able to read a file, the second argument
# should be r.
input_file = open("even.txt", "r")

# Files which are already existing can be read.
# An exception is thrown if the file doesn't exist.
# Writing or appending the file is not allowed.

# readlines reads the complete file and returns a list
# of all lines.
lines = input_file.readlines()
for line in lines:
    print(line)
```

You will see that each number is printed on a different line. This is because of the new line ("\n") character which we wrote.

### The case of the new line.
Whenever we read or write to a text file, we are responsible for the new line character "\n". When a file's content is "python\nis a good language.", it is displayed as 

```
python
is a good language
```

on any text editor, because the "\n" gets converted into an actual new line. But, the content of the text file is still 
"python\nis a good language."

```python
file = open("file.txt", "w")
for i in range(5):
    file.write(str(i))
file.close()

file = open("file.txt", "r")
lines = file.readlines()
print(lines)
```

Output:
['01234']

We can see that the file contains only one line. This is because, the `write` method doesn't add a new line character at the end of each operation. To understand it better, open this file in a text editor.

Now, consider this block.

```python
file = open("file.txt", "w")
for i in range(5):
    file.write(str(i) + "\n")
file.close()

file = open("file.txt", "r")
lines = file.readlines()
print(lines)
```

Output:

['0\n', '1\n', '2\n', '3\n', '4\n']

By adding a "\n" in each write call, we ensure that the new number gets written to a new line, that's why, when we run the above code, we will get four lines in the text file. Verify this by opening the file in a text editor.

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
```
##### Syntax

	[ condition for i in <list> if <another condition>]

List comprehension returns a new list based on the current list, the first argument `list.strip()` would be the elements of the list. The second argument is the for loop, the third argument is optional, you can have an `if` block there.

```python
a = ["a.txt", "b.txt", "c.tct", "j.txt"]
# list comprehension to remove *.tct
b = [i for i in a if not a.endswith(".tct")]
# write another list comprehension to remove all .tct files
```

## Examples:

1. Convert each element to upper case (works only when each element is a string).
	```python
	a = ["a.txt", "b.txt", "c.tct", "j.txt"]
	b = [i.upper() for i in a]
	print(b)
	```

1. Convert each element to lower case (works only when each element is a string).
	```python
	a = ['A.TXT', 'B.TXT', 'C.TCT', 'J.TXT']
	b = [i.lower() for i in a]
	print(b)
	```

1. Give all the values of list a which are greater than 3.

	```python
	a = [1, 3, 4, 5, 5]
	b = [i for i in a if i > 3] 
	print(b)
	```

1. Give all the values of list a which are greater than 3.
	```python
	a = ["Haskell", "Ruby", "Python"]
	b = [i for i in a if len(i) > 3] 
	print(b)	
	```

1. Give all values in a which are even.

	```python
	a = [1, 3, 4, 5, 5]
	b = [i for i in a if i % 2 == 0] 
	print(b)
	```


## Appending files
Write even numbers from 100 to 200 in a file "even.txt" which already contains even numbers from 0 to 100.

```python
# To append to a file, the second argument should be a.
# if we open in write mode, we will lose the data present
# in the file before we open it.
file = open("even.txt", "a")

# Does not overwrite the file like the write mode.
# It will create a file if it isn't present. 
# Adds content to the end of the file.
# Doesn't allow file to be read.

for i in range(100, 200):
	if i % 2 == 0:
		file.write(str(i)+"\n")

file.close()
```

### Binary Mode

```python
f = open("file.txt", "rb")
```

Python allows us to manipulate binary files, we have to club the modes, `b` stands for binary, along with `b`, we can use any of r/w/a.
	
	* Read a binary file: "rb".
	* Write a binary file: "wb".

> Note: One essential part of working with files is removing the `\n` or adding it when it is required.


## Other methods

1. `read()`
	Takes an argument as number of bytes to be read.
	
	When you open a file for reading, the pointer is at the 0'th position. if you do `f.read(1)`, the pointer moves to 1. If you do `f.read(1)` again, the pointer would return the 2nd character of the file and not the first one.

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

2. `readline()`
	Returns the current line that the pointer is located.

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

3. `readlines()`
	Returns all the lines of the file as a list. 
	
	If the pointer is present at the end of file, then it returns an empty list. In that case, do a `f.seek(0)` to reset the pointer.

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

4. `write()`
	Writes the **string** argument which you pass on the pointer. We need to be careful of the pointer, otherwise writing to the file can be dangerous. You are responsible for adding the "\n" character if you want to a new line, by default it'll write at the position the pointer is currentl `f.tell()`.

5. `writelines()`
	If you want to write a list to a file, you'll use writelines. Even here you are responsible for adding \n wherever you feel necessary.

	```python
	j = ["\nthis is something\n", "another line\n"]
	f.writelines(j)
	f.close()
	```	

	We encourage you to try out file IO on your own, please refer to help() for any details regarding file, do not search "how to open a file in Python" on the internet.

## Exercise

1. Take the user's name, age and height as input and write them to a file using this format. name,age,height.
1. Read a file "input.txt" and print all the lines which are present multiple times. Please create the input.txt file in such a way that it has many lines and few of them are present multiple times.
1. Read a file "input.txt" and print how many times each line is present.
1. There are two files, "file1.txt" and "file2.txt"
	1. swap the content of both files.	
	1. append the content of file1.txt to file2.txt.
	1. append content of file2.txt to file1.txt.
	1. take unique content of both files and write them to file3.txt
1. Use any file created above. Take a positive number as input from the user and read those many characters from the text file.
1. Prepare a csv file like this: first field = name, second onwards marks/100.

	```
	tom,10,10,10
	tim,20,20,20
	```
	
	1. Print the name of the student with highest marks.
	1. Print the name of the student with highest marks in upper case.
	1. Print the highest score.
	1. calculate the total score of each student, add the total at the end of the line and write everything to result.csv

	sample output:

	```
	tom,10,10,10,30
	tim,20,20,20,60
	```

1. Read the result.csv file and create a new file named result.txt like the following sample output.
	
	```
	tom-10-10-10-30
	tim-20-20-20-60
	```
1. read the result.txt file. Print every other character from the file.


##### Links

|[Next](08-exception.md) | [Previous](05-constructs.md) |  [Index](SUMMARY.md)
| ----| ----| ----| 

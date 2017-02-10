## Some examples

1. Merge two files
1. Student Marks manager
1. CSV to SQL generator

Let's say you have two files, "file.txt" and "file2.txt" and you want to merge them. One can try sorting the file and then copy pasting and running some duplicate removal program, or one can use Python.

First read both the files and create a dictionary. In that dictionary, we create an integer entry about each line, if it is not present in the dictionary keys, we add a value, otherwise we increment the value, that way, we can find out the duplicate values if needed.

```python
first_file = open("file.txt")
second_file = open("file2.txt")

first_lines = first_file.readlines()
second_lines = second_file.readlines()

first_lines = [line.strip() for line in first_lines]
second_lines = [line.strip() for line in second_lines] 

final_lines = {}

for line in first_lines:
    if line not in final_lines.keys():
        final_lines[line] = 0
    else:
        final_lines+=1

for line in second_lines:
    if line not in final_lines.keys():
        final_lines[line] = 0
    else:
        final_lines[line]+=1

lines = "\n".join(list(final_lines.keys()))

file = open("output.txt", "w")
file.write(lines+"\n")
file.close()
```

Student Marks Generator

Say that you want to build some analytics software for a school for some reason, you have the following data in a csv file:

name,science,math,history
tony,12,12,12
antony,13,13,13
bantony,14,14,14

##### Links

| [Previous](12modules_tasks.md) | 
| ----| 
## Some examples

1. Merge two files
1. Student Marks manager
1. CSV to SQL generator

## Merge two files

Let's say you have two files, "file.txt" and "file2.txt" and you want to merge them. One can try sorting the file and then copy pasting and running some duplicate removal program, or one can use Python.

First read both the files and create a dictionary. In that dictionary, we create an integer entry about each line, if it is not present in the dictionary keys, we add a value, otherwise we increment the value, that way, we can find out the duplicate values if needed.


#### file name: ch13/merge.py

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

## Student Marks Manager

Say that you want to build some analytics software for a school for some reason, you have the following data in a csv file:

name,science,math,history
tony,12,12,12
antony,13,13,13
bantony,14,14,14

### file name: ch13/student_scores.py

```python

input_file = open("data.csv", "r")
score = input_file.readlines()
score = [line.strip() for line in score]

heading = score[0].split(",")
score = score[1:]
total_subjects = len(heading)

marks = {}

for i in range(len(score)):
    sc = score[i].split(",")
    marks[sc[0]] = sum([int(j) for j in sc[1:]])

for name in marks.keys():
    print("%s: %d"%( name, marks[name]))

#TODO print the name of the student who got the maximum aggregare marks
# This part is intentionally kept as homework for the readers.

```


## CSV to SQL generator

Let's say that you have a csv file which you want to import into a database and for some reason your db client doesn't support direct import, so you have the task to convert the data in csv file into insert statements.

This is a crude way to convert data, if you are having access to the database client in python, you can write your own importer without having to generate SQL statements.

### file name: ch13/csv_to_db.py

```python

file_name = "data.csv"
input_file = open(file_name, "r")
output_file = open("data.sql", "w")

csv_lines = input_file.readlines()
csv_lines = [line.strip() for line in csv_lines]

INSRT_STMT = 'INSERT INTO STUDENT(NAME, SCIENCE, MATH, HISTORY) VALUES('

inserts = []

for line in csv_lines[1:]:
    iline = line.split(",")
    insert = INSRT_STMT + '"' + iline[0] + '"'
    for i in iline[1:]:
        insert += ","
        insert += i
    insert+=");\n"
    inserts.append(insert)

output_file.writelines(inserts)
output_file.close()
```

##### Links

| [Previous](12-modules-tasks.md) |  [Index](SUMMARY.md)
| ----| ----| 
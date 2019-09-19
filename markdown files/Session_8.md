
# An introduction to Python

## Session 2.3: Files

- [Using files](#Using-files)
- [Data formats](#Data-formats)
- [Importing modules and libraries](#Importing-modules-and-libraries)
- [Using the `csv` module](#Using-the-csv-module)
- [Python file library](#Python-file-library)

# Data input and output (I/O)

So far, all that data we have been working with has been written by us into our scripts, and the results of out computation has just been displayed in the terminal output. In the real world data will be supplied by the user of our programs (who may be you!) by some means, and we will often want to save the results of some analysis somewhere more permanent than just printing it to the screen. In this session we cover 2 widely used ways of reading data into our programs, via the command line and by reading files from dish, we also discuss writing out data to files. 

There are, of course, many other ways of accessing data, such as querying a database or retrieving data from a network such as the internet. We don't cover these here, but python has excellent support for interacting with databases and networks either in the standard library or using external modules.

## Using files

Frequently the data we want to operate on or analyse will be stored in files, so in our programs we need to be able to open files, read through them (perhaps all at once, perhaps not), and then close them. 

We will also frequently want to be able to print output to files rather than always printing out results to the terminal.

Python supports all of these modes of operations on files, and provides a number of useful functions and syntax to make dealing with files straightforward.

### Opening files

To open a file, python provides the `open` function, which takes a filename as its first argument and returns a _file object_ which is python's internal representation of the file.


```python
path = "data/datafile.txt"
fileObj = open( path )
```

`open` takes an optional second argument specifying the _mode_ in which the file is opened, either for reading, writing or appending.

It defaults to `'r'` which means open for reading in text mode. Other common values are `'w'` for writing (truncating the file if it already exists) and `'a'` for appending.


```python
open( "data/myfile.txt", "r" ) # open for reading, default
```


```python
open( "data/myfile.txt", "w" ) # open for writing (existing files will be overwritten)
```


```python
open( "data/myfile.txt", "a" ) # open for appending
```

### Closing files

To close a file once you finished with it, you can call the `.close` method on a file object.


```python
fileObj.close()
```

### Mode modifiers

These mode strings can include some extra modifier characters to deal with issues with files across multiple platforms.

`'b'`: binary mode, e.g. `'rb'`. No translation for end-of-line characters to platform specific setting value.

|Character | Meaning |
|----------|---------|
|`'r'` |	open for reading (default) |
|`'w'` |	open for writing, truncating the file first |
|`'x'` |	open for exclusive creation, failing if the file already exists |
|`'a'` |	open for writing, appending to the end of the file if it exists |
|`'b'` |	binary mode |
|`'t'` |	text mode (default) |
|`'+'` |	open a disk file for updating (reading and writing) |

### Reading from files

Once we have opened a file for reading, file objects provide a number of methods for accessing the data in a file. The simplest of these is the `.read` method that reads the entire contents of the file into a string variable.




```python
fileObj = open( "data/datafile.txt" )
print(fileObj.read()) # everything
fileObj.close()
```

Note that this means the entire file will be read into memory. If you are operating on a large file and don't actually need all the data at the same time this is rather inefficient.

Frequently, we just need to operate on individual lines of the file, and you can use the `.readline` method to read a line from a file and return it as a python string.

File objects internally keep track of your current location in a file, so to get following lines from the file you can call this method multiple times.

It is important to note that the string representing each line will have a trailing newline `"\n"` character, which you may want to remove with the `.rstrip` string method.

Once the end of the file is reached, `.readline` will return an empty string `''`. This is different from an apparently empty line in a file, as even an empty line will contain a newline character. Recall that the empty string is considered as `False` in python, so you can readily check for this condition with an `if` statement etc.


```python
# one line at a time
fileObj = open( "data/datafile.txt" )
print("1st line:", fileObj.readline())
print("2nd line:", fileObj.readline())
print("3rd line:", fileObj.readline())
print("4th line:", fileObj.readline())
fileObj.close()
```

To read in all lines from a file as a list of strings containing the data from each line, use the `.readlines` method (though note that this will again read all data into memory).


```python
# all lines
fileObj = open( "data/datafile.txt" )

lines = fileObj.readlines()

print("The file has", len(lines), "lines")

fileObj.close()
```

Looping over the lines in a file is a very common operation and python lets you iterate over a file using a `for` loop just as if it were an array of strings. This does not read all data into memory at once, and so is much more efficient that reading the file with `.readlines` and then looping over the resulting list.


```python
# as an iterable
fileObj = open( "data/datafile.txt" )

for line in fileObj:
    print(line.rstrip().upper())

fileObj.close()
```

### The with statement

It is important that files are closed when they are no longer required, but writing ``fileObj.close()`` is tedious (and more importantly, easy to forget). An alternative syntax is to open the files within a ``with`` statement, in which case the file will automatically be closed at the end of the `with` block.


```python
# fileObj will be closed when leaving the block
with open( "data/datafile.txt" ) as fileObj:
    for ( i, line ) in enumerate( fileObj, start = 1 ):
        print("%s: %r" % ( i, line ))
```

### Writing to files

Once a file has been opened for writing, you can use the `.write()` method on a file object to write data to the file.

The argument to the `.write()` method must be a string, so if you want to write out numerical data to a file you will have to convert it to a string somehow beforehand.

<div class="alert-warning">**Remember** to include a newline character `\n` to separate lines of your output, unlike the `print()` statement, `.write()` does not include this by default.</div>


```python
marks = {
    'Luttapi': 43,
    'Dagini': 32,
    'Mayavi': 34
}

with open( "out.txt", "w" ) as output:
    output.write("Name\tMark\n")

    for mark in marks:
        line = "\t".join( [ mark, str(marks[mark]) ] )
        output.write(line + "\n")
```

To view the output file, open a terminal window, go to the directory where the file has been written, and print the content of the file using `cat` command or open it using your favourite editor:

```bash
cat out.txt
```

Be cautious when opening a file for writing, as python will happily let you overwrite any existing data in the file. 

## Data formats

JSON, XML, CSV, txt are a few common Data formats. You can learn more about those from various websites. Go on and search and read about them. 

Delimited file example:
```
X 169008682 1 111267453 1.0976
2 8265484 5 69763543 4.9825
MT 10924 MT 81934 7.2357
3 127 8 10908776 1.2509
```

### Reading delimited files

We can use the various string manipulation techniques covered earlier to process delimited files in a fairly straightforward way. Here we loop through a file with columns delimited by spaces, reading the data for each row into a list, and storing each of these lists into a main results list.

To view the an example of a delimited file, open a terminal window, go to the course directory, and print the content of the file using `cat` command or open it using your favourite editor:

```bash
cat data/mydata.txt
```

```
Index Organism Score
1 Human 1.076
2 Mouse 1.202
3 Frog 2.2362
4 Fly 0.9853
```


```python
results = []

with open("data/mydata.txt", "r") as data:
    header = data.readline()
    for line in data:
        line = line.strip()
        results.append(line.split(" "))
        
print(results)
```

Here we show a slightly more complicated example where we are reading the results into a more convenient data structure, a list of dictionaries with the dictionary keys corresponding to the column headers and the values to the values from each line. We also convert the columns to an appropriate type as we go.


```python
results = []

with open("data/mydata.txt", "r") as data:
    header = data.readline()
    for line in data:
        idx, org, score = line.strip().split(" ")
        row = {'Index': int(idx), 'Organism': org, 'Score': float(score)}
        results.append(row)
        
print(results)
print('Score of first row:', results[0]['Score'])
```

### Writing delimited files

Writing out a delimited file is also straightforward using the `join` method. Here, as an example we will recreate our original file from above, but this time we will delimit the columns with a comma.


```python
mydata = [{'Organism': 'Human', 'Index': 1, 'Score': 1.076}, 
          {'Organism': 'Mouse', 'Index': 2, 'Score': 1.202}, 
          {'Organism': 'Frog', 'Index': 3, 'Score': 2.2362}, 
          {'Organism': 'Fly', 'Index': 4, 'Score': 0.9853}]

with open('data/mydata.csv', 'w') as output:
    # write a header
    header = ",".join(['Index', 'Organism', 'Score'])
    output.write(header + "\n")
    for row in mydata:
        line = ",".join([str(row['Index']), row['Organism'], str(row['Score'])])
        output.write(line + "\n")
```

To view the output file, open a terminal window, go to the course directory, and print the content of the file using `cat` command or open it using your favourite editor:

```bash
cat data/mydata.csv
```

```
Index,Organism,Score
1,Human,1.076
2,Mouse,1.202
3,Frog,2.2362
4,Fly,0.9853
```

<div class="alert-warning">**NOTE** that there is actually a module in the standard library called `csv` which can also be used to read and write delimited files. There is example code reading this same file using this library towards the end of this notebook.</div>

## Importing modules and libraries

Like other laguages, Python has the ability to import external modules (or libraries) into the current program. These modules may be part of the standard library that is automatically included with the Python installation, they may be extra libraries which you install separately or they may be other Python programs you have written yourself. Whatever the source of the module, they are imported into a program via an <tt>import</tt> command.

For example, if we wish to access the mathematical constants pi and e we can use the import keyword to get [the module named `math`](https://docs.python.org/3/library/math.html) and access its contents with the dot notation:


```python
import math
print(math.pi, math.e)
```

Also we can use the `as` keyword to give the module a different name in our code, which can be useful for brevity and avoiding name conflicts:


```python
import math as m
print(m.pi, m.e)
```

Alternatively we can import the separate components using the `from … import` keyword combination, like we've seen in the [previous session](Introduction_to_python_day_2_session_2.ipynb#Modules):


```python
from math import pi, e
print(pi, e)
```

We can import multiple components from a single module, either on one line like as seen above or on separate lines:


```python
from math import pi
from math import e
```

### Listing module contents

Using the [method `dir()`](https://docs.python.org/3/library/functions.html?highlight=dir#dir) and passing the module name:


```python
import math
dir(math)
```

or directly using an instance, like with this String:


```python
dir("mystring")
```

or using the object type


```python
dir(str)
```

### Getting quick help on method

After listing all contents, you may wish to display specific information on a method using [`help()`](https://docs.python.org/3/library/functions.html?highlight=help#help)


```python
help(str.title)
```

### Getting help from the official Python documentation

The most useful information is online on https://www.python.org/ website and should  be used as a reference guide.

- [Python 3.5.2 documentation](https://docs.python.org/3/) is the starting page with links to tutorials and libraries' documentation for Python 3
    - [The Python Tutorial](https://docs.python.org/3/tutorial/index.html)
        - [Modules](https://docs.python.org/3/tutorial/modules.html)
        - [Brief Tour of the Standard Library: Mathematics](https://docs.python.org/3/tutorial/stdlib.html#mathematics)
    - [The Python Standard Library Reference](https://docs.python.org/3/library/index.html) is the documentation of all libraries included within Python as well as built-in functions and data types like:
        - [Text Sequence Type — `str`](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str)
        - [`math` — Mathematical functions](https://docs.python.org/3/library/math.html)
        - [`csv` — CSV File Reading and Writing](https://docs.python.org/3/library/csv.html)
        - [`os` — Miscellaneous operating system interfaces](https://docs.python.org/3/library/os.html)
        - [`os.path` — Common pathname manipulations](https://docs.python.org/3/library/os.path.html)

## Using the `csv` module

The so-called CSV (Comma Separated Values) format is the most common import and export format for spreadsheets and databases. The csv module implements methods to read and write tabular data in CSV format.

The csv module’s `reader()` and `writer()` methods read and write CSV files. You can also read and write data into dictionary form using the `DictReader()` and `DictWriter()` methods.

For more information about this built-in Python library about [CSV File Reading and Writing documentation](https://docs.python.org/3/library/csv.html).

Let's now read our `data/mydata.txt` file using the `csv` module.


```python
import csv
with open("data/mydata.txt") as f:
    reader = csv.reader(f, delimiter = " ") # default delimiter is ","
    for row in reader:
        print(row)
```

Change the `csv.reader()` by the `csv.DictReader()` and it builds up a dictionary automatically based on the column headers.


```python
with open("data/mydata.txt") as f:
    reader = csv.DictReader(f, delimiter = " ")
    for row in reader:
        print(row)
```


```python
# Write tab delimited files using the csv module
import csv

mydata = [
    ['1', 'Human', '1.076'], 
    ['2', 'Mouse', '1.202'], 
    ['3', 'Frog', '2.2362'], 
    ['4', 'Fly', '0.9853']
]

with open("csvdata.tsv", "w") as f:
    writer = csv.writer(f, delimiter='\t' )
    writer.writerow( [ "Index", "Organism", "Score" ] ) # write header
    for record in mydata:
        writer.writerow( record )

# Open the output file and print out its content
with open("csvdata.tsv") as f:
    print(f.read())
```


```python
# Write delimited files using the csv module from a list of dictionaries 
import csv

mydata = [
    {'Index': '1', 'Score': '1.076', 'Organism': 'Human'}, 
    {'Index': '2', 'Score': '1.202', 'Organism': 'Mouse'}, 
    {'Index': '3', 'Score': '2.2362', 'Organism': 'Frog'}, 
    {'Index': '4', 'Score': '0.9853', 'Organism': 'Fly'}
]

with open("csvdictdata.tsv", "w") as f:
    writer = csv.DictWriter(f, mydata[0].keys(), delimiter='\t')
    writer.writeheader() # write header

    for record in mydata:
        writer.writerow( record )

# Open the output file and print out its content
with open("csvdictdata.tsv") as f:
    print(f.read())
```

## Python file library

### [`os.path` — Common pathname manipulations](https://docs.python.org/3/library/os.path.html)

- `exists(path)` : returns whether path exists
- `isfile(path)` : returns whether path is a “regular” file (as opposed to a directory)
- `isdir(path)` : returns whether path is a directory
- `islink(path)` : returns whether path is a symbolic link
- `join(*paths)` : joins the paths together into one long path
- `dirname(path)` : returns directory containing the path
- `basename(path)` : returns the path minus the dirname(path) in front
- `split(path)` : returns (dirname(path), basename(path))

### [`os` — Miscellaneous operating system interfaces](https://docs.python.org/3/library/os.html)

- `chdir(path)` : change the current working directory to be path
- `getcwd()` : return the current working directory
- `listdir(path)` : returns a list of files/directories in the directory path
- `mkdir(path)` : create the directory path
- `rmdir(path)` : remove the directory path
- `remove(path)` : remove the file path
- `rename(src, dst)` : move the file/directory from src to dst

Building the path to your file from a list of directory and filename makes your script able to run on any platforms.


```python
import os.path
os.path.join("data", "mydata.txt")
# data/mydata.txt - Unix
# data\mydata.txt - Windows
```

Check if a file exists before opening it:


```python
import os.path
data_file = os.path.join("data", "mydata.txt")
if os.path.exists(data_file):
    print("file", data_file, "exists")
    with open(data_file) as f:
        print(f.read())
else:
    print("file", data_file, "not found!")
```

## Congratulation! You reached the end of the tutorial! 

## but there are miles to go.. [Next Step](../next%20step.md)

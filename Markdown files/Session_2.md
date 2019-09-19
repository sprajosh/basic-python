
# An introduction to Python

## Session 1.2: Collections

- [Tuples](#Tuples), [Lists](#Lists) and [Manipulating tuples and lists](#Manipulating-tuples-and-lists) | [Exercise 1.2.1](#Exercise-1.2.1)
- [String manipulations](#String-manipulations) | [Exercise 1.2.2](#Exercise-1.2.2)
- [Sets](#Sets) |
- [Dictionnaries](#Dictionnaries) |

As well as the basic data types we introduced above, very commonly you will want to store and operate on collections of values, and python has several _data structures_ that you can use to do this. The general idea is that you can place several items into a single collection and then refer to that collection as a whole. Which one you will use will depend on what problem you are trying to solve.

## Tuples

- Can contain any number of items
- Can contain different types of items
- __Cannot__ be altered once created (they are immutable)
- Items have a defined order

A tuple is created by using round brackets around the items it contains, with commas seperating the individual elements.


```python
a = (123, 54, 92) # tuple of 4 integers
b = () # empty tuple
c = ("Ala",) # tuple of a single string (note the trailing ",")
d = (2, 3, False, "Arg", None) # a tuple of mixed types

print(a)
print(b)
print(c)
print(d)
```

You can of course use variables in tuples and other data structures


```python
x = 1.2
y = -0.3
z = 0.9
t = (x, y, z)

print(t)
```

Tuples can be _packed_ and _unpacked_ with a convenient syntax. The number of variables used to unpack the tuple must match the number of elements in the tuple.


```python
t = 2, 3, 4 # tuple packing
print('t is', t)
x, y, z = t # tuple unpacking
print('x is', x)
print('y is', y)
print('z is', z)
```

## Lists

- Can contain any number of items
- Can contain different types of items
- __Can__ be altered once created (they are _mutable_)
- Items have a particular order

Lists are created with square brackets around their items:


```python
a = [1, 3, 9, 'Py', 217.213]
b = ["Python"]
c = []

print(a)
print(b)
print(c)
```

    [1, 3, 9, 'Py', 217.213]
    ['Python']
    []


Lists and tuples can contain other list and tuples, or any other type of collection:


```python
matrix = [[input(),input()], [input(),input()]]
print(matrix)
```

    r
    ff
    fd
    sd
    [['r', 'ff'], ['fd', 'sd']]


You can convert between tuples and lists with the <tt>tuple</tt> and <tt>list</tt> functions. Note that these create a new collection with the same items, and leave the original unaffected.


```python
a = (1, 4, 9, 16)     # A tuple of numbers
b = ['A','B','C','d'] # A list of characters

print(a)
print(b)

l = list(a)   # Make a list based on a tuple 
print(l)

t = tuple(b)  # Make a tuple based on a list
print(t)
```

## Manipulating tuples and lists

Once your data is in a list or tuple, python supports a number of ways you can access elements of the list and manipulate the list in useful ways, such as sorting the data.

Tuples and lists can generally be used in very similar ways.

### Index access

You can access individual elements of the collection using their _index_, note that the first element is at index 0. Negative indices count backwards from the end.


```python
t = (123, 54, 92, 87, 33)
x = [123, 54, 92, 87, 33]

print('t is', t)
print('t[0] is', t[0])
print('t[2] is', t[2])

print('x is', x)
print('x[-1] is', x[-1])
```

### Slices

You can also access a range of items, known as _slices_, from inside lists and tuples using a colon `:` to indicate the beginning and end of the slice inside the square brackets. **Note that the slice notation `[a:b]` includes positions from `a` up to _but not including_ `b`**.


```python
t = (123, 54, 92, 87, 33)
x = [123, 54, 92, 87, 33]
print('t[1:3] is', t[1:3])
print('x[2:] is', x[2:])
print('x[:-1] is', x[:-1])
```

    t[1:3] is (54, 92)
    x[2:] is [92, 87, 33]
    x[:-1] is [123, 54, 92, 87]


### `in` operator
You can check if a value is in a tuple or list with the <tt>in</tt> operator, and you can negate this with <tt>not</tt>


```python
t = (123, 54, 92, 87, 33)
x = [123, 54, 92, 87, 33]
print('123 in', x, 123 in x)
print('234 in', t, 234 in t)
print('999 not in', x, 999 not in x)
```

    123 in [123, 54, 92, 87, 33] True
    234 in (123, 54, 92, 87, 33) False
    999 not in [123, 54, 92, 87, 33] True



```python
a = [1, 2, 3, 4, 5]

a[2:]
```




    [3, 4, 5]



### `len()` and `count()` functions
You can get the length of a list or tuple with the in-built <tt>len()</tt> function, and you can count the number of particular elements contained in a list with the <tt>.count()</tt> function.


```python
t = (123, 54, 92, 87, 33)
x = [123, 54, 92, 87, 33]
print("length of t is", len(t))
print("number of 33s in x is", x.count(33))
```

    length of t is 5
    number of 33s in x is 1


### Modifying lists
You can alter lists in place, but not tuples


```python
x = [123, 54, 92, 87, 33]
print(x)
x[2] = 33
print(x)
```

    [123, 54, 92, 87, 33]
    [123, 54, 33, 87, 33]


Tuples _cannot_ be altered once they have been created, if you try to do so, you'll get an error.


```python
t = (123, 54, 92, 87, 33)
print(t)
t[1] = 4
```

    (123, 54, 92, 87, 33)



    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-1-7204a6fa6a43> in <module>()
          1 t = (123, 54, 92, 87, 33)
          2 print(t)
    ----> 3 t[1] = 4
    

    TypeError: 'tuple' object does not support item assignment


You can add elements to the end of a list with <tt>append()</tt>


```python
x = [123, 54, 92, 87, 33]
x.append(101)
print(x)
```

    [123, 54, 92, 87, 33, 101]


or insert values at a certain position with <tt>insert()</tt>, by supplying the desired position as well as the new value


```python
x = [123, 54, 92, 87, 33]
x.insert(3, 1111)
print(x)
```

    [123, 54, 92, 1111, 87, 33]


You can remove values with <tt>remove()</tt>


```python
x = [123, 54, 92, 87, 33]
x.remove(123)
print(x)
```

    [54, 92, 87, 33]


and delete values by index with <tt>del</tt>


```python
x = [123, 54, 92, 87, 33]
print(x)
del x[0]
print(x)
```

    [123, 54, 92, 87, 33]
    [54, 92, 87, 33]


It's often useful to be able to combine arrays together, which can be done with <tt>extend()</tt> (as <tt>append</tt> would add the whole list as a single element in the list)


```python
a = [1,2,3]
b = [4,5,6]
a.extend(b)
print(a)
a.append(b)
print(a)
```

    [1, 2, 3, 4, 5, 6]
    [1, 2, 3, 4, 5, 6, [4, 5, 6]]


The plus symbol <tt>+</tt> is shorthand for the extend operation when applied to lists:


```python
a = [1, 2, 3]
b = [4, 5, 6]
a = a + b
print(a)
```

    [1, 2, 3, 4, 5, 6]


Slice syntax can be used on the left hand side of an assignment operation to assign subregions of a list


```python
a = [1, 2, 3, 4, 5, 6]
a[1:3] = [9, 9, 9, 9]
print(a)
```

    [1, 9, 9, 9, 9, 4, 5, 6]


You can change the order of elements in a list


```python
a = [1, 3, 5, 4, 2]
a.reverse()
print(a)
#print(a[::2])
a.sort()
print(a)
```

    [2, 4, 5, 3, 1]
    [1, 2, 3, 4, 5]


Note that both of these change the list, if you want a sorted copy of the list while leaving the original untouched, use <tt>sorted()</tt>


```python
a = [2, 5, 7, 1]
b = sorted(a)
print(a)
print(b)
```

## String manipulations

Strings are a lot like tuples of characters, and individual characters and substrings can be accessed and manipulated using similar operations we introduced above.



```python
text = "ABCDEFGH"
print(text[0])
print(text[-2])
print(text[0:6])
print("EFG" in text)
print("ABC" in text)
print(len(text))
```

    A
    G
    ABCDEF
    True
    True
    8


Just as with tuples, trying to assign a value to an element of a string results in an error


```python
text = "ABCDEFGH"
text[0:2] = "CCC" 
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-3-6c7e51bd134e> in <module>()
          1 text = "ABCDEFGH"
    ----> 2 text[0:2] = "CCC"
    

    TypeError: 'str' object does not support item assignment


Python provides a number of useful functions that let you manipulate strings

The <tt>in</tt> operator lets you check if a substring is contained within a larger string, but it does not tell you where the substring is located. This is often useful to know and python provides the <tt>.find()</tt> method which returns the index of the first occurrence of the search string, and the <tt>.rfind()</tt> method to start searching from the end of the string.

If the search string is not found in the string both these methods return -1.


```python
string = "ABCDEDCBA"
index = string.find("CDE")
print("CDE is at position:", index)
index = string.rfind('C')
print("The last C is at position:", index)
```

    CDE is at position: 2
    The last C is at position: 6


When we are reading text from files  (which we will see later on), often there is unwanted whitespace at the start or end of the string. We can remove leading whitespace with the <tt>.lstrip()</tt> method, trailing whitespace with <tt>.rstrip()</tt>, and whitespace from both ends with <tt>.strip()</tt>.

All of these methods return a copy of the changed string, so if you want to replace the original you can assign the result of the method call to the original variable.


```python
s = "     My name is Python     "
print(len(s), s, ".")
print(len(s.rstrip()), s.rstrip(), ".")
print(len(s.lstrip()), s.lstrip(), ".")
print(len(s.strip()), s.strip(),".")
```

    27      My name is Python      .
    22      My name is Python .
    22 My name is Python      .
    17 My name is Python .


You can split a string into a list of substrings using the <tt>.split()</tt> method, supplying the delimiter as an argument to the method. If you don't supply any delimiter the method will split the string on whitespace by default (which is very often what you want!)

To split a string into its component characters you can simply _cast_ the string to a list 


```python
string = "My name is Python"
words = string.split(" ")
print(words)

letters = list(string) # a tuple of character converted into a list
print(letters)
```

    ['My', 'name', 'is', 'Python']
    ['M', 'y', ' ', 'n', 'a', 'm', 'e', ' ', 'i', 's', ' ', 'P', 'y', 't', 'h', 'o', 'n']


<tt>.split()</tt> is the counterpart to the <tt>.join()</tt> method that lets you join the elements of a list into a string only if all the elements are of type String:


```python
string = "My name is Python"
words = string.split(" ")
print(words)
print("|".join(words))
```

    ['My', 'name', 'is', 'Python']
    My|name|is|Python


We also saw earlier that the <tt>+</tt> operator lets you concatenate strings together into a larger string.

Note that this operator only works on variables of the same type. If you want to concatenate a string with an integer (or some other type), first you have to cast the integer to a string with the <tt>str()</tt> function.


```python
language = "Python"
version = 3.6
print(language + str(version))
```

    Python3.6


## Exercise 1.2.2

1. Create a string variable with your full name in it, with your first and last name (and any middle names) seperated by a space. Split the string into a list, and print out your surname.
2. Check if your surname contains the letter "E", and print out the position of this letter in the string. Try a few other letters.

### Optional exercise
- Use a format string to print out your first name and the length of your first name by looking into the python library for String formating https://docs.python.org/3/library/stdtypes.html#str.format and https://docs.python.org/3/library/string.html#formatstrings using `str.format()`

## Sets

- Sets contain unique elements, i.e. no repeats are allowed
- The elements in a set do not have an order
- Sets cannot contain elements which can be internally modified (e.g. lists and dictionaries)


```python
l = [1, 2, 3, 2, 3] # list of 5 values
s = set(l) # set of 3 unique values
print(s)
e = set() # empty set
print(e)
```

Sets are very similar to lists and tuples and you can use many of the same operators and functions, except they are **inherently unordered**, so they don't have an index, and can only contain _unique_ values, so adding a value already in the set will have no effect


```python
s = set([1, 2, 3, 2, 3])
print(s)
print("number in set:", len(s))
s.add(4)
print(s)
s.add(3)
print(s)
```

You can remove specific elements from the set.


```python
s = set([1, 2, 3, 2, 3])
print(s)
s.remove(3)
print(s)
```

You can do all the expected logical operations on sets, such as taking the union or intersection of 2 sets with the <tt>|</tt> _or_ and <tt>&</tt> _and_ operators 


```python
s1 = set([2, 4, 6, 8, 10])
s2 = set([4, 5, 6, 7])

print("Union:", s1 | s2)
print("Intersection:", s1 & s2)
```

## Dictionaries

Lists are useful in many contexts, but often we have some data that has no inherent order and that we want to access by some useful name rather than an index. For example, as a result of some experiment we may have a set of genes and corresponding expression values. We could put the expression values in a list, but then we'd have to remember which index in the list corresponded to which gene and this would quickly get complicated.

For these situations a _dictionary_ is a very useful data structure.

Dictionaries:

- Contain a mapping of keys to values (like a word and its corresponding definition in a dictionary)
- The keys of a dictionary are unique, i.e. they cannot repeat
- The values of a dictionary can be of any data type
- The keys of a dictionary cannot be an internally modifiable type (e.g. lists, but you can use tuples)
- Dictionaries do not store data in any particular order


```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton"}
print(sports)

sports['C']
```

    {'A': 'Cricket', 'B': 'Football', 'C': 'Hockey', 'D': 'Badminton'}





    'Hockey'



You can access values in a dictionary using the key inside square brackets


```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton"}
print("A represents", sports["A"])
print("G represents", sports["G"])
```

An error is triggered if a key is absent from the dictionary:


```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton"}
print("What about N?", sports["N"])
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-25-422dcfa53292> in <module>()
          1 sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton"}
    ----> 2 print("What about N?", sports["N"])
    

    KeyError: 'N'


You can access values safely with the <tt>get</tt> method, which gives back <tt>None</tt> if the key is absent and you can also supply a default values


```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton"}
print("What about N?", sports.get("N"))
print("With a default value:", sports.get("N", "asfasfasf"))
```

    What about N? None
    With a default value: asfasfasf


You can check if a key is in a dictionary with the <tt>in</tt> operator, and you can negate this with <tt>not</tt>


```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton"}
"T" in sports
```




    False




```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton"}
"Y" not in sports
```




    True



The <tt>len()</tt> function gives back the number of (key, value) pairs in the dictionary:


```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton"}
print(len(sports))
```

    4


You can introduce new entries in the dictionary by assigning a value with a new key:


```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton"}
sports['E'] = 'Kabaddi'
print(sports)
```

    {'A': 'Cricket', 'B': 'Football', 'C': 'Hockey', 'D': 'Badminton', 'E': 'Kabaddi'}


You can change the value for an existing key by reassigning it:


```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton", "E": "Kabaddi"}
sports['F'] = 'Volley Ball'
print(sports)
```

    {'A': 'Cricket', 'B': 'Football', 'C': 'Hockey', 'D': 'Badminton', 'E': 'Kabaddi', 'F': 'Volley Ball'}


You can delete entries from the dictionary:


```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton", "E": "Kabaddi", 'F': 'Volley Ball'}
del sports['F']
print(sports)
```

    {'A': 'Cricket', 'B': 'Football', 'C': 'Hockey', 'D': 'Badminton', 'E': 'Kabaddi'}


You can get a list of all the keys (in arbitrary order) using the inbuilt <tt>.keys()</tt> function


```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton", "E": "Kabaddi"}
print(list(sports.keys()))
```

    ['A', 'B', 'C', 'D', 'E']


And equivalently get a list of the values:


```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton", "E": "Kabaddi"}
print(list(sports.values()))
```

    ['Cricket', 'Football', 'Hockey', 'Badminton', 'Kabaddi']


And a list of tuples containing (key, value) pairs:


```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton", "E": "Kabaddi"}
print(list(sports.items()))
```

    [('A', 'Cricket'), ('B', 'Football'), ('C', 'Hockey'), ('D', 'Badminton'), ('E', 'Kabaddi')]


## Next Session

- Go to next session: [Session 3](Session_3.ipynb)

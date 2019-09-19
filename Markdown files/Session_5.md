
# An introduction to Python

- Python website: https://www.python.org/ 
- [Python 3 Standard Library](https://docs.python.org/3/library/index.html])

## Learning objectives

- **Basics** how to print, create variables and save Python code in files
- **List** the most common data types in Python
- **Explain** how to write conditions and loops in Python
- **Use and compare** these concepts in different code examples 
- **Propose and create** solutions using these concepts in different exercises

- **Session 2.1** - Functions
- **Session 2.2** - Modules
- **Session 2.3** - Files

## What we've learned so far

- Simple data types, Collections
- Conditional execution
- Loops
- Functions used so far...

## Collections


```python
## Tuple - immutable
example_tuple = (2, 3, 4, 5)
print('A tuple:', example_tuple)
print('First element of tuple:', example_tuple[0])
```

    A tuple: (2, 3, 4, 5)
    First element of tuple: 2



```python
## List
example_list = [2, 3, 4, 5]
print('A list:', example_list)
print('First element of list:', example_list[0])
example_list.append(12)
print('Appended list:', example_list)
example_list[0] = 45
print('Modified list:', example_list)
```

    A list: [2, 3, 4, 5]
    First element of list: 2
    Appended list: [2, 3, 4, 5, 12]
    Modified list: [45, 3, 4, 5, 12]



```python
## String - immutable, tuple of characters
text = "ABCDEFGH"
print('Here is a string:', text)
print('First character:', text[0])
print('Number of characters in text', len(text))
```

    Here is a string: ABCDEFGH
    First character: A
    Number of characters in text 8



```python
## Set - unique unordered elements
example_set = set([1,2,2,2,2,4,5,6,6,6])
print('A set:', example_set)
```

    A set: {1, 2, 4, 5, 6}



```python
## Dictionary
example_dictionary = {"A": "APPLE", 
                      "B": "BALL", 
                      "C": "CAT", 
                      "D": "DOLL"}
print('A dictionary:', example_dictionary)
print('Value associated to key C:', example_dictionary['C'])
```

    A dictionary: {'A': 'APPLE', 'B': 'BALL', 'C': 'CAT', 'D': 'DOLL'}
    Value associated to key C: CAT


## Conditional execution


```python
x = 2
print('Is 2 < 5?', x < 5)
print('Is 2 == 5?', x == 5)
print('Is 2 < 5 and 2 > 1?', (x < 5) & (x > 1))

if x == 2:
    print('x is equal to 2')
```

    Is 2 < 5? True
    Is 2 == 5? False
    Is 2 < 5 and 2 > 1? True
    x is equal to 2


## Loops


```python
example_list = ['A', 'B', 'C', 'D', 'E']

## Looping through a list
for element in example_list:
    print("The element in list is:", element)
```

    The element in list is: A
    The element in list is: B
    The element in list is: C
    The element in list is: D
    The element in list is: E


## Exercise 2.0.1

- Create a string variable with the lyrics of Imagine by John Lennon, 1971. Split into words. Print the total number of words, and the number of unique words. Calculate the frequency of each word and store the result into a dictionary. Print each unique word along with its frequency. Find the most frequent word in the song, print it with its frequency.

<center><img src="https://upload.wikimedia.org/wikipedia/en/1/1d/John_Lennon_-_Imagine_John_Lennon.jpg"/></center>


```python
lyrics = """
Imagine there's no Heaven
It's easy if you try
No Hell below us
Above us only sky

Imagine all the people
Living for today
Aaa haa

Imagine there's no countries
It isn't hard to do
Nothing to kill or die for
And no religion too

Imagine all the people
Living life in peace
Yoo hoo

You may say I'm a dreamer
But I'm not the only one
I hope someday you'll join us
And the world will be as one

Imagine no possessions
I wonder if you can
No need for greed or hunger
A brotherhood of man

Imagine all the people
Sharing all the world
Yoo hoo

You may say I'm a dreamer
But I'm not the only one
I hope someday you'll join us
And the world will live as one
"""
```

## Next session

- Go to next session: [Session 6](Session_6.ipynb)

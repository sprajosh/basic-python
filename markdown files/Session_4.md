
# An introduction to Python

## Session 1.4: Loops

- [The <tt>for</tt> loop](#The-for-loop)
- [The <tt>while</tt> loop](#The-while-loop)
- [Skipping and breaking loops](#Skipping-and-breaking-loops)
- [More looping using range and enumerate](#More-looping)
- [Filtering in loops](#Filtering-in-loops)

## Loops

When an operation needs to be repeated multiple times, for example on all of the items in a list, we 
avoid having to type (or copy and paste) repetitive code by creating a loop. There are two ways of creating loops in Python, the <tt>for</tt> loop and the <tt>while</tt> loop.

## The <tt>for</tt> loop

The for loop in Python iterates over each item in a sequence (such as a list or tuple) in the order that they appear in the sequence. What this means is that a variable (<tt>code</tt> in the below example) is set to each item from the sequence of values in turn, and each time this happens the indented block of code is executed again.


```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]

for x in numbers:
    print(x)
    #print(number, end = '-')
```

    1
    2
    3
    4
    5
    6
    7
    8
    9


A <tt>for</tt> loop can iterate over the individual characters in a string:


```python
name = 'Kochi Python'

for character in name:
    print(character)
```

    K
    o
    c
    h
    i
     
    P
    y
    t
    h
    o
    n


And also over the keys of a dictionary: 


```python
sports = {"A": "Cricket", "B": "Football", "C": "Hockey", "D": "Badminton", "E": "Kabaddi"}

for x in sports:
    print(x, sports[x])
```

    A Cricket
    B Football
    C Hockey
    D Badminton
    E Kabaddi


Any variables that are defined before the loop can be accessed from inside the loop. So for example to calculate the summation of the items in a list of values we could define the total initially to be zero and add each value to the total in the loop:


```python
total = 0
values = [1, 2, 4, 8, 16]

for v in values:
    total = total + v
    # total += v
    print(total)

print(total)
```

Naturally we can combine a <tt>for</tt> loop with an <tt>if</tt> statement, noting that we need two indentation levels, one for the outer loop and another for the conditional blocks:


```python
markList = {
    'Tintumon': 22, 
    'Dundumol': 86, 
    'Dingan': 69, 
    'Luttapi': 45
}

for person in markList:
    if markList.get(person) < 45:
        print(person, " : Failed")
        
    elif markList.get(person) > 45:
        print(person, " : Passed")
        
    else:
        print(person, ' : Just Pass' )
```

    Tintumon  : Failed
    Dundumol  : Passed
    Dingan  : Passed
    Luttapi  : Just Pass


## The <tt>while</tt> loop

In addition to the <tt>for</tt> loop that operates on a collection of items, there is a <tt>while</tt> loop that simply repeats while some statement evaluates to True and stops when it is False. Note that if the tested expression never evaluates to False then you have an “infinite loop”, which is not good.

In this example we generate a series of numbers by doubling a value after each iteration, until a limit is reached: 


```python
value = 0.25
while value < 8:
    value = value * 2
    print(value)

print("final value:", value)
```

    0.5
    1.0
    2.0
    4.0
    8.0
    final value: 8.0


Whats going on here is that the value is doubled in each iteration and once it gets to 8 the while test fails (8 is not less than 8) and that last value is preserved. Note that if the test were instead value `<= 8` then we would get one more doubling and the value would reach 16.

## Skipping and breaking loops

Python has two ways of affecting the flow of the <tt>for</tt> or <tt>while</tt> loop inside the block. The <tt>continue</tt> statement means that the rest of the code in the block is skipped for this particular item in the collection, i.e. jump to the next iteration. In this example negative numbers are left out of a summation:


```python
#Sum of positive integers in a list
values = [10, -5, 3, -1, 7]

total = 0
for v in values:
    if v < 0:
        continue # Skip this iteration   
    total += v

print(total)
```

    20


The other way of affecting a loop is with the <tt>break</tt> statement. In contrast to the <tt>continue</tt> statement, this immediately causes all looping to finish, and execution is resumed at the next statement _after_ the loop.


```python
#Print from 1 - 7
for n in range(1,10):
    if n % 8 == 0:
        break            # Quit looping at this point
    else:
        print(n)
```

    1
    2
    3
    4
    5
    6
    7


## Looping gotchas

An internal counter is used to keep track of which item is used next, and this is incremented on each iteration. When this counter has reached the length of the sequence the loop terminates. This means that if you delete the current item from the sequence, the next item will be skipped (since it gets the index of the current item which has already been treated). Likewise, if you insert an item in a sequence before the current item, the current item will be treated again the next time through the loop. This can lead to nasty bugs that can be avoided by making a temporary copy using a slice of the whole sequence.

<div class="alert-warning">
**When looping, never modify the collection!** Always create a copy of it first.
</div>

## More looping

### Using range

If you would like to iterate over a numeric sequence then this is possible by combining the `range()` function and a for loop.


```python
print(list(range(10)))

print(list(range(5, 10)))

print(list(range(0, 10, 3)))

print(list(range(7, 2, -1)))
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    [5, 6, 7, 8, 9]
    [0, 3, 6, 9]
    [7, 6, 5, 4, 3]


### Looping through ranges 


```python
for x in range(8):
    print(x*x)
```

    0
    1
    4
    9
    16
    25
    36
    49



```python
squares = []
for x in range(8):
    s = x*x
    squares.append(s)
    
print(squares)
```

    [0, 1, 4, 9, 16, 25, 36, 49]


#### Looping through list ndices


```python
alphabets = ['A', 'B', 'C', 'D', 'E']

for index in range(len(alphabets)):
    print(index, alphabets[index])
```

    0 A
    1 B
    2 C
    3 D
    4 E


#### Looping through indices for two lists


```python
alphabets = ['A', 'B', 'C', 'D', 'E']
more_alphabets = ['F', 'G', 'H', 'I', 'J']

for index in range(len(alphabets)):
    print(index, alphabets[index], more_alphabets[index])
```

    0 A F
    1 B G
    2 C H
    3 D I
    4 E J


### Using enumerate

Given a sequence, `enumerate()` allows you to iterate over the sequence generating a tuple containing each value along with a corresponding index.


```python
letters = ['A','B','C','D']
for index, letter in enumerate(letters):
    print(index, letter)
```

    0 A
    1 B
    2 C
    3 D



```python
numbered_letters = list(enumerate(letters))
print(numbered_letters)
```

    [(0, 'A'), (1, 'B'), (2, 'C'), (3, 'D')]


## Filtering in loops


```python
city_pops = {
    'London': 8200000,
    'Cambridge': 130000,
    'Edinburgh': 420000,
    'Glasgow': 1200000
}

big_cities = []
for city in city_pops:
    if city_pops[city] >= 1000000:
         big_cities.append(city)

print(big_cities)
```

    ['London', 'Glasgow']



```python
total = 0
for city in city_pops:
    total += city_pops[city]
print("total population:", total)
```

    total population: 9950000



```python
pops = list(city_pops.values())
print("total population:", sum(pops))
```

    total population: 9950000


## Next session

- Go to next session: [Session 5](Session_5.md)


# An introduction to Python

## Session 1:

- [Printing values](#Printing-values)
- [Using variables](#Using-variables)
- [Simple data types](#Simple-data-types): [Booleans](#Booleans), [Integers](#Integers), [Floating point numbers](#Floating-point-numbers), and [Strings](#Strings)
- [Comments](#Comments)
- [Exercises 1.1.1](#Exercises-1.1.1)
- [Arithmetic](#Arithmetic)
- [Exercises 1.1.2](#Exercises-1.1.2)

## My Mantra of how to learn a new programming language

- Learn Data Types
- Learn Control Structures
- Practice

## Printing values

The first bit of python syntax we're going to learn is the <tt>print</tt> statement. This command lets us print messages to the user, and also to see what Python thinks is the value of some expression (very useful when debugging your programs).

We will go into details later on, but for now just note that to print some text you have to enclose it in  "quotation marks". 

We will go into detail on the arithmetic operations supported in python shortly, but you can try exploring python's calculating abilities.


```python
print (sys.version)
```

    3.6.2 |Anaconda, Inc.| (default, Sep 30 2017, 18:42:57) 
    [GCC 7.2.0]



```python
print("Hello from python!")
```

    Hello from python!



```python
print(34)
```

    34



```python
print(2 + 3)
```

    5


You can print  multiple expressions you need to seperate them with commas. Python will insert a space between each element, and a newline at the end of the message (though you can suppress this behaviour by leaving a trailing comma at the end of the command).


```python
print("The answer:", 42)
```

    The answer: 42


## Using variables

In the <tt>print</tt> commands above we have directly operated on values such as text strings and numbers. When programming we will typically want to deal with rather more complex expressions where it is useful to be able to assign a name to an expression, especially if we are trying to deal with multiple values at the same time.

We can give a name to a value using _variables_, the name is apt because the values stored in a variable can _vary_. Unlike some other languages, the type of value assigned to a variable can also change (this is one of the reasons why python is known as a _dynamic_ language).

A variable can be assigned to a simple value...


```python
x = 3
print(x)
```

    3


... or the outcome of a more complex expression.


```python
x = 2 + 2
print(x)
```

    4


A variable can be called whatever you like (as long as it starts with a character, it does not contain space and is meaningful) and you assign a value to a variable with the **`=` operator**. Note that this is different to mathematical equality (which we will come to later...)

You can <tt>print</tt> a variable to see what python thinks its current value is.


```python
name = "Iron man"
print(name, "is his name")
```

    Iron man is his name


In the interactive interpreter you don't have to <tt>print</tt> everything, if you type a variable name (or just a value), the interpreter will automatically print out what python thinks the value is. Note though that this is not the case if your code is in a file.


```python
3 + 4
```




    7




```python
x = 5
3 * x
```




    15



Variables can be used on the right hand side of an assignment as well, in which case they will be evaluated before the value is assigned to the variable on the left hand side.


```python
x = 5
y = x * 3
print(y)
```

    15


or just `y` in the interpreter and in Jupyter notebook


```python
y
```




    15



You can use the current value of a variable itself in an assignment


```python
y = y + 1
y
```




    16



In fact this is such a common idiom that there are special operators that will do this implicitly (more on these later)


```python
y += 1
y
```




    17



## Simple data types

Python (and computers in general) treats different types of data differently. Python has 5 main basic data types. Types are useful to constrain some operations to a certain category of variables. For example it doesn't really make sense to try to divide a string.

We will see some examples of these in use shortly, but for now let's see all of the basic types available in python.

### Booleans

Boolean values represent truth or falsehood, as used in logical operations, for example. Not surprisingly, there are only two values, and in Python they are called <tt>True</tt> and <tt>False</tt>.


```python
a = True
b = False
print(a, b)

x = 10 < 5
print(x)
```

    True False
    False


### Integers

Integers represent whole numbers, as you would use when counting items, and can be positive or negative.


```python
i = -7
j = 123
print(i, j)
```

    -7 123


### Floating point numbers

Floating point numbers, often simply referred to as <tt>float</tt>s, are numbers expressed in the decimal system, i.e. 2.1, 999.998, -0.000004 etc. The value 2.0 would also be interpreted as a floating point number, but the value 2, without the decimal point will not; it will be interpreted as an integer.


```python
x = 3.14159
y = -42.3
print(x * y)
```

    -132.889257


Floating point numbers can also carry an <tt>e</tt> suffix that states which power of ten they operate at.


```python
k = 1.5e3
l = 3e-2
print(k)
print(l)
```

    1500.0
    0.03


### Strings

Strings represent text, i.e. "strings" of characters. They can be delimited by single quotes <tt>‘</tt> or double quotes <tt>“</tt>, but you have to use the same delimiter at both ends. Unlike some programming languages, such as Perl, there is no difference between the two types of quote, although using one type does allow the other type to appear inside the string as a regular character.

Normally a python statement ends at the end of the line, but if you want to type a string over several lines you can enclose it in triple quotation marks.


```python
s = "String with double quotes"
t = 'String with single quotes'
u = "It's a string with apostrophes"
"""A string that extends
over multiple lines"""
```




    'A string that extends\nover multiple lines'



### The <tt>None</tt> object

The None object is special built-in value which can be thought of as **representing nothingness or that something is undefined**. For example, it can be used to indicate that a variable exists, but has not yet been set to anything specific.


```python
z = None
print(z)
```

    None


### Object type

You can check what type python thinks an expression is with the <tt>type</tt> function, which you can call with the name <tt>type</tt> immediately followed by parentheses enclosing the expression you want to check (either a variable or a value), e.g. <tt>type(3)</tt>. (This is the general form for calling functions, we'll see lots more examples of functions later...)


```python
a = True
print(a, "is of", type(a))
```

    True is of <class 'bool'>



```python
i = -7
print(i, "is of", type(i))
```

    -7 is of <class 'int'>



```python
x = 12.7893
print(x, "is of", type(x))
```

    12.7893 is of <class 'float'>



```python
s = "Workshop"
print(s, "is of", type(s))
```

    Workshop is of <class 'str'>



```python
z = None
print(z, "is of", type(z))
```

    None is of <class 'NoneType'>


## Comments

When you are writing a program it is often convenient to annotate your code to remind you what you were (intending) it to do. In programming these annotations are known as _comments_. You can include a comment in python by prefixing some text with a <tt>#</tt> character. All text following the <tt>#</tt> will then be ignored by the interpreter. You can start a comment on its own line, or you can include it at the end of a line of code.

It is also often useful to temporarily remove some code from a script without deleting it. This is known as _commenting out_ some code.


```python
print("Hi") # this will be ignored
# as will this
print("Bye")
# print "Never seen"
```

## Exercises 1.1.1

To start the Python interpreter, open a terminal window, type the command `python`, then enter Python commands after the prompt `>>>` and press `Enter` when you're done. 

Python will run the code you typed, and might display some output on the line below, before leaving you with another prompt which looks like `>>>`.

If you want to exit the interactive interpreter you can type the command `quit()` or type `Ctrl-D`.

In the interpreter:

1. Create a variable and assign it the string value of your first name, assign your age to another variable (you are free to lie!), print out a message saying how old you are
2. Use the addition operator to add 10 to your age and print out a message saying how old you will be in 10 years time

## Arithmetic

Python supports all the standard arithmetical operations on numerical types, and mostly uses a similar syntax to several other computer languages:


```python
x = 4.5
y = 2

print('x = ', x, 'y = ', y)
print('addition x + y =', x + y) 
print('subtraction x - y =', x - y) 
print('multiplication x * y =', x * y) 
print('division x / y =', x / y) 
```

    x =  4.5 y =  2
    addition x + y = 6.5
    subtraction x - y = 2.5
    multiplication x * y = 9.0
    division x / y = 2.25



```python
x = 4.5
y = 2

print('x = ', x, 'y = ', y)
print('division x / y =', x / y)
print('floored division x // y =', x // y)
print(type(x//y))
print('modulus (remainder of x/y) x % y =', x % y) 
print('exponentiation x ** y =', 10 ** 2)
```

    x =  4.5 y =  2
    division x / y = 2.25
    floored division x // y = 2.0
    <class 'float'>
    modulus (remainder of x/y) x % y = 0.5
    exponentiation x ** y = 100


As usual in maths, division and multiplication have higher precedence than addition and subtraction, but arithmetic expressions can be grouped using parentheses to override the default precedence


```python
x = 13
y = 5

print('x * (2 + y) =', x * (2 + y))
print('(x * 2) + y =', (x * 2) + y)
print('x * 2 + y =', x * 2 + y)
```

You can mix (some) types in arithmetic expressions and python will apply rules as to the type of the result



```python
int(13 + 5.0)
```




    18



You can force python to use a particular type by converting an expression explicitly, using helpful named functions: <tt>float</tt>, <tt>int</tt>, <tt>str</tt> etc.


```python
float(3) + float(7)
```




    10.0




```python
int(3.14159) + 1

+1+1
```




    2



The addition operator `+` allows you also to concatenate strings together.


```python
print('number' + str(3))
```

    number3


Division in Python 2 sometimes trips up new (and experienced!) programmers. If you divide 2 integers you will only get an integer result. If you want a floating point result you should explicitly cast at least one of the arguments to a <tt>float</tt>.


```python
print("3/4 =", 3/4)
print("3.0/4 =", 3.0/4)
print("float(3)/4 =", float(3)/4)
```

    3/4 = 0.75
    3.0/4 = 0.75
    float(3)/4 = 0.75


There are a few shortcut assignment statements to make modifying variables directly faster to type


```python
x = 3
x += 1 # equivalent to x = x + 1
x
```




    4




```python
x = 2
y = 10
y *= x
y
```




    20



These shortcut operators are available for all arithmetic and logical operators.

## Exercises 1.1.2

In the interpreter:

1. Assign numerical values to 2 variables, calculate the mean of these two variables and store the result in another variable. Print out the result to the screen.

## Next Session

[Go to next session](Session_2.md)

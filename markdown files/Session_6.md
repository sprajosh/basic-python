
# An introduction to Python

## Session 2.1: Functions

- [Function definition syntax](#Function-definition-syntax)
- [Excercises 2.1.1](#Excercises-2.1.1)
- [Return value](#Return-value)
- [Exercises 2.1.2](#Exercises-2.1.2)
- [Function arguments](#Function-arguments)
- [Exercises 2.1.3](#Exercises-2.1.3)
- [Variable scope](#Variable-scope)

## Function basics

We have already seen a number of functions built into python that let us do useful things to strings, collections and numbers etc. For example `print()` or `len()` which is passed some kind of sequence object and returns the length of the sequence.

This is the general form of a function; it takes some input _arguments_ and returns some output based on the supplied arguments.

The arguments to a function, if any, are supplied in parentheses and the result of the function _call_ is the result of evaluating the function.



```python
x = abs(-3.0)
print(x)

l = len("ABCDEF")
print(l)
```

    3.0
    6


As well as using python's built in functions, you can write your own. Functions are a nice way to **encapsulate some code that you want to reuse** elsewhere in your program, rather than repeating the same bit of code multiple times. They also provide a way to name some coherent block of code and allow you to structure a complex program.

## Function definition syntax

Functions are defined in Python using the `def` keyword followed by the name of the function. If your function takes some arguments (input data) then you can name these in parentheses after the function name. If your function does not take any arguments you still need some empty parentheses. Here we define a simple function named `sayHello` that prints a line of text to the screen:


```python
def sayHello():
    print('Hello world!')
    
sayHello()
```

    Hello world!


Note that the code block for the function (just a single print line in this case) is indented relative to the `def`. The above definition just decalares the function in an abstract way and nothing will be printed when the definition is made. To actually use a function you need to invoke it (call it) by using its name and a pair of round parentheses:


```python
sayHello() # Call the function to print 'Hello world'
```

If required, a function may be written so it accepts input. Here we specify a variable called `name` in the brackets of the function definition and this variable is then used by the function. Although the input variable is referred to inside the function the variable does not represent any particular value. It only takes a value if the function is actually used in context.


```python
def sayHello(name):
    print('Hello', name)
```

When we call (invoke) this function we specify a specific value for the input. Here we pass in the value `User`, so the name variable takes that value and uses it to print a message, as defined in the function. 


```python
sayHello('User')  # Prints 'Hello User'
```

When we call the function again with a different input value we naturally get a different message. Here we also illustrate that the input value can also be passed-in as a variable (text in this case).


```python
text = 'Mary'
sayHello(text)     # Prints 'Hello Mary'
```

A function may also generate output that is passed back or returned to the program at the point at which the function was called. For example here we define a function to do a simple calculation of the square of input (`x`) to create an output (`y`):


```python
def square(x):
  y = x*x
  return y
```

Once the `return` statement is reached the operation of the function will end, and anything on the return line will be passed back as output. Here we call the function on an input number and catch the output value as result. Notice how the names of the variables used inside the function definition are separate from any variable names we may choose to use when calling the function.
  


```python
number = 7
result = square(number) # Call the square() function which returns a result
print(result)           # Prints: 49
```

The function `square` can be used from now on anywhere in your program as many times as required on any (numeric) input values we like.


```python
print(square(1.2e-3))   # Prints: 1.4399999999999998e-06
```

A function can accept multiple input values, otherwise known as arguments. These are separated by commas inside the brackets of the function definition. Here we define a function that takes two arguments and performs a calculation on both, before sending back the result.



```python
def calcFunc(x, y):
  z = x*x + y*y
  return z


result = calcFunc(1.414, 2.0)
print(result)  #  5.999396
```

Note that this function does not check that x and y are valid forms of input. For the function to work properly we assume they are numbers. Depending on how this function is going to be used, appropriate checks could be added.

Functions can be arbitrarily long and can peform very complex operations. However, to make a function reusable, it is often better to assign it a single responsibility and a descriptive name.
Let's define now a function to calculate the [Euclidean distance](https://en.wikipedia.org/wiki/Euclidean_distance) between two vectors:


```python
def calcDistance(vec1, vec2):    
    dist = 0
    for i in range(len(vec1)):
        delta = vec1[i] - vec2[i]
        dist += delta*delta
    dist = dist**(1/2) # square-root
    return dist
```

For the record, the [prefered way to calcule a square-root](https://docs.python.org/3/library/math.html#math.sqrt) is by using the built-in function `sqrt()` from the `math` library:
```python
import math
math.sqrt(x)
```

Let's experiment a little with our function.


```python
w1 = ( 23.1, 17.8, -5.6 )
w2 = ( 8.4, 15.9, 7.7 )
calcDistance( w1, w2 )
```

Note that the function is general and handles any two vectors (irrespective of their representation) as long as their dimensions are compatible:


```python
calcDistance( ( 1, 2 ), ( 3, 4 ) ) # dimension: 2
```


```python
calcDistance( [ 1, 2 ], [ 3, 4 ] ) # vectors represented as lists
```


```python
calcDistance( ( 1, 2 ), [ 3, 4 ] ) # mixed representation
```

## Return value

There can be more than one `return` statement in a function, although typically there is only one, at the bottom. Consider the following function to get some text to say whether a number is positive or negative. It has three return statements: the first two return statements pass back text strings but the last, which would be reached if the input value were zero, has no explicit return value and thus passes back the Python `None` object. Any function code after this final return is ignored. 
The `return` keyword immediately exits the function, and no more of the code in that function will be run once the function has returned (as program flow will be returned to the call site)


```python
def getSign(value):
    
    if value > 0:
        return "Positive"
    
    elif value < 0:
        return "Negative"
    
    return # implicit 'None'

    print("Hello world") # execution does not reach this line
    
print("getSign( 33.6 ):", getSign( 33.6 ))
print("getSign( -7 ):", getSign( -7 ))
print("getSign( 0 ):", getSign( 0 ))
```

    getSign( 33.6 ): Positive
    getSign( -7 ): Negative
    getSign( 0 ): None


All of the examples of functions so far have returned only single values, however it is possible to pass back more than one value via the `return` statement. In the following example we define a function that takes two arguments and passes back three values. The return values are really passed back inside a single tuple, which can be caught as a single collection of values. 


```python
def myFunction(value1, value2):
    
    total = value1 + value2
    difference = value1 - value2
    product = value1 * value2
    
    return total, difference, product

values = myFunction( 3, 7 )  # Grab output as a whole tuple
print("Results as a tuple:", values)

x, y, z = myFunction( 3, 7 ) # Unpack tuple to grab individual values
print("x:", x)
print("y:", y)
print("z:", z)
```

## Function arguments

### Mandatory arguments

The arguments we have passed to functions so far have all been _mandatory_, if we do not supply them or if supply the wrong number of arguments python will throw an error also called an exception:


```python
def square(number):
    # one mandatory argument
    y = number*number
    return y
```


```python
square(2)
```

**Mandatory arguments are assumed to come in the same order as the arguments in the function definition**, but you can also opt to specify the arguments using the argument names as _keywords_, supplying the values corresponding to each keyword with a `=` sign.


```python
square(number=3)
```


```python
def repeat(seq, n):
    # two mandatory arguments
    result = ''
    for i in range(0,n):
        result += seq
    return result

print(repeat("abc", 3))
print(repeat(n=4, seq="XYZ"))
```

    abcabcabc
    XYZXYZXYZXYZ


<div class="alert-warning">**NOTE** Unnamed (positional) arguments must come before named arguments, even if they look to be in the right order.</div>


```python
print(repeat(seq="LMN", n=3))
```

    LMNLMNLMN


### Arguments with default values
Sometimes it is useful to give some arguments a default value that the caller can override, but which will be used if the caller does not supply a value for this argument. We can do this by assigning some value to the named argument with the `=` operator in the function definition.


```python
def runSimulation(nsteps=1000):
    print("Running simulation for", nsteps, "steps")

runSimulation(500)
runSimulation()
```

    Running simulation for 500 steps
    Running simulation for 1000 steps


<div class="alert-warning">**CAVEAT**: default arguments are defined once and keep their state between calls. This can be a problem for *mutable* objects:</div>


```python
def myFunction(parameters=[]):
    parameters.append( 100 )
    print(parameters)
    
myFunction()
myFunction()
myFunction()
myFunction([])
myFunction([])
myFunction([])
```

    [100]
    [100, 100]
    [100, 100, 100]
    [100]
    [100]
    [100]


... or avoid modifying *mutable* default arguments.


```python
def myFunction(parameters):
    # one mandatory argument without default value
    parameters.append( 100 )
    print(parameters)
    
my_list = []
myFunction(my_list)
myFunction(my_list)
myFunction(my_list)
my_new_list = []
myFunction(my_new_list)
```

### Position of mandatory arguments
Arrange function arguments so that *mandatory* arguments come first:


```python
def runSimulation(initialTemperature, nsteps=1000):
    # one mandatory argument followed by one with default value
    print("Running simulation starting at", initialTemperature, "K and doing", nsteps, "steps")
    
runSimulation(300, 500)
runSimulation(300)
```

As before, no positional argument can appear after a keyword argument, and all required arguments must still be provided.


```python
runSimulation( nsteps=100, initialTemperature=300 )
```


```python
runSimulation( initialTemperature=300 )
```


```python
runSimulation( nsteps=100 ) # Error: missing required argument 'initialTemperature'
```


```python
runSimulation( nsteps=100, 300 ) # Error: positional argument follows keyword argument
```

Keyword names must naturally match to those declared:


```python
runSimulation( initialTemperature=300, numSteps=100 ) # Error: unexpected keyword argument 'numSteps'
```

Function cannot be defined with mandatory arguments after default ones.


```python
def badFunction(nsteps=1000, initialTemperature):
    pass
```

## Variable scope

Every variable in python has a _scope_ in which it is defined. Variables defined at the outermost level are known as _globals_ (although typically only for the current module). In contrast, variables defined within a function are local, and cannot be accessed from the outside.


```python
def mathFunction(x, y):
    math_func_result = ( x + y ) * ( x - y )
    return math_func_result
```


```python
answer = mathFunction( 4, 7 )
print(answer)
```


```python
answer = mathFunction( 4, 7 )
print(math_func_result)
```

Generally, variables defined in an outer scope are also visible in functions, but you should be careful manipulating them as this can lead to confusing code and python will actually raise an error if you try to change the value of a global variable inside a function. Instead it is a good idea to avoid using global variables and, for example, to pass any necessary variables as parameters to your functions.


```python
counter = 1
def increment(): 
    print(counter)
    counter += 1

increment()
print(counter)
```

If you really want to do this, there is a way round this using the `global` statement. Any variable which is changed or created inside of a function is local, if it hasn't been declared as a global variable. To tell Python that we want to use the global variable, we have to explicitly state this by using the keyword `global`.


```python
counter = 1
def increment(): 
    global counter
    print(counter)
    counter += 1

increment()
print(counter)
```

<div class="alert-warning">**NOTE** It is normally better to avoid global variables and passing through arguments to functions instead.</div>


```python
def increment(counter): 
    return counter + 1

counter = 0
counter = increment( counter ) 
print(counter)
```

## Next session

- Go to next session: [Session 7](Session_7.md)

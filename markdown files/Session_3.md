
# An introduction to Python

## Session 1.3: Conditional execution

- [Code blocks](#Code-blocks)
- [Conditional execution](#Conditional-execution)
- [Exercises 1.3.1](#Exercises-1.3.1)

## Program control and logic

A program will normally run by executing the stated commands, one after the other in sequential order. Frequently however, you will need the program to deviate from this. There are several ways of diverting from the line-by-line paradigm:

- With conditional statements. Here you can check if some statement or expression is true, and if it is then you continue on with the following block of code, otherwise you might skip it or execute a different bit of code.

- By performing repetitive loops through the same block of code, where each time through the loop different values may be used for the variables.

- Through the use of functions (subroutines) where the program’s execution jumps from a particular line of code to an entirely different spot, even in a different file or module, to do a task before (usually) jumping back again. Functions are covered in the next session, so we will not discuss them yet.

- By checking if an error or exception occurs, i.e. something illegal has happened, and executing different blocks of code accordingly

## Code blocks

With all of the means by which Python code execution can jump about we naturally need to be aware of the boundaries of the block of code we jump into, so that it is clear at what point the job is done, and program execution can jump back again. In essence it is required that the end of a function, loop or conditional statement be defined, so that we know the bounds of their respective code blocks.

Python uses indentation to show which statements are in a block of code, other languages use specific `begin` and `end` statements or curly braces `{}`. It doesn't matter how much indentation you use, but the whole block must be consistent, i.e., if the first statement is indented by four spaces, the rest of the block must be indented by the same amount. The Python style guide recommends using 4-space indentation. Use spaces, rather than tabs, since different editors display tab characters with different widths.

The use of indentation to delineate code blocks is illustrated in an abstract manner in the following scheme: 

Statement 1:

    Command A – in the block of statement 1
    Command B – in the block of statement 1
  
    Statement 2:
        Command C – in the block of statement 2
        Command D – in the block of statement 2
  
    Command E – back in the block of statement 1

Command F – outside all statement blocks


## Conditional execution

### The <tt>if</tt> statement

A conditional <tt>if</tt> statement is used to specify that some block of code should only be executed if some associated test is upheld; a conditional expression evaluates to <tt>True</tt>. This might also involve subsidiary checks using the <tt>elif</tt> statement to use an alternative block if the previous expression turns out to be False. There can even be a final <tt>else</tt> statement to do something if none of the checks are passed. 

The following uses statements that test whether a number is less than zero, greater than zero or otherwise equal to zero and will print out a different message in each case:


```python
x = -3

if x > 0:
    print("Value is positive")

elif x < 0:
    print("Value is negative")

else:
    print("Value is zero")
```

    Value is negative


The general form of writing out such combined conditional statements is as follows:

<pre>
if conditionalExpression1:
    # codeBlock1

elif conditionalExpression2:
    # codeBlock2

elif conditionalExpressionN:
    # codeBlockN
    +any number of additional elif statements, then finally:

else:
    # codeBlockE
</pre>


The <tt>elif</tt> block is optional, and we can use as many as we like. The <tt>else</tt> block is also optional, so will only have the <tt>if</tt> statement, which is a fairly common situation. It is often good practice to include <tt>else</tt> where possible though, so that you always catch cases that do not pass, otherwise values might go unnoticed, which might not be the desired behaviour.

Placeholders are needed for “empty” code blocks:


```python
name = "luttapi"
mark = 30

if mark < 45:
    print(name, "has failed in the exam")
        
elif geneExpression > 0:
    print(name, "has passed in the exam")
        
else:
    pass
```

    luttapi has failed in the exam


For very simple conditional checks, you can write the `if` statement on a single line as a single expression, and the result will be the expression before the `if` if the condition is true or the expression after the `else` otherwise.




```python
x = 11

if x < 10:
    s = "Yes"
else:
    s = "No"
print(s)

# Could also be written onto one line
s = "Yes" if x < 10 else "No"
print(s)
```

### Comparisons and truth

With conditional execution the question naturally arises as to which expressions are deemed to be true and which false. For the python boolean values <tt>True</tt> and <tt>False</tt> the answer is (hopefully) obvious. Also, the logical states of truth and falsehood that result from conditional checks like “Is x greater than 5?” or “Is y in this list?” are also clear. When comparing values Python has the standard comparison (or relational) operators, some of which we have already seen:

|Operator |	Description |	Example |
|---------|-------------|-----------|
|`==`  |	    equality |	1 == 2 # False |
|`!=`  |	    non equality |	1 != 2 # True |
| `<`  |	    less than |	1 < 2 # True |
| `<=` |	    equal or less than |	2 <= 2 # True |
| `>`  |	    greater then |	1 > 2 # False |
| `>=` |	    equal or greater than |	1 >= 1 # True |

It is notable that comparison operations can be combined, for example to check if a value is within a range.


```python
x = 5

#if x > 0 and x < 10:
if 0 < x < 10: #is also possible
    print("In range A")
else:
    print("Not in range")
    
#elif x < 0 or x > 10:
#    print("In range B")
```

    In range A


Python has two additional comparison operators <tt>is</tt> and <tt>is not</tt>. These compare whether two objects are the same object, whereas <tt>==</tt> and <tt>!=</tt> compare whether values are the same.

As an example in Python:


```python
x = [123, 54, 92, 87, 33]
y = x[:] # y is a copy of x
z = x
print(x)
print("Are values of y and x the same?", y == x)
print("Are objects y and x the same?", y is x)
print("Are values of z and x the same?", z == x)
print("Are objects z and x the same?", z is x)
# Let's change x
x[1] = 23
print(x)
print("Are values of y and x the same?", y == x)
print("Are objects y and x the same?", y is x)
print("Are values of z and x the same?", z == x)
print("Are objects z and x the same?", z is x)
```

In Python even expressions that do not involve an obvious boolean value can be assigned a status of "truthfulness";  the value of an item itself can be forced to be considered as either True or False inside an if statement. For the Python built-in types discussed in this chapter the following are deemed to be False in such a context:

| False value | Description | 
|-------------|-------------|
| `None` |	numeric equality |
| `False` |	False boolean |
| `0`	| 0 integer |
| `0.0` |	0.0 floating point |
| `""` |	empty string |
| `()` |	empty tuple |
| `[]` |	empty list |
| `{}` |	empty dictonary |
| `set()` |	empty set |

And everything else is deemed to be True in a conditional context.


```python
x = ''      # An empty string
y = ['a']   # A list with one item

if x:
    print("x is true")
else: 
    print("x is false")     

if y:
    print("y is true")
else:
    print("y is false")
```

## Exercises 1.3.1

Create a `if..elif..else` block that will compare a variable containing your age to another variable containing another person's age and print a statement which says if you are younger, older or the same age as that person.

## Next session

- Go to next session: [Session 4](Session_4.md)

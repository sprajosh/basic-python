
# An introduction to Python

## Session 2.2: Modules
- [Modules](#Modules)
- [Be creative and create a module for what you love](#Create)

## Modules

So far we have been writing Python code in files as executable scripts without knowning that they are also modules from which we are able to call the different functions defined in them.

A module is a file containing Python definitions and statements. The file name is the module name with the suffix .py appended. Create a file called `my_first_module.py` in the current directory with the following contents:


```python
def say_hello(user):
    print('hello', user, '!')
```

Now enter the Python interpreter from the directory you've created `my_first_module.py` file and import the `say_hello` function from this module with the following command:

```bash
python3
Python 3.5.2 (default, Jun 30 2016, 18:10:25) 
[GCC 4.2.1 Compatible Apple LLVM 7.0.2 (clang-700.1.81)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from my_first_module import say_hello
>>> say_hello('Anne')
hello Anne !
>>> 
```

There is one module already stored in the course directory called `my_first_module.py`, if you wish to import it into this notebook, below is what you need to do. If you wish to edit this file and change the code or add another function, you will have to restart the notebook to have these changes taken into account using the restart the kernel button in the menu bar.


```python
from my_first_module import say_hello
say_hello('Anne')
```

A module can contain executable statements as well as function definitions. These statements are intended to initialize the module. They are executed only the first time the module name is encountered in an import statement. 
They are also run if the file is executed as a script.

Do comment out these executable statements if you do not wish to have them executed when importing your module.

For more information about modules, https://docs.python.org/3/tutorial/modules.html.

## Create 

Now that you know functions, lists, dictionaries, loops and a lot more why don't you try to build something on your own.

Maybe a module with some mathematical functions.

I'll leave this part to you!

Good luck!

## Next session

- Go to next session: [Session 8](Session_8.md)

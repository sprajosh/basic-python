
# An introduction to Python

## Learning objectives
- **Basics** how to print, create variables and save Python code in files
- **List** the most common data types in Python
- **Explain** how to write conditions and loops in Python
- **Use and compare** these concepts in different code examples 
- **Propose and create** solutions using these concepts in different exercises

## Course materials

- All course materiel is available on [GitHub](https://github.com/sprajosh/basic-python)
- Follow along with the example code as you go through the material, and attempt the exercises to practice what you’ve learned
- Questions are welcome at any point!
- If you have specific projects/problems you like to use Python for we are happy to (try to) help.


## What is *Python*?

- Python is a *dynamic, interpreted* general purpose programming language initially created by Guido van Rossum in 1991
- It is a powerful language that supports several popular programming paradigms:
    - procedural
    - object-oriented
    - functional
- Python is widely used in bioinformatics and scientific computing, as well as many other fields and in industry
- Python is available on all popular operating systems
    - Macs
    - Windows
    - Linux

## The Python programming language

- Python is considered to come with "batteries included" and the <a href="https://docs.python.org/3.5/library/">standard library</a> (some of which we will see in this course) provides built-in support for lots of common tasks:
    - numerical & mathematical functions 
    - interacting with files and the operating system
    - ...

- There is also a wide range of external libraries for areas not covered in the standard library, such as [Pandas](http://pandas.pydata.org/) the Python Data Analysis Library

## Getting started

- Python is an *interpreted* language, this means that your computer does not run Python code natively, but instead we run our code using the Python interpreter
- There are three ways in which you can run Python code:
    - Directly typing **commands into the interpreter**: *Good for experimenting with the language, and for some interactive work*
    - Using a **Jupyter notebook**: *Great for experimenting with the language, and for sharing and learning*
    - Typing code **into a file** and then telling the interpreter to run the code from this file: *Good for larger programs, and when you want to run the same code repeatedly*


## How to start the Python interpreter?

- How you start the interpreter will depend on which operating system you are using, but on a Mac or Linux machine you should start a terminal and then just type the command `python3`
- This will print out some information about your installation of python and then leave you with a command prompt which looks like `>>>` 
- You can then type commands and press `Enter` when you're done. Python will run the code you typed, and might display some output on the line below, before leaving you with another prompt.
- If you want to exit the interactive interpreter you can type the command `quit()` or type `Ctrl-D`

## The terminal

We will see later how to save code in a file and run it.
<center><img src="img/terminal.png"></center>

## What is a Jupyter notebook?

<center><img src="img/Jupyter.svg"></center>

- The [Jupyter Notebook](http://jupyter.org/) is a web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text. 

- Jupyter provides a rich architecture for interactive data science and scientific computing with: 
    - Over 40 programming languages such as Python, R, Julia and Scala.
    - A browser-based notebook with support for code, rich text, math expressions, plots and other rich media.
    - Support for interactive data visualization.
    - Easy to use tools for parallel computing.

## How to install Jupyter on your own computer?




<center><img src="img/Jupyter.svg"></center>

- [See Installing Jupyter Notebook](https://jupyter.readthedocs.io/en/latest/install.html)

- For new users, we recommend [installing Anaconda](https://www.continuum.io/downloads). Anaconda conveniently installs Python, the Jupyter Notebook, and other commonly used packages for scientific computing and data science.

- Start the notebook server from the command line:
```
jupyter-notebook
```
- You should see the notebook home page open in your web browser.


## How to run python in a Jupyter notebook?


<center><img src="img/Jupyter.svg"></center>

- See [Jupyter Notebook Basics](http://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)


- Go to first session: [Session 1](Session_1.ipynb)

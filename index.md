#Python Pyzza worksheet

##Task 1 - Why Python?

* one of the top two languages in the world, javascript for the web 'front end', python for everything else (almost). 
  * it is used by NASA, Google, Gimp, Minecraft, and Microsoft Office. 
* my project has a million lines of Ada & C, and 3 million lines of Python to prove it!

**Python can be run from the command line, from an desktop IDE, or from an online IDE** 

It is useful to try all of them to find out which you prefer.

**Start a command line prompt using ```cmd```**

* You can find out the version of python by typing ```python --version```.
  * 2.7.x means you have Python 2 installed
  * 3.5.x means you have Python 3 installed

**Type ```python``` to give the ```>>>``` prompt**

* Python is now running!


##Task 2 - Batteries included

**Everything in Python is an ```object```, with a uniform interface.**

Which means everything you make comes with functions built in, and anything you might like to try probably has a library to match.

You already know about ```classes``` and ```objects```, just not in a programming sense: 
* *you* are an instance of the class `boy` or of the class `girl`, 
* *you* come with a bunch of attributes that you can do just like every other boy or girl, 
* *you* have attributes special to you - called ```overriding```.
  * an object is an instance of a class, where an class is some sort of abstraction of a category of things!

**You have spent all your life writing and have expectations about what Python strings can do.**

So, let's play with your name:

```
name = "your name"
```

**```"your name"``` is a string that we have labelled ```name```**

as a string object, it comes with methods and attributes:
```
"your name".capitalize()
```

gives the same result as 
```
name.capitalize()
```

You can also count letters:

```
len("your name")
```

or talk about the n'th character:

```"your name"[3]```

array indexing is interesting in python, so you can do this:

```"your name"[0:3:1]```

where:
* 0 is the start
* 3 is the end
* 1 is the step length

but what does ```"your name"[::-1]``` do?


*Things in Python have behaviour defined by Python, by the package it belongs to, and by programs that you write.*


##Task 3 - A graphics app

There are lots of graphics packages for python, 
* Tkinter is one of the oldest. 
* The name ```Tkinter``` is the python interface to Tk, a cross-platform graphics toolkit, embedded in many applications, from engineering and design to office applications.

* *This is a basic Tkinter template for making a graphics app:**
  * import the libraries
  * create the top level object
  * attach a canvas
  * draw things
  * pack the canvas
  * run the mainloop

*Some of the steps may be hidden by the package, but it is useful to keep remembering the basic template*

```python
# import libraries
from Tkinter import * 

# create the top level Tk object
window=Tk()
window.title("a window")

# create the canvas
canvas = Canvas(window, height=600, width=600)

# draw stuff on the canvas
# first the pizza base
canvas.create_oval(200,200,300,300,fill="brown")
# draw some more stuff
# this might be the tomato sauce toppings
# now add your cheese and anything else, before we get to the pepperoni

# pack the canvas and run the Tk mainloop
canvas.pack()
window.mainloop()
```

##Task 4 - Running and saving your work

* click *run* at the top left - did you get what you expected?
  * press this every time you want to see what your code does 
  * this should then appear in modal form labelled 'Tk'

* click *save* at the top left - no URL this time :/
  * the first time you will need to give a file name
  * save the file to a memory stick if you need to transport it


##Task 6 - Things to add to your Pizza

* Making the base
  * Note - the numbers give a bounding box for the oval

```python
canvas.create_oval(50,50,450,450,fill="brown")
```
  
* Putting tomato sauce on the base
  * Note - there is no opacity in a tk canvas, so the layers are important

```python
canvas.create_oval(65,65,435,435,fill="red")
```

***

##Task 7 - Random toppings

* look up what other toppings, we can have more shapes and colours
  * http://infohost.nmt.edu/tcc/help/pubs/tkinter/web/index.html

* we can also add them in random places, try this for pepperoni!

```python
colours = ["red", "orange", "yellow", "green", "blue", "purple"]

# create some pepperoni - random 3 places
for x in range(15):
    rndX = randint(0,600)
    rndY = randint(0,400)
    rndCol = randint(0, (len(colours)-1))
    canvas.create_oval(rndX,rndY,rndX+50,rndY+50,fill=colours[rndCol])

```

Pro Tip - put the drawing things all together and change the magic numbers for variables

***

Remember to save your file and put it on a memory stick - we will be animating our pizza next week!


 
John Reeves

john@de-velopment.com
www.programming-uk.com
www.twitter.com/programming_uk


```python
# -*- coding: utf-8 -*-
"""
Created on Thu May 26 09:14:29 2016

@author: jreeves
"""
#import libraries
from Tkinter import *
from random import randint
 
c_width,c_height=600,600
col="black"

pepperone=[]
colours = ["red", "orange", "yellow", "green", "blue", "purple"]
 
x0,y0=0,0
x1,y1=c_width,c_height
radius= (x1-x0)/2
 
N_tot,N_hit=40,0
pepperone_please=N_tot
 
# step 1: create the top level Tk object
window=Tk()
window.title("a window")
 
# step 2: create the canvas
canvas=Canvas(width=c_width, height=c_height, bg=col)
 
# step 3: draw stuff on the canvas
# pizza things
 
# create the pizza dough
canvas.create_oval(x0,y0,x1,y1,fill="brown")
# create the tomato sauce
canvas.create_oval(x0+20,y0+20,x1-20,y1-20,fill="red")
# create the cheese
canvas.create_oval(x0+40,y0+40,x1-40,y1-40,fill="yellow")

def in_pepperone(p, x,y):
    if x<p[0]:  
       # print "p0: ",x, "<", p[0]
        return False
    if y<p[1]: 
       # print "p1: ",y, "<", p[1]
        return False
    if x>p[2]: 
       # print "p2: ",x, ">", p[2]
        return False
    if y>p[3]: 
       # print "p3: ",y, ">", p[3]
        return False
    return True
    
def callback(event):
    print "clicked at", event.x, event.y
    global pepperone 
    print "checking"
    for p in pepperone:
        if in_pepperone(p,event.x,event.y) == True:
            print event.x, event.y, p
            return p

lastx, lasty = 0, 0

def move_pepperone(event):
    print "clicked at", event.x, event.y
    print "moved to", 
    global lastx, lasty
    global pepperone
    print "checking"
    for p in pepperone:
        if in_pepperone(p,event.x,event.y) == True:
            print event.x, event.y, p, p[4]
            #canvas.create_oval(event.x-25, event.y-25, event.x+25, event.y+25, fill=colours[p[4]])
            lastx, lasty = event.x, event.y

def draw_pepperone(event):
    #canvas.create_oval(event.x-25, event.y-25, event.x+25, event.y+25, fill=colours[p[4]])
    print "clicked at", event.x, event.y
    print "moved to", 
    global lastx, lasty
    global pepperone
    print "checking"
    for p in pepperone:
        if in_pepperone(p,event.x,event.y) == True:
            print event.x, event.y, p, p[4]
            canvas.create_oval(event.x-25, event.y-25, event.x+25, event.y+25, fill=colours[p[4]])
            lastx, lasty = event.x, event.y

canvas.bind("<Button-1>", callback)
canvas.bind("<B1-Motion>", move_pepperone)
canvas.bind("<ButtonRelease-1>", draw_pepperone)

# create some pepperoni - random 3 places

while (N_hit < pepperone_please):
    randomSpaceX,randomSpaceY= randint(x0,x1),randint(x0,y1)
    randomColour = randint(0, (len(colours)-1))
    if (randomSpaceX-300)**2 + (randomSpaceY-300)**2 < (radius-20)**2:

            canvas.create_oval(randomSpaceX,randomSpaceY,randomSpaceX+50,randomSpaceY+50,fill=colours[randomColour])
            pepperone.append((randomSpaceX,randomSpaceY,randomSpaceX+50,randomSpaceY+50,randomColour))
            N_hit = N_hit + 1
           
 
print("%d hits in %d throw, gives %3.5f as an approximation to 3.1415926535, is it any good?" % (N_hit,N_tot, float(N_hit / 1000.)))
# canvas.create_line(100,100, 200,200, fill="green")
 
# Step 4: pack the canvas and run the Tk mainloop
canvas.pack()

print pepperone 
 
window.mainloop()

```

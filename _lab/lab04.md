---
layout: lab
num: lab04
ready: true
desc: "Turtle Graphics: Scene from a forest"
assigned: 2017-08-23 09:30:00.00-7
due: 2017-08-30 17:00:00.00-7
submit_cs_pnum: 
---

Goal
====

The goal of this exercise is to write two functions to draw basic shapes using turle graphics. You will then use these primitives to create a forest scene. The key idea to learn how to use functions as building blocks, and apply repetition and randomization in your code to create interesting outcomes.


What you'll be drawing
----------------------

You'll be writing functions to produce two basic shapes: a rectangle and a triangle. Each function takes parameters that specify the size, orientation, pen color, and fill color of that shape. This will allow us to create more interesting drawings later on. The function definitions are given below:

-   `drawRectangle(width, height, tilt, penColor, fillColor)`
-   `drawTriangle(base, height, tilt, penColor, fillColor)`


The output produced when each function is callled with specific parameter values is shown in the following figure.

![basicShapes](basicShapes.png)

The above drawings are the result of calling either <code>drawRectangle()</code> or <code>drawTriangle()</code>. In each drawing, the turtle stamp shoes the initial location and heading of the turtle right before the corresponding function is called. For example the top left drawing is the output of the following line of code, when the turtle is at the top left corner:

```
drawRectangle( width = 50, height = 100, tilt = 0, penColor = "red", fillColor = "")
```

The subsequent three drawings on the same row are the output of repeatedly moving the turtle to the right, and calling the <code>drawRectangle()</code> function changing the tilt, penColor and fillColor. The function calls and parameter values to produce these drawings are given below:


```
drawRectangle( width = 50, height = 100, tilt = 20, penColor = "green", fillColor = "yellow")
...
drawRectangle( width = 50, height = 100, tilt = 60, penColor = "blue", fillColor = "blue")
...
drawRectangle( width = 50, height = 100, tilt = 90, penColor = "red", fillColor = "red")

```

Similarly, the drawings on the next row are the result of repeatedly calling **<code>drawTriangle()</code>** with the following parameter values:

|   <code>base</code>   |  <code>height</code>    |   <code>tilt</code>   |   <code>penColor</code> |  <code>fillColor</code> |   
|-----------------------|-------------------------|-----------------------| ------------------------| ----------------------- |
|   50                  |   100                   |   0                   |   <code> "red" </code>  |  <code> ""</code>       |
|   50                  |   100                   |   20                  |   <code> "green" </code>|  <code> "yellow"</code> |
|   50                  |   100                   |   60                  |   <code> "red"</code>   |  <code> "red"</code>    |
|   50                  |   100                   |   90                  |   <code> "blue"</code>  |  <code> "blue"</code>   |


Once you have implemented the above basic shape primitives, you will use them as building blocks to create the following forest scene!

![forestScene](forestScene.png)

To create this scene you will implement additional functions to draw a tree, a hut, a forest and a village! 


# The programming part

## Step 1: Create a lab04 directory under your cs8 directory


Create a directory called `~/cs8/lab04` for a file
we are going to call `lab04.py`.

If you don't recall the commands, you may refer to any of the previous labs

## Step 2: Open `idle3` and create `lab04.py`

Open up `idle3` and select the menu option `File => New File` to create a new file.

In this file, put this code (but put your name instead of "your name goes here")

```
# lab04.py, your name goes here
import turtle
import math 


t = turtle.Turtle()

```

You can name your turtle anything you like; I used `t` because it's short to type.

Optionally, you can make your turtle look like a turtle by typing this:

```
t.shape("turtle")
```

Save this, and run it.   You should see a turtle appear.


## Step 3: Create and implement the functions for the two basic shapes (rectangle and triangle)

In your lab04.py file, write the skeleton of <code> drawRectangle() </code> and <code> drawTriangle()</code> as shown below. You will need some of the trigonometric functions provided in that math module to implement <code> drawTriangle()</code>. In order to use that module, add a line to import it at the top of the file. To learn more about the math module refer [the Python documentation on the module](https://docs.python.org/3/library/math.html) and scroll down to the section on trigonometric functions.

```
import math

def drawRectangle(width, height, tilt, penColor, fillColor):
    """
    draw a rectangle with a given width, height, penColor and fillColor,
    with the current location of the turtle being the 
    lower left corner, and the bottom side tilted by an angle tilt (specified in degrees)
    relative to the horizontal axis. Use a turtle called t to create the drawing
    """

    # Insert code to draw the rectangle
    
def drawTriangle(base, height, tilt, penColor, fillColor):
    """
    draw a triangle with a given base, height, penColor and fillColor,
    with the current location of the turtle being the 
    lower left corner, and the bottom side tilted by an angle tilt (specified in degrees)
    relative to the horizontal axis. Use a turtle called t to create the drawing
    """

    # Insert code to draw the rectangle
  
def testRectangle():
    
    drawRectangle( 50, 100, 0, "red", "") 

    # Move the turtle right by 200 units without leaving a trail
    t.seth(0)   # Set the absolute heading of the turtle to 0 degrees (pointing east)
    t.up()     
    t.forward(200) # Move the turtle forward by 200 units 
    t.down()

    drawRectangle( 50, 100, 20, "green", "yellow") 

    # Move the turtle right by 200 units without leaving a trail
    t.seth(0)   # Set the absolute heading of the turtle to 0 degrees (pointing east)
    t.up()     
    t.forward(200) 
    t.down()

   

testRectangle()
```

* Read the test code provided in testRectangle(). Refer to the [turtle documentation](https://docs.python.org/3.6/library/turtle.html) to understand any commands that may be new to you. In particular, note that you can use the t.forward() command to move the turle forward relative to its current location in the direction that it is currently pointing. Similarly, the commands t.left() and t.right() rotate the turtle in the anticlockwise or clockwise directions respectively. These are commands that you may use as alternatives to the goto() command in your implementation of the drawRectangle() and drawTriangle() functions. 

* On a piece of paper draw the output that you expect to get for a correct implementaion of the drawRectangle() function, when the above code is executed. You may refer to the drawings and information on the top of this page.

* Implement the drawRectangle() function and run your code until you get the expected output for the provided test code.

* Add more test cases to the testRectangle() function until you arrive at a general enough implementation

* Repeat the above process to implememt and test your drawTriangle() function. 

With these basic primitives, you are now ready to make something more interesting! Refer back to the forest scene that you are working towards. Which functions do you think you should implement next? Try to write the definitions of these functions before reading the next section.

## Step 4: Draw a tree

Now that we have our basic shapes (the rectangle and the triangle), we are in a position to create the essential elements of our forest scene in code - functions to draw a tree and a hut. Once we do that, drawing the forest boils down to making repeated calls to these two functions and moving the turtle to a new spot in between function calls. We'll start with the tree because it has a more regular structure. 

Define a 'drawTree()' function to draw a tree.  A general 'drawTree()' function should allow the user to specify the height and color of the tree. With that in mind, the definition of the 'drawTree()' function is given below. 

```
def drawTree(height, color):
    ''' This function draws a tree with a specific height and color. The bark of the tree is always brown, and all other parameters such as the width of the tree or the length of the bark should be chosen so that the tree is well proportioned. The tree top is composed of three triangles stacked on top of each other
    '''

```




To make sure that you can draw your tree at two different places, draw a tree with width 50 and height 100, then pick up the pen and move it to a new location, and then draw a bigger tree and a smaller tree at two different locations


If see two proportioned trees that correspond to the specified width and height, you are ready for the next step.

## Step 5: Draw a row of trees

## Step 6: Take a detour into random numbers

## Step 7: Draw a hut 

## Step 8: Put it all together



When you are finished, ask a TA or instructor to look it over and give you some feedback on it.  

It should be structured in a way that there is 

1. A single file called `lab04.py`
2. Code at the top of the `lab04.py` file that sets up a turtle
3. Next, function defintions for each of the basic shapes

4. Finally, code that calls those functions to draw your initials and graduation year all in a line
5. And then, code that draws all those letters and digits <strong>a second time, at a different size</strong> by <em>calling your functions again</em>.

If you code meets all those criteria, you should be in good shape to submit it.


## Step 9: Submitting via submit.cs

Note that this week, although we are using submit.cs, it is NOT the case that the grade you get from submit.cs is your final grade for the assignment.   The grade on submit.cs is just a PART of your grade--you will get 10 points for basically submitting *anything* that is a valid Python program that has the name lab01.py.   However, the other 90 points for this lab will come from an instructor or TA doing a manual inspection of your code to see if it complies with the requirements listed above.      

If you want reassurance that your code is in good shape, you may ask a TA or instructor to look it over during office hours or lab.

To submit your code, use:

### Navigate to the page for submitting lab04

The page for submitting lab04 is here: <https://submit.cs.ucsb.edu/form/project/{{page.submit_cs_pnum}}/submission>

Navigate to that page, and upload your `lab04.py` file.

If you are working on the ECI/CSIL/lab linux systems, you can also submit at the command line with this command:

```
~submit/submit ~/cs8/lab04/lab04.py
```

It will ask for your email address: use your full umail address (e.g. `cgaucho@umail.ucsb.edu`).  For password, use the password that you enter for the submit.cs system.    You may save these credentials if you don't want to have to type them in every time.


Note that if you try to upload a file with a name that does not match EXACTLY the name `lab01.py`, the system will not allow you to do it. 

Once you upload it, you should get a page that shows your submission is pending.

Refresh that page, and you should get one that indicates with either red, or green, whether the test cases for your code passed or failed.

If you got all green, and 10 points, then your submission was accepted---but to emphasize, for this week, the other 90 points will be assigned by a human grader.   You'll be notified of that grade [via Gauchospace](https://gauchospace.ucsb.edu).

Created by Diba Mirza
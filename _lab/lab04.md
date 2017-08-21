---
layout: lab
num: lab04
ready: true
desc: "Turtle Graphics: Art compositions with basic shapes and loops"
assigned: 2017-08-23 09:30:00.00-7
due: 2017-08-30 17:00:00.00-7
submit_cs_pnum: 
---

Goal
====

The goal of this exercise is to write four functions to draw basic shapes using turle graphics. You will then use these primitives to create more complex graphics compositions by completing a few guided exercises and writing two functions from scratch. The key idea to learn how to using functions as building blocks in your code, and the use of loops to create more complex compositions.


What you'll be drawing
----------------------

You'll be writing functions to produce two basic shapes: a rectangle and a triangle. In order to use these shape primitives to create more complex drawings, each function takes parameters that specify the size, orientation, pen color, and fill color of that shape. The function definitions for the two basic shapes are:

-   `drawRectangle(width, height, tilt, penColor, fillColor)`
-   `drawTriangle(base, height, tilt, penColor, fillColor)`


Below is the output produced when each function is callled with specific parameter values.

![basicShapes](basicShapes.png)

The above drawings are produced by calling either <code>drawRectangle()</code> or <code>drawTriangle()</code>. In each drawing, the initial location and heading of the turtle right before the corresponding function is called is shown by the turtle stamp. For example the top left drawing is the output of the following function call:

```
drawRectangle( width = 50, height = 100, tilt = 0, penColor = "red", fillColor = "")
```

The subsequent three drawings on the same row are the output of repeatedly moving the turtle to the right, and calling the <code>drawRectangle()</code> function with the same width and height as before, changing the tilt, penColor and fillColor. The exact function calls and parameter values to produce these drawings are given below:


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

Your drawing does not have to match the above scene exactly but should contain the same elements. To create this scene to will implement additional fucntions to draw a tree, a hut, a forest and a village!


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

t = turtle.Turtle()

```

You can name your turtle anything you like; I used `t` because it's short to type.

Optionally, you can make your turtle look like a turtle by typing this:

```
t.shape("turtle")
```

Save this, and run it.   You should see a turtle appear.


## Step 3: Create the functions for the two basic shapes (rectangle and triangle)



```
def drawA(width, height):
    """
    draw the letter A with a given width and height,
    with the current location being the lower left corner of the A
    using a turtle called t
    """

    # figure out where we are

    startX = t.xcor()
    startY = t.ycor()

    # figure out the other points using only what we know,
    # which is width, height, startX and startY
    
    topAX = startX + (width/2)
    topAY = startY + height

    bottomRightX = startX + width
    bottomRightY = startY
    
    barLeftX = startX + width/4
    barLeftY = startY + height/2

    barRightX = startX + (width/4) + (width/2)
    barRightY = startY + height/2
    
    # draw left hand side of the A (assumes we start at startX,startY)
    
    t.goto(topAX,topAY)

    # draw the right side of the A

    t.goto(bottomRightX, bottomRightY)

    # draw bar across the middle
    
    t.up()
    t.goto(barLeftX,barLeftY)
    t.down()
    t.goto(barRightX,barRightY)

    # leave turtle at lower right hand corner of letter
    
    t.up()
    t.goto(bottomRightX,bottomRightY)
    t.down()

drawA(50,100)

```

## Step 4: Make sure first letter function is reusable

Now, we want to make sure your function is general enough to be able to draw your letter:

* at different places on the screen
* at different heights and widths

To make sure that you can draw your first letter at two different places, change the function call
at the bottom of the file from something like this:

```
drawA(50,100)
```

to something like this, that draws an A of width 50 and height 100, picks up the pen and moves to a new location,
and then draws the A again with a different width and height.

```
drawA(50,100)

# a new line
t.up()
t.goto(-200,-200)
t.down()

drawA(40,80)
```

If your code is written in a general way, i.e. the `drawA` routine works ONLY with the `startX`, `startY`, `width`, and `height` values, both letters should look good.  If one of them looks incorrect, then see if you can determine what is wrong with your code.

When you see two good drawings of your first letter, you are ready for the next step.

## Step 5: Add the function for the next letter or number

Now we are going to add another function just like the first, right under it.

Keep the code that has the actual function calls *at the bottom* of the file.  The order should be:

* First, the code that imports and sets up the turtle, i.e.
   ```
   import turtle
   t = turtle.Turtle()
   t.shape("turtle")
   
   ```
* Second, the functions definitions for `drawA`, `drawX`, etc., e.g.
   ```
   def drawA(width,height):
   
      startX = t.xcor()
      startY = t.ycor()
      
      # etc..
   
   def drawX(width,height):
      
      # code for drawX is here, indented...
     
   ```
   
* Then, last, the section of code with function calls that draw your letters

   ```
   drawA(50,100)
   
   # a new line
   t.up()
   t.goto(-200,-200)
   t.down()

   drawA(40,80)
   # etc ...
   
   ```
   
Try running the code again after adding the function definition for your new letter (e.g. `def drawX(width,height): ...`.  Make sure you don't get any error messages&mdash;if you do, fix those before continuing.

Then, we'll try adding in code to call the function for your second letter, for example `drawX(100,200)`.    We probably want to move the turtle over a bit before drawing the second letter.  We can do that with with `t.forward()` or another `t.goto()` with some numbers, as shown in the two options below.  

<table>
<tr>
<th>
Before
</th>
<th markdown="1">
After (using `t.forward()`)
</th>
<th markdown="1">
After (using `t.goto()`)
</th>
</tr>

<tr>
<td markdown="1">

```
drawA(50,100)

# a new line
t.up()
t.goto(-200,-200)
t.down()

drawA(40,80)
```
</td>

<td markdown="1">

```
drawA(50,100)

# a bit of space
t.up()
t.forward(10)
t.down()

drawX(50,100)

# a new line
t.up()
t.goto(-200,-200)
t.down()

drawA(40,80)

# a bit of space
t.up()
t.forward(10)
t.down()

drawX(50,100)

```
</td>
<td markdown="1">

```
drawA(50,100)

# a bit of space
t.up()
t.goto(60,0)
t.down()

drawX(50,100)


# a new line
t.up()
t.goto(-200,-200)
t.down()

drawA(40,80)


# a bit of space
t.up()
t.goto(-150,-200)
t.down()

drawX(50,100)

```
</td>
</tr>
</table>


## Step 6: Continue adding letters and numbers one by one

Continue adding letters and numbers one by one until you have two rows at different sizes, just like in the example.

When you are finished, ask a TA or instructor to look it over and give you some feedback on it.  

It should be structured in a way that there is 

1. A single file called `lab01.py`
2. Code at the top of the `lab01.py` file that sets up a turtle
3. Next, function defintions for each of the letters and digits that you draw, each of which takes `width` and `height` as parameters, e.g.
   ```
   def drawP(width,height):
      ...
   
   def drawC(width,height):
      ...
   def draw2(width,height):
      ...
      # etc
   ```
4. Finally, code that calls those functions to draw your initials and graduation year all in a line
5. And then, code that draws all those letters and digits <strong>a second time, at a different size</strong> by <em>calling your functions again</em>.

If you code meets all those criteria, you should be in good shape to submit it.


## Step 7: Submitting via submit.cs

Note that this week, although we are using submit.cs, it is NOT the case that the grade you get from submit.cs is your final grade for the assignment.    The grade on submit.cs is just a PART of your grade--you will get 10 points for basically submitting *anything* that is a valid Python program that has the name lab01.py.   However, the other 90 points for this lab will come from an instructor or TA doing a manual inspection of your code to see if it complies with the requirements listed above.      

If you want reassurance that your code is in good shape, you may ask a TA or instructor to look it over during office hours or lab.

To submit your code, use:

### Navigate to the page for submitting lab00

The page for submitting lab00 is here: <https://submit.cs.ucsb.edu/form/project/{{page.submit_cs_pnum}}/submission>

Navigate to that page, and upload your `hello.py` file.

If you are working on the ECI/CSIL/lab linux systems, you can also submit at the command line with this command:

```
~submit/submit ~/cs8/lab01/lab01.py
```

It will ask for your email address: use your full umail address (e.g. `cgaucho@umail.ucsb.edu`).  For password, use the password that you enter for the submit.cs system.    You may save these credentials if you don't want to have to type them in every time.


Note that if you try to upload a file with a name that does not match EXACTLY the name `lab01.py`, the system will not allow you to do it. 

Once you upload it, you should get a page that shows your submission is pending.

Refresh that page, and you should get one that indicates with either red, or green, whether the test cases for your code passed or failed.

If you got all green, and 10 points, then your submission was accepted---but to emphasize, for this week, the other 90 points will be assigned by a human grader.   You'll be notified of that grade [via Gauchospace](https://gauchospace.ucsb.edu).


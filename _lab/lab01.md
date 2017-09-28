---
layout: lab
num: lab01
ready: false
desc: "Turtle Graphics: Basic shapes"
assigned: 2017-10-10 09:30:00.00-7
due: 2017-10-17 16:50:00.00-7
submit_cs_pnum: 768
---

Goal
====

The goal of this exercise is to practice with Turtle Graphics in
Python by producing somewhere between two and four Python functions
that use Turtle Graphics to make particular shapes.

(You'll understand the reasons its "between three and six" in a
minute.)


What you'll be drawing
----------------------

You'll be writing functions to produce two basic shapes: a rectangle and a triangle. Each function takes parameters that specify the size, pen color, and fill color of that shape. The drawRectangle function additionally allows us to specifiy the tilt of the rectangle relative to the x-axis in degrees. The function definitions are given below:

-   `drawRectangle(width, height, tilt, penColor, fillColor)`
-   `drawTriangle(base, height,  penColor, fillColor)`


The output produced when each function is callled with specific parameter values is shown in the following figure.

![basicShapes](basicShapes.png){:height="400px"}

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

|   <code>base</code>   |  <code>height</code>     |   <code>penColor</code> |  <code>fillColor</code> |   
|-----------------------|-------------------------| ------------------------| ----------------------- |
|   50                  |   100                   |  <code> "red" </code>  |  <code> ""</code>       |
|   50                  |   100/2                   |  <code> "green" </code>|  <code> "yellow"</code> |
|   50                  |   100/4                   |  <code> "red"</code>   |  <code> "red"</code>    |
|   50                  |   100/8                   |  <code> "blue"</code>  |  <code> "blue"</code>   |


In a later lab, we will use these functions to create more interesting drawings. 

# The programming part

## Step 1: Create a lab01 directory under your cs8 directory

In [lab00](/lab/lab00) you created a directory `~/cs8/lab00` and, if
you followed the instructions to the letter, your `hello.py` file
is located in that directory.

You should now create a directory called `~/cs8/lab01` for a file
we are going to call `lab01.py`.

To do that, use the commands below.

(Just like last week, your prompt may not be exactly like the one shown here.  Instead of `-bash-4.2$ `, you might have something like `[cgaucho@cstl-15 ~]$ `.    The `cgaucho` here is your username, the `cstl-15` is where you are logged in, and the `~` is your current directory.    Don't be distracted by this detail.)


<pre>-bash-4.2$ <strong>cd</strong>
-bash-4.2$ <strong>pwd</strong>
/<em>cs</em>/<em>student</em>/<em>yourusername</em>
-bash-4.2$ <strong>cd cs8</strong>
-bash-4.2$ <strong>pwd</strong>
/<em>cs</em>/<em>student</em>/<em>yourusername</em>/cs8
-bash-4.2$ <strong>mkdir lab01</strong>
-bash-4.2$ <strong>cd lab01</strong>
-bash-4.2$ <strong>pwd</strong>
/<em>cs</em>/<em>student</em>/<em>yourusername</em>/cs8/lab01
-bash-4.2$
</pre>

## Step 2: Open `idle3` and create `lab01.py`

Open up `idle3` and select the menu option `File => New File` to create a new file.

In this file, put this code (but put your name instead of "your name goes here")

```
# lab01.py, your name goes here
import turtle

t = turtle.Turtle()

```

You can name your turtle anything you like; I used `t` because it's short to type.

Optionally, you can make your turtle look like a turtle by typing this:

```
t.shape("turtle")
```

And you can set your turtle to move at the fastest possible speed on the screen - which will help make your drawings as quickly as possible.

```
t.speed(0)
```
Also, you can change the pen width to make your drawings look more prominent

```
t.width(4)
```

Save this, and run it.   You should see a turtle appear. The turtle is not moving because we haven't given it instructions to move. 


## Step 3: Create a function for drawing a rectangle

Next, you are going to define a function to draw a rectangle. Your final function will be names drawRectangle() but before you implement that we will implement a couple of different versions of that function with simpler specifications. 

Below is the first version of the function. It doesn't take any parameters, instead it draws a rectangle with a fixed width (50), a fixed height (100), a fixed orientation (0 degrees with respect to the x-axis). To write the code we should first come up with a plan, a sequence of steps or algorithm (CS speak). Here is a very simple algorithm: Orient the turtle to point right at 0 degrees with respect to the x-axis. Move the turtle forward by 50 units, turn the turtle left by 90 degrees, move the turtle forward by 100 units, turn left 90 degrees, move forward by 50 units, turn left by 90, move forward by 100...(we are repeating ourselves, but that's fine for now. In later labs we will express the same algorithm in a more concise way). Here is the code that does what we just described: 

```
def drawRectangle_1():
    """
    draw a rectangle with width 50 and height 100. Use a turtle called t to create the drawing
    """
    t.seth(0)        # Set the initial orientation of the turtle to 0 degrees
    t.forward(50)    # Move the turtle forward by 50 units in the direction that it was pointing
    t.left(90)       # Turn the turtle left by 90 degrees relative to the direction it was pointing
    t.forward(100)   # Move the turtle forward by 100 units
    t.left(90)
    t.forward(50)
    t.left(90)
    t.forward(100)
    t.left(90)       # Make sure the turtle is oriented back to its initial orientation
    
```

Put this code right after the code you wrote earlier in the <tt>{{page.num}}.py</tt> file. After entering the function definition, at the bottom try a sample
function call (`drawRectangle_1()`).  The
function call should NOT be indented, just as shown in the example below.

Try running it and see if the rectangle looks ok.  Change the first line: `t.seth(0)` to `t.seth(90)`. Save and run your code again. What changed? 

We will now update our `drawRectangle_1` to draw a rectangle with a green boundary and yellow interior. To do that write the following statement before the very first line in the body of the function:

```
  t.color("green", "yellow") # Sets the pen color to green and fill color to yellow
``` 

The first parameter is the pen color and the second is the fill color. To actually fill the rectangle with the specified color, you must precede the code that draws the rectangle with t.begin_fill() and follow it with t.end_fill(). Below is the complete code. Save and run it.

```
def drawRectangle_1():
    """
    draw a rectangle with width 50, height 100, tilt 0, pen color green and fill color yellow. Use a turtle called t to create the drawing
    """
    t.color("green", "yellow")
    t.seth(0)        # Set the initial orientation of the turtle to 0 degrees
    t.begin_fill()   
    t.forward(50)    # Move the turtle forward by 50 units in the direction that it was pointing
    t.left(90)       # Turn the turtle left by 90 degrees relative to the direction it was pointing
    t.forward(100)   # Move the turtle forward by 100 units
    t.left(90)
    t.forward(50)
    t.left(90)
    t.forward(100)
    t.left(90)       # Make sure the turtle is oriented back to its initial orientation
    t.end_fill()
```
You will soon discover that there are many different ways to solve any problem. Computer Scientists almost always care about *correct* solutions that run the fastest on any computer (which is the field of algorithms), and expressing those solutions in the simplest and most understandable way in code (good programming chops).

Below is an alternate implementation for drawing a rectangle. The algorithm is slightly different: It first computes the absolute location of the 4 corners of the rectangle and then commands the turtle to go to the four locations in a specific order. To move the turtle to any location (x,y), we will use a new turtle method: t.goto(x, y). Here is one possible implementation of this algorithm. Inorder to we will name our function draw:

```
def drawRectangle_2():
    """
    draw a rectangle with width 50, height 100, tilt 0, pen color green and fill color yellow . Use a turtle called t to create the drawing
    """
    t.color("green", "yellow")

    xleft = t.
    t.seth(0)        # Set the initial orientation of the turtle to 0 degrees
    t.begin_fill()   
    t.forward(50)    # Move the turtle forward by 50 units in the direction that it was pointing
    t.left(90)       # Turn the turtle left by 90 degrees relative to the direction it was pointing
    t.forward(100)   # Move the turtle forward by 100 units
    t.left(90)
    t.forward(50)
    t.left(90)
    t.forward(100)
    t.left(90)       # Make sure the turtle is oriented back to its initial orientation
    t.end_fill()


```








Refer to the [turtle documentation](https://docs.python.org/3.6/library/turtle.html) to understand all the commands we have used so far and possible alternatives to them (like t.goto())

## Step 4: Make sure your drawRectangle() function is reusable

Now, we want to make sure your function is general enough to be able to draw a rectangle:

* at different heights, widths and orientation
* with different pen and fill color


What you need to do is to write the final version of this function that takes 5 parameters as shown below:

```
def drawRectangle(width, height, tilt, penColor, fillColor):
    """
    draw a rectangle with a given width, height, penColor and fillColor,
    with the current location of the turtle being the 
    lower left corner, and the bottom side tilted by an angle tilt (specified in degrees)
    relative to the horizontal axis. Use a turtle called t to create the drawing
    """

    # Insert code to draw the rectangle

```

Add the five parameters to the version of the function we wrote earlier and modify the code to make it generic. 


Next we want to draw two rectangles at different locations. To make sure that you can do that change the function call
at the bottom of the file from something like this:

```
drawRectangle()
```

to something like this, that draws a rectangle with a given size and color,  picks up the pen and moves to a new location,
and then draws another rectangle with a different size and color.

```
drawRectangle( 50, 100, 0, "red", "") 


t.seth(0)   # Set the absolute heading of the turtle to 0 degrees (pointing east)

# Move the turtle right by 200 units without leaving a trail
t.up()     
t.forward(200)
t.down()

drawRectangle( 20, 40, 20, "green", "yellow") 

```

Save and run your code to make sure you see two distinct rectangles. If one of them looks incorrect, then see if you can determine what is wrong with your code. We are now going to move to the next step that involves drawing triangles. To keep avoid drawing unnecessary rectangles while writing your drawTriangle function, place the code above in a function called `test_drawRectangle()`. That way the rectangles are drawn only when you call that function. Here is the final code:

```

def testRectangle():
    
    drawRectangle( 50, 100, 0, "red", "") 

    t.seth(0)   # Set the absolute heading of the turtle to 0 degrees (pointing east)


    # Move the turtle right by 200 units without leaving a trail
    t.up()     
    t.forward(200)  
    t.down()

    drawRectangle( 20, 40, 20, "green", "yellow") 
   

testRectangle()  # call the testRectangle function to draw rectangles of different sizes and colors

```


## Step 5: Add the function to draw an isosceles triangle

Now we are going to add another function to draw an [isosceles triangle](https://en.wikipedia.org/wiki/Isosceles_triangle) with the base of the triangle along the x-axis as shown in the figure on top of this page. Place your function definition right below that of drawRectangle(). For this function, you will need some of the trigonometric functions provided in the math module. In order to use that module, add a line to import it at the top of the file. To learn more about the math module refer [the Python documentation on the module](https://docs.python.org/3/library/math.html) and scroll down to the section on trigonometric functions.

Keep the code that has the actual function calls *at the bottom* of the file.  The order should be:

* First, the code that imports and sets up the turtle, i.e.

```
   import turtle
   import math
   t = turtle.Turtle()
   t.shape("turtle")
   t.speed(0)
   t.width(4)
   
```

* Second, the functions definitions for `drawRectangle`, `drawTriangle`, etc., e.g.

```
   def drawRectangle(width, height, tilt, penColor, fillColor):
      t.color(penColor, fillColor)
     
      # etc..
   
   def drawTriangle(width, height, penColor, fillColor):
      
      # code for drawTriangle is here, indented...
     
```
* Third, the function definitions for your test functions

```

def testRectangle():
    
    # code to draw two or more non overlapping rectangles at different locations


def testTriangle():
    
    # code to draw two or more non overlapping isosceles triangles at different locations

```

* Then, last, the section of code that calls the test functions 

```
  # testRectangle()   # You may comment out this line when testing your drawTriangle() function
   testTriangle()
   # etc ...
   
```
   

Remember, before implementing a new function, you need to come up with a plan that you can eventually turn into an algorithm (a sequence of steps to achieve the task you set out to do)

Complete this worksheet to plan for your triangle

Implement your drawTriangle function and write test code in testTriangle to draw at least two non-overlapping triangles of different sizes, then at the very bottom call your test function.


```

    
def drawTriangle(base, height, tilt, penColor, fillColor):
    """
    draw a triangle with a given base, height, penColor and fillColor,
    with the current location of the turtle being the 
    lower left corner, and the bottom side tilted by an angle tilt (specified in degrees)
    relative to the horizontal axis. Use a turtle called t to create the drawing
    """

    # Insert code to draw the triangle

def testTriangle():
    """ Draw at least two non overlapping triangles with different sizes and colors
    """
    # Insert code to test your  drawTriangle function

```


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


<tt>~submit/submit -p {{page.submit_cs_pnum}} ~/cs8/lab01/lab01.py</tt>

It will ask for your email address: use your full umail address (e.g. `cgaucho@umail.ucsb.edu`).  For password, use the password that you enter for the submit.cs system.    You may save these credentials if you don't want to have to type them in every time.


Note that if you try to upload a file with a name that does not match EXACTLY the name `lab01.py`, the system will not allow you to do it. 

Once you upload it, you should get a page that shows your submission is pending.

Refresh that page, and you should get one that indicates with either red, or green, whether the test cases for your code passed or failed.

If you got all green, and 10 points, then your submission was accepted---but to emphasize, for this week, the other 90 points will be assigned by a human grader.   You'll be notified of that grade [via Gauchospace](https://gauchospace.ucsb.edu).


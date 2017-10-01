---
layout: lab
num: project01
ready: false
desc: "Turtle Graphics: Scene from a forest"
assigned: 2017-10-20 11:00:00.00-7
due: 2017-11-09 20:00:00.00-8
submit_cs_pnum: 774
---

# To do : rewrite section on "Take a detour into random numbers" not to use tilt angles for darwTriangle, set up submit.cs

Goal
====

The goal of this exercise is to draw a forest scene from basic shape primitives that you will implement using turtle graphics. The key idea to learn how to use functions as building blocks in more complex compositions. You will also learn about using repetition and randomization in your code to create interesting outcomes.


What you'll be drawing
----------------------

In this lab you will use the basic shapes that you created in lab03 as building blocks to create the following forest scene!

![forestScene](forestScene.png){:height="400px"}

To create this scene you will implement additional functions to draw a tree, a hut, a forest and a village! 


# The programming part

## Step 1: Create a {{page.num}} directory under your cs8 directory


Create a directory called `~/cs8/{{page.num}}` for a file
we are going to call `{{page.num}}.py`.

If you don't recall the commands, you may refer to any of the previous labs

## Step 2: Open `idle3` and create <tt>{{page.num}}.py</tt>

Open up `idle3` and select the menu option `File => New File` to create a new file. Save this file as {{page.num}}.py

In this file, put this code (but put your name instead of "your name goes here")

<pre>
# {{page.num}}.py, your name goes here
import turtle
import math 

if __name__=="__main__":
  print('Inside main of project01.py')

</pre>

The `if` test for `__name__=="__main__":` is where everthing in your program
should go <em>except for</em>:

* `import` statements
* function definitions

I realize it's a strange looking line of code&mdash;if you haven't already
seen it before in lecture or another lab, you can find an explanation of it
here: [All about `if __name__=="__main__":`](https://ucsb-cs8.github.io/ptopics/main_blocks/).

You can name your turtle anything you like; I used `t` because it's short to type.


Save this, and run it.   You should see 'Inside main of project01.py' printed to screen. Don't set up the turtle in this file. We will reuse the turtle setup from lab03.



## Step 3: Create a basicShapes module from your lab03.py

* Make a copy of your code from lab03 and rename it as basicShapes.py:

```
cp ~/cs8/lab03/lab03.py ~/cs8/project01/basicShapes.py
```

* Modify the code in basicShapes.py so that you can import the code as a model. Apply the concepts that you learned in lab04 about making your own modules using the `if __name__=="__main__": ` clause. Here are some hints:

- In basicShapes.py, keep all the statements that relate to importing modules and setting up the turtle outside the `if __name__=="__main__:" at the top of the file:

```
import turtle
import math
t = turtle.Turtle()
t.shape("turtle")
t.speed(0)
t.width(4)
```
- Put all other code that is not within a function definition in the `if __name__=="__main__:" 

* Now you are ready to import basicShapes as a module and use the functions that you implemented there - specifically: `drawRectangle()` and `drawTriangle()`

* In Idle, open {{page.num}}.py and 


## Step 4: Draw a tree

Now that we have our basic shapes (the rectangle and the triangle), we are in a position to create the essential elements of our forest scene in code - functions to draw a tree and a hut. Once we do that, drawing the forest boils down to making repeated calls to these two functions and moving the turtle to a new spot in between function calls. We'll start with the tree because it has a more regular structure. 

Define a 'drawTree()' function to draw a tree.  A general 'drawTree()' function should allow the user to specify the height and color of the tree as captured in the following function definition.  

```
def drawTree(height, color):
    
    ''' 
    This function draws a tree with a specific height and color, with the bottom of the bark at the current location of the turtle. The bark of the tree is always brown. All other parameters such as the width of the tree and the length of the bark are chosen so that the tree is well proportioned. The tree top is composed of three triangles stacked on top of each other.
    '''

```

Copy the above code and place it right after your implementation for `drawTriangle`. Now write a function `testdrawTree()` with some test code to test your implentation of `drawTree()`. Below is some initial test code:

```
def testdrawTree():
    t.up()
    t.goto(0,-400)
    t.down()
    drawRectangle(200, 200, 0 , "red","")
    drawTree(200, "green")
```
The above code helps you visually inspect if the your tree is of the specified height by drawing it alongside a rectangle of the same height. When you run this code with a correct implementation of drawTree() should see that the top of the tree coincides with the top side of the rectangle as shown in the following output:

![testTree](testTree.png){:height="200px"}

Note that there are aspects of the tree that are not specified for you such as the width of the tree, the width and height of the bark, and the spacing between the three triangles that make up the tree top. You should make decisions on these aspects relative to the height of the tree so that a taller tree is wider and has a thicker and taller bark.

Now go ahead and implement your drawTree() function. Add more code to the testdrawTree() function to draw at least two well-proportioned trees of different heights at two different locations.  

## Step 5: Draw a row of trees - repetition made easy with loops

We would now like to go from drawing one tree to many trees, which will essentially become our forest. To begin define the function `drawForest()` as below:

```
def drawForest():
    ''' 
    Draws a collection of trees placed at random locations within a rectangular region
    '''
```
Start by drawing three trees of the same height in a row. One way of doing is this is to repeat a block of code to move the turtle to a specific spot and then call the drawTree() function as shown below:

```
# Move the turtle to location (-200, -100) and draw a tree  
t.up()
t.goto(-200, -100)  
t.down()
drawTree(200, "green")

# Move the turtle to location (0, -100) and draw another tree
t.up()
t.goto(0, -100)  
t.down()
drawTree(200, "green")

# Move the turtle to location (200, -100) and draw the third tree
t.up()
t.goto(200, 100)  
t.down()
drawTree(200, "green")

```
However a better way of doing the same thing is to use a for loop as demonstrated below:

```
for i in range(3):
    t.up()
    t.goto(400, -100)  
    t.down()
    drawTree(200, "green")
```

The for loop runs the block of code inside it three times. Run it and you'll find that the turtle draws all the three instances of the tree at the same spot. Modify exactly one of the lines to get the same output as the version above it. You should get an output similar to the one below:

![manyTrees](manyTrees.png){:height="200px"}

## Step 6: Take a detour into random numbers

In this step you will use the [python random module](https://docs.python.org/3/library/random.html) to add an artistic touch to your drawings.
Although drawing all the trees in a straight line is a good first attempt at creating the forest, its not very realistic. So, your next goal is to place the trees at random locations that are roughly along a horizontal line. As a warm up try out the exercises below that demonstrate the use of the random module with the `drawTriangle()` function that you implemented earlier. 


Start by writing a simple for loop to draw triangles along a circle. This code does not involve randomization.

```

def randomPlay():
    '''
    Experiments with the random module
    '''
    t.pensize(10)
    for i in range(36):
        t.up()
        radius = 200
        x = radius*math.cos(i*10*math.pi/180)
        y = radius*math.sin(i*10*math.pi/180)
        t.goto(x,y)
        t.down()
        tilt = 10*i
        drawTriangle(50, 50, tilt, "black", "red")

randomPlay()
```

When you run the above code, you will find a very regular arrangement of triangles along a circle as shown below. Read the code to understand why its producing this output. Note that both the location and tilt of each triangle is dependent on the value of our loop variable (i). 

![circleOfTris](circleOfTris.png){:height="200px"}

We will now introduce the use of random numbers into this code by selecting the tilt of each triangle to be a random number between 0 and 90 degrees. To do this replace the line `tilt = 10*i` by `tilt = random.randint(0, 90)`. Then run the code. You should see a drawing similar to the one below, although not exactly the same!

![randTilt](randTilt.png){:height="200px"}

We will next use the random module to randomize two other aspects of our drawing: the location of each triangle and its color. Previously, we drew all our triangles along a circle of radius 200. This time we will introduce a small random perturbation in that value by adding a random number between -50 and 50 to the radius in every iteration of the for loop. The line of code that does that is:

```
 radius = 200 + random.randint(-50, 50)

```

The second modification we will make is to select the color of each triangle at random from a list of colors. The following two lines of code defines our color choices and then selects one color from this list at random.

```
shadesOfGreen =["#006400", "#556b2f", "#8fbc8f", "#2e8b57", "#3cb371", "#20b2aa", "#32cd32"] 
color = random.choice(shadesOfGreen)
```

The list `shadesOfGreen` defines a list of color codes for different shades of green. The next line selects one of the elements of this list at random. The following code incorporates these new elements.

```
def randomPlay():
    '''
    Experiments with the random module
    '''
    shadesOfGreen =["#006400", "#556b2f", "#8fbc8f", "#2e8b57", "#3cb371", "#20b2aa", "#32cd32"] 
    
    t.pensize(10)
    for i in range(36):
        t.up()
        radius = 200 + random.randint(-50, 50)
        x = radius*math.cos(i*10*math.pi/180)
        y = radius*math.sin(i*10*math.pi/180)
        t.goto(x,y)
        t.down()
        tilt = 0
        color = random.choice(shadesOfGreen)
        drawTriangle(50, 50, tilt, "black", color)
``` 
The output of the code is shown in the figure below. Try changing the limits to the random.randint() function and rerun the code, and observe the outcome. Notice how you can control the level of randomness in your drawings using this simple strategy.

![randLoc](randLoc.png){:height="200px"}

Apply what you have learned in this section to complete your `drawForest()` function. Your forest should contain anywhere between 10 and 15 trees of different sizes and different shades of green placed randomly along a horizontal line.

## Step 7: Draw a hut, then a village

Define a function to draw a hut with fixed dimensions, composed of only rectangles. 

```
def drawHut():
    '''
    Draw a brown hut of fixed dimensions purely composed of rectangles
    Use the random module to enhance your drawing by introducing irregularilities in a controlled way
    '''


def drawVillage():
    '''
    Draw a sequence of five huts, placed randomly along a horizontal line
    '''

```

When testing these functions, comment out all calls to previous functions. This will help you focus on the elements of interest in your drawing.

## Step 8: Put it all together

Finally, put all the elements that you have implemented to draw the final scene. 
When you are finished, ask a TA or instructor to look it over and give you some feedback on it.  

It should be structured in a way that there is 

1. A single file called <tt>{{page.num}}.py</tt>
2. Code at the top of the <tt>{{page.num}}.py</tt> file that sets up a turtle
3. Next, function defintions for each of the basic shapes, test code for the basic shapes, `drawTree()`, `testdrawTree()`, `drawForest()`, `drawHut()`, and `drawVillage()`
4. Finally, code that calls those functions to draw the forest scene.  That code should be in a block that starts with `if __name__=="__main__":` as explained later in the lab.


If your code meets all those criteria, you should be in good shape to submit it.


## Step 9: Submitting via submit.cs

Note that this week, although we are using submit.cs, it is NOT the case that the grade you get from submit.cs is your final grade for the assignment.

The grade on submit.cs is just a PART of your grade--you will get 10
points for basically submitting *anything* that is a valid Python
program that has the name <tt>{{page.num}}.py</tt>.

However, the other 90 points for this lab will come from an instructor
or TA doing a manual inspection of your code to see if it complies
with the requirements listed above.

If you want reassurance that your code is in good shape, you may ask a
TA or instructor to look it over during office hours or lab.

To submit your code, use:

### Navigate to the page for submitting {{page.num}}

The page for submitting {{page.num}} is here: <https://submit.cs.ucsb.edu/form/project/{{page.submit_cs_pnum}}/submission>

Navigate to that page, and upload your `{{page.num}}.py` file.

If you are working on the ECI/CSIL/lab linux systems, you can also submit at the command line with this command:

```
~submit/submit -p {{page.submit_cs_pnum}} ~/cs8/{{page.num}}/{{page.num}}.py
```

It will ask for your email address: use your full umail address (e.g. `cgaucho@umail.ucsb.edu`).  For password, use the password that you enter for the submit.cs system.    You may save these credentials if you don't want to have to type them in every time.


Note that if you try to upload a file with a name that does not match EXACTLY the name `{{page.num}}.py`, the system will not allow you to do it. 

Once you upload it, you should get a page that shows your submission is pending.

Refresh that page, and you should get one that indicates with either red, or green, whether the test cases for your code passed or failed.

If you got all green, and 10 points, then your submission was accepted---but to emphasize, for this week, the other 90 points will be assigned by a human grader.   You'll be notified of that grade [via Gauchospace](https://gauchospace.ucsb.edu).

Created by Diba Mirza, thanks to Phill Conrad for his inputs

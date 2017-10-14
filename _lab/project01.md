---
layout: lab
num: project01
ready: true
desc: "Turtle Graphics: Scene from a forest"
assigned: 2017-10-20 11:00:00.00-7
due: 2017-11-09 20:00:00.00-8
submit_cs_pnum: 856
---


Goal
====

The goal of this exercise is to draw a forest scene from basic shape primitives that you implemented in lab03 using turtle graphics. The key learning goals are:

* using functions as building blocks in more complex compositions 
* using loops to perform repetitive tasks while keeping your code DRY (Don't repeat yourself)
* using randomization to create variety and controlled chaos in your drawings
* applying concepts learned in lab04 to creating and using your own modules



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

* Modify the code in basicShapes.py so that you can import the code as a module. Apply the concepts that you learned in lab04 about making your own modules using the `if __name__=="__main__": ` clause. Here are some hints:

- In basicShapes.py, keep all the statements that relate to importing modules and setting up the turtle outside the `if __name__=="__main__:" at the top of the file:

```
import turtle
import math
t = turtle.Turtle()
t.shape("turtle")
t.speed(0)
t.width(4)
```
- Put all other code that is not part of a function definition in the `if __name__=="__main__: clause" 

* Now you are ready to import basicShapes as a module and use its functions: `drawRectangle()` and `drawTriangle()`

* In Idle, open {{page.num}}.py and import your basicShapes module by adding the following line to the top of the file:

```
from basicShapes import *
```

We could have also used the statement <code>import basicShapes</code> to import the code in the file basicShapes.py. In the first case if you were to call a function written within the basicShapes module, you may refer to it simply by its name e.g. `drawRectangle(100, 200, 10, "red", "yellow")`, while with the latter import statement you must use the name of the module each time followed by the dot operator in addition to the function name e.g.: `basicShapes.drawRectangle(...)`



## Step 4: Draw a tree

Using only the two functions available in `basicShapes.py`, we will create the essential elements of our forest scene in code: a function to draw a tree and another to draw a hut. Once we do that, drawing the forest boils down to making repeated calls to these two functions and moving the turtle to a new spot in between function calls. We'll start with writing a function to draw a tree. 


### Write the stub function and test code

Define a 'drawTree()' function as shown below

```
def drawTree(height, color):
    
    ''' 
    This function draws a tree of a given height that consists of a rectangular brown bark and a top comprised of three triangles of a given color stacked on top of each other.
    The bottom left corner of the bark should be at current location of the turtle making no assumptions about the orientation of the turtle.
    After drawing the tree the turtle should be returned to its original position and oriented at 0 degrees 
    All other parameters such as the width of the tree and the length of the bark must be chosen so that the tree is well proportioned. 
    '''

```

* Copy the above code and place it right after the statement `from basicShapes import *` in your project01.py file.
* In the spirit of Test Driven Development (TDD) style of developing your code, think about how you would test your `drawTree()` function. Its natural to inspect the output visually, making sure your tree "looks right" with the expected shape and color. However it may be harder to tell if its drawn with the correct dimensions. To check that write a function `checkTreeHeight()` that helps you visually inspect if your tree is drawn with the specified height by drawing it alongside a rectangle of the same height. Below is one possible implementation of the `checkTreeHeight()` function:

```
def checkTreeHeight():
    t.up()
    t.goto(0,-400)
    t.down()
    drawRectangle(200, 200, 0 , "red","")
    t.seth(0)
    drawTree(200, "green")


if __name__=="__main__":
  checkTreeHeight()
```


If you ran the above code with a correct implementation of `drawTree()` function you should see that the top of the tree coincides with the top side of the rectangle as shown in the following output:

![testTree](testTree.png){:height="200px"}

Note that there are aspects of the tree that are not specified for you such as the width of the tree, the width and height of the bark, and the spacing between the three triangles that make up the tree top. You should make decisions on these aspects relative to the height of the tree so that a taller tree is wider and has a thicker and taller bark.

### Plan out your tree

As always, its good practice to plan out your tree. As you may have noticed your tree is entirely made up of triangles and rectangles which you have already implemented as functions. In your code you will need the coordinates at which you have to draw each of the triangles and rectangles and their respective parameters. Also some of the parameters o fyour tree (like its width) is left for you to decide. Use [this worksheet](/hwk/ic02/) to make decisions about the unspecified aspects of the tree and plan out the grid locations that are important to drawing your tree.


### Implement your `drawTree()` function


Now go ahead and implement your `drawTree()` function. As you do so, add more code to the checkTreeHeight() function to draw at least two well-proportioned trees of different heights at two different locations.  

## Step 5: Draw a row of trees - repetition made easy with loops

We would now like to go from drawing one or two trees to many trees, which will eventually become our forest. To begin define the function `drawForest()` as below:

```
def drawForest():
    ''' 
    Draws a collection of trees placed at random locations within a rectangular region
    '''
```

Getting to a solution is an iterative process. Attempt a simpler version of the `drawForest()` function that would help you progress towards a final solution. Its up to you to define 'a simpler version of the forest'. I might start by making a forest that comprises of just three trees of the same height placed in a row with equal spacing between them. For now, follow along because this simpler solution is a good segway to learning a very important programming concept: loops


One way of drawing a row of trees that are equally spaced from each other is to repeat a block of code that moves the turtle to a specific spot and then calls the `drawTree()` function. Recall that we did a similar thing with rectangles in lecture. This is shown below:

```
# Move the turtle to location (-200, -100) and draw a tree  
t.up()
t.goto(-200, -100)  
t.seth(0)
t.down()
drawTree(200, "green")

# Move the turtle to location (0, -100) and draw another tree
t.up()
t.seth(0)
t.forward(200)
t.down()
drawTree(200, "green")

# Move the turtle to location (200, -100) and draw the third tree
t.up()
t.seth(0)
t.forward(200) 
t.down()
drawTree(200, "green")

```
A (better) alternative is to use a for loop as shown below:

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

def regularPlay():
    '''
    A circle of triangles
    '''
    t.pensize(10)
    for i in range(36):
        t.up()
        radius = 200
        x = radius*math.cos(i*10*math.pi/180)
        y = radius*math.sin(i*10*math.pi/180)
        t.goto(x,y)
        t.down()
        drawTriangle(50, 50, "black", "red")

regularPlay()
```

When you run the above code, you should find a very regular arrangement of triangles along a circle as shown below. Read the code to understand why its producing this output. Note that the location of each triangle is dependent on the value of our loop variable `i`. 

![circleOfTris](circleOfTris.png){:height="200px"}


We will next use the random module to randomize two aspects of our drawing: the location of each triangle and its color. Previously, we drew all our triangles along a circle of radius 200. This time we will introduce a small random perturbation in that value by adding a random number between -50 and 50 to the radius in every iteration of the for loop. The line of code that does that is:

```
 radius = 200 + random.randint(-50, 50)

```

The second modification we will make is to select the color of each triangle at random from a list of colors. The following two lines of code defines our color choices and then selects one color from this list at random.

```
shadesOfGreen =["#006400", "#556b2f", "#8fbc8f", "#2e8b57", "#3cb371", "#20b2aa", "#32cd32"] # A list of color codes for different shades of green
color = random.choice(shadesOfGreen) # select one of the elements of the list at random
```

Now copy the following function into your file, read it and then run it

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
        color = random.choice(shadesOfGreen)
        drawTriangle(50, 50, "black", color)
``` 
The output of the code is shown in the figure below. Try changing the limits to the random.randint() function and re-run the code, and observe the outcome. Notice how you can control the level of randomness in your drawings using this simple strategy.

![randLoc](randLoc.png){:height="200px"}

Apply what you have learned in this section to complete your `drawForest()` function. Your forest should contain anywhere between 10 and 15 trees of different sizes and different shades of green placed randomly along a narrow horizontal region.

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

## Step 9: Make it your own! 

We have 10 points reserved for you to add new elements to your forest and get creative. Define new functions to your file and call them in the `if __name__=="__main__" block to make te forest scene your own!!


It should be structured in a way that there is 

1. A single file called <tt>{{page.num}}.py</tt>
2. Code at the top of the <tt>{{page.num}}.py</tt> file that sets up a turtle
3. Next, function defintions for each of the basic shapes, test code for the basic shapes, `drawTree()`, `checkTreeHeight()`, `drawForest()`, `drawHut()`, and `drawVillage()` and any other functions that you like to add.
4. Finally, code that calls those functions to draw the forest scene.  That code should be in a block that starts with `if __name__=="__main__":` as explained later in the lab.


If your code meets all those criteria, you should be in good shape to submit it.


## Step 10: Submitting via submit.cs

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

---
num: "e01-actual"
desc: "Midterm 1 actual"
ready: true 
assigned: 2017-10-24 12:30:00.00-7:00
due: 2017-10-24 13:45:00.00-7:00
---

{% include exam-name-header-template.html%}

<ol>


<li markdown="1">

Problem 1: [20 points] Generalizing a function

In the left column below, there is a function definition for drawU. In the right column, there is Python code that uses that function definition to draw the letter U, and a picture of the resulting drawing.

In the version below, the width and height of the U are hard coded: width is 50 and height is 100
Also, please note that the turtle ends up exactly where it started, facing the same way, with the pen down
Your job is to rewrite in your answer sheet the function definition so that it can draw a U of any width or height.
Your new function should work for the functions calls below, producing output like that shown:
Helpful hints (how to get full credit):

The drawU function given starts with the Turtle at the lower left hand corner of the U, facing right, and ends with the Turtle at the same spot. Your function should also do that, even after you generalize it. (Points will be deducted if it doesn't.)

* Focus only on rewriting the drawU function:
* Don't worry about things like import turtle, or fred=turtle.Turtle("turtle") or any of that other stuff, which is not relevant to the problem I'm asking you solve here.
* You won't get any extra points for including that stuff
* I only want the function definition for the re-written drawU function—nothing more, nothing less.
* For full credit, include the comments from the original function definition

</li>

<li markdown="1">

Problem 2 [10 points]: Consider the following functions that you implemented as part of lab03 to draw a rectangle and triangle of any size and color:

```
drawRectangle(width, height, tilt, penColor, fillColor)
drawTriangle(base, height, penColor, fillColor)
```

As a reminder, the following outputs are produced by the 




<style>
div.bigger table * td { padding: 0.7em 3pt 0.7em 3pt; }
span.wide { padding: 0pt 4em 0pt 4em; }
</style>

<div class="bigger" markdown="1">

| Points  | Expression  | <span class="wide">Result</span> | Points  | Expression  | <span class="wide">Result</span> |
|---------|-------------|--------|---------|-------------|--------|
| (4 pts) | `2 + 3 * 5` |        | (4 pts) | `4 < 3`     |        |
| (4 pts) | `19 % 3`    |        | (4 pts) | `1 + 2 == 3`|        |
| (4 pts) | `5 ** 2`    |        | (4 pts) | `True and False`  |        |
| (4 pts) | `7 // 2`    |        | (4 pts) | `True or False`  |        |
| (4 pts) | `9 // 2`    |        | (4 pts) | `5 != 10//2`    |        |

</div>
<div class="pagebreak"></div>
</li>


<li style="margin-bottom:5em;" markdown="1">
(5 pts) As described in section 2.1, a Python assignment statement contains the assignment operator, an expression and a variable, but not in that order.

What is the correct order for these three parts, reading from left to right?

</li>


<li style="margin-bottom:5em;" markdown="1">
(5 pts) Section 2.1 contains a list of thirty-three <em>reserved words</em> in Python that may not be used as the name of a variable.   You don't need to memorize this list, but you do need to know where to find it, either in the book, or online.  So, to be sure you can find it, list all of the Python reserved words that start with the letter `c` or `f`.
</li>

<li style="margin-bottom:5em;" markdown="1">
Section 2.2 describes strings in Python, including the concepts of "dictionary order" (also called "lexicographic order"), concatenation of strings, multiplication of strings times an integer, the `in` operator, the `not in` operation, the `len` function, and string indexing.  Review that material.

Then, assuming the following assignment statements have been entered at the Python prompt:

```python
school = "UCSB"
course = "CS8"
qtr = "F17"
```

Indicate the value of each of these expressions:

<style>
div.evenbigger table * td { padding: 2em 1pt 2em 1pt; text-align: center; }
div.evenbigger table * th { padding: 0em 1pt 0em 1pt; margin: 0 0 0 0;
  text-align:center;}
div.evenbigger table * td code { padding: 0pt 1em 0pt 1em; }
span.wider { padding: 0pt 6em 0pt 6em; }
</style>


<div class="evenbigger" markdown="1">

| | Expression  | <span class="wider">Result</span> | | | Expression  | <span class="wider">Result</span> |
|---------|-------------|--------|-|--------|-------------|--------|
| (4 pts) | `school * 2`        |  | | (4 pts) | `school > course` | |
| (4 pts) | `qtr[1:3]`          |  | |(4 pts) | `qtr < school`   | |
| (4 pts) | `course[0:2]`        |  | |(4 pts) | `len(qtr) > 4`   | |
| (4 pts) | `'D' in school`     |  | |(4 pts) | `school[-1]`     | |
| (4 pts) | `'E' not in school` |  | |(4 pts) | `school[0]`      | |

</div>


</li>


</ol>


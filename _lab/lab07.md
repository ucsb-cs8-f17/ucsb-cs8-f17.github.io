---
layout: lab
num: lab07
ready: false
desc: "Scrabble word finder: Python lists, dictionaries and file I/O"
assigned: 2017-11-21 8:00:00.00-7
due: 2017-11-28 17:00:00.00-8
submit_cs_pnum: 830
---

## To do: Adapt this lab to build on the TDD style of coding using pytest, set up submit.cs

## You may pair or work alone on this lab.

If you choose to pair, please start by registering your pair on submit.cs in the normal way.  Go to 
<https://submit.cs.ucsb.edu>, log on, navigate to the link for {{page.num}}, then follow the links to invite your pair partner to form a group.   Make sure your pair partner logs in and accepts your invitation.

## Goals for this lab

The goals for this lab are:

* more practice using Python lists
* practice using Python dictionaries
* read data (words) from a text file and put them into a list
* create a Scrabble word finder
* use list method sort() to sort words in order of descending point value
* print formatted output to the screen
* write formatted output to a file

## Getting started


* Step 1: Log on & bring up a terminal window
This is done following the steps you have performed in lab00.
* Step 2: Create a directory in your cs8 directory named {{page.num}}. 
* Step 3: Start IDLE

The terminal command for this is idle3.  When you have the IDLE window up, you are ready for some programming! 

 
## What to program?

In this lab assignment, you are going to make your own Scrabble word finder function, `scrabbleWords()`.  In the end, you will simply input a string of letters and the program will print out (to the screen and to a file) a list of all the possible words you can make along with their point values in descending order (neglecting things like triple letter, double word squares, etc. in the real game of Scrabble).  For example, if I input 'bouni' as my string of letters, this is what I get:

```
>>> scrabbleWords('buoni')
obi      5
nub      5
nob      5
nib      5
bun      5
bio      5
bin      5
bi       4
uni      3
ion      3
on       2
nu       2
no       2
in       2
u        1
i        1
```

So, how did our program know which letter combinations were valid words?......We have to specify a file of words, which you can find here: [wordlist.txt](wordlist.txt){:data-ajax="false"} .  This file must be downloaded (right click and "save as") and put into your {{page.num}} directory before you begin, so do that now.  Note that this file contains a fairly complete list of English words, so beware that there may be some expletive and/or raunchy words - please don't hold me personally responsible if you are offended.  Perhaps this will be motivation for some of you to complete the assignment.  

 

### Functions to Implement:

1. createWordList(filename) - return L
2. canWeMakeIt(myWord, myLetters) - return True or False
3. getWordPoints(myWord, letterPoints) - return points
4. scrabbleWords(myLetters) - NO return (just prints a formatted list and writes to file)

 

### Function Details:

1. createWordList(filename) - return L.  Write a function which reads the file filename and returns a list L containing all the words in the file.  Note that the last character of every line of the file is the invisible "new line" character '\n' and needs to be sliced off.

 

2. canWeMakeIt(myWord, myLetters) - return True or False.  Write a function which answers the question: Can I form the word myWord from the string of letters myLetters?  The function should return a boolean True or False.  Converting myLetters to a list and using the pop() or remove() method may come in handy.

 

3. getWordPoints(myWord, letterPoints) - return points.  Write a function that calculates and returns the total point value of myWord given the Python dictionary object letterPoints which consists of letter:pointValue pairs.  Note that you do not need to create the letterPoints dictionary in this step - it is a parameter to our function and will be created in part 4.

 

4. scrabbleWords(myLetters) - NO return (just prints a formatted list and writes to file).  Here you will call upon your "helper functions" created in steps 1-3 to form a list of all the words (from wordlist.txt) that can be formed from the set of letters contained in myLetters. 

* Create a Python list of words from wordlist.txt and name it wordList.  You will want to call helper function createWordList.

* Create a list of all the words that we can make with myLetters by looping through every word in wordList and checking if it can be made with myLetters - name this list myWords.  You will want to call helper function canWeMakeIt.

* Create a dictionary of letter:pointValue pairs - name it letterPoints.  The image below shows the Scrabble point value for each letter, but note that your dictionary keys should be the lower case letters.

![letter points](scrabble_letters.png){:height="200px"}

* Create a list of tuples consisting of (pointValue, word) pairs by looping through the list myWords and getting the point value for each word - name this list of tuples pointWordList.  To calculate pointValue, you will want to call helper function getWordPoints.

* Sort pointWordList in descending order.  Now, you can use the list method sort() to sort the tuples according to their first entry, pointValue.  But sort() arranges a list in ascending order by default....can you think of a way to reverse this?

* Print all the words followed by their point value.  Format the output so that your word is left justified in a field of width 4 more than the number of letters in myLetters, and the point value follows immediately afterwards.  You can do this with the format string method by carefully forming the '{...}' string first.  Hint: Use string concatenation with str(len(myLetters) + 4).

* Write the same text as your formatted screen output from Part 5 to a text file.  Name the file the string of letters contained in myLetters followed by .txt.  So in my example where I call scrabbleWords('buoni'), the file that is created is buoni.txt.  Note that every time you want to write to a new line, you will need to include the newline character '\n' in your file.write() statement.  You can see what the output should look like in the example here: buoni.txt.  Do not download this file, but simply verify that when you run your program you produce this same file.

 

\(^_^)/, you're finished!  Now have fun and experiment with the word finder ;-).

# Submission

## Navigate to the page for submitting {{page.num}}

The page for submitting {{page.num}} is here: <https://submit.cs.ucsb.edu/form/project/{{page.submit_cs_pnum}}/submission>

Navigate to that page, and upload your `{{page.num}}.py` file.

# Submission from CSIL command line

If you are working on the ECI/CSIL/lab linux systems, you can also submit at the command line with this command:

<tt>~submit/submit -p {{page.submit_cs_pnum}} ~/cs8/{{page.num}}/{{page.num}}.py</tt>

Notes on using the command line version of submit:

* This ONLY works on CSIL.  From your own PC or Mac, use the web form for submission.

* The first time you use the `~submit/submit ...` command (or every time if you choose not to save your credentials) you will be asked for your email address: use your full umail address (e.g. `cgaucho@umail.ucsb.edu`).  For password, use the password that you enter for the submit.cs system.    You may save these credentials if you don't want to have to type them in every time.

* Note that if you try to upload a file with a name that does not match EXACTLY the name `{{page.num}}.py`, the system will not allow you to do it.   Once you upload it, you should get a page that shows your submission is pending.  Refresh that page, and you should get one that indicates with either red, or green, whether the test cases for your code passed or failed.

Thanks to Matt Buoni for this lab!
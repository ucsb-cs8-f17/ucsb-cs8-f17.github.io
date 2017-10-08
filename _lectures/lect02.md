---
num: "Lecture 2"
desc: "Python data and functions"
ready: false
date: 2017-08-09 09:30:00.00-7:00
---

# Code from today's lecture


# Questions and Answers

* Q: Installing Python?
* A: Visit http://python.org/download

# lab00 and lab01

* lab00 is now ready for you to work on it.
* Eventually, we'll explain how to work on labs on your own computer.
   * If you want a head start on that, come to office hours with your laptop, and we'll go over it with you.
* For now, if you want to work on it before Tuesday lab
   
# Python Data Types

`int`, `float`, `str`, `list`, `tuple`, `dict`

'''
Anything between three single-quotes (or double quotes) is considered
a comment
'''

''' Variables
    - Variables are useful for storing values of any type.
    - There are many "types" in Python, programmers can also create custom ones
    - Types are important depending on what you need to do with the data.
        - Some types suport certain functionality while others don't.
        - Using certain types can affect the performance of your program.
    - Names of variables must...
        - Start with a letter or underscore (the former is more common)
        - Remaining letters in variables names can consist of letters, numbers,
           or underscores
        - Names are case-sensitive (name and NAME are considered two different
           variables).

x = 10
print(x)
x = x * 10 # 10 * current value of x is stored back into x
print(x)

'''

''' Some Python Data Types
    - int: Integers representing non-decimal values
    - float: Floating point number representing a decimal (fractional) value
    - string - Represents a collection of characters
        - Ex: 'A', 'a', '1', ' ', '-'
    - Note: 3 and 3.0 are considered different types!
        - 3 is an integer (non-decimal value)
        - 3.0 is a float (decimal value, even if the decimal is 0)
    - Python automatically knows what type these numbers are based on its value.

x = 1
print(x)
print(type(x))

#x = 4 / 2
x = 4 * 2.0
print(x)
print(type(x))

x = "CS 8"
print(x)
print(type(x))

x = "8.0"
print(x)
print(type(x))

x = float(x) + 5
print(x)
'''
''' Indexing strings and substrings
    - In a string, we can extract certain pieces from it.
    - This is also known as "parsing" a string
    - Positions in a string start at index 0

schoolName = "UCSB"
print(len(schoolName))
print(type(schoolName))
print(schoolName[0])
print(schoolName[3])
#print(schoolName[4]) # Error!
print(schoolName[-1])
#print(schoolName[-5])
# Extracting a substring
print(schoolName[1:3]) # CS (from position 1 up to (but not including) pos 3)
'''

''' Lists
    - A list is a collection of multiple values (similar to how a str is a
      collection of characters)
        - Note: In python, lists can be of heterogenous (different) types
        - Lists can have duplicate values.

evenNumbers = [2, "4", 6, "8"]
print(evenNumbers)
print(type(evenNumbers))
print(evenNumbers[2])
print(evenNumbers[-1])
evenNumbers.append(10)
print(evenNumbers)
print(int(evenNumbers[1]) + evenNumbers[2])

print(evenNumbers.pop(1))
print(evenNumbers)


names = ["Rick", "Morty", "Summer", 1, 2]
print(names[1], names[3])
print(names[3] + names[4]) # 3
#print(names[0] + names[4]) #ERROR
names.pop()
names.pop()
names.sort()
print(names)
'''

''' Tuples
    - A tuples is similar to a list, but with small (but important) differences
    - Certain built-in functionality (list sort()) works for lists, but not
       tuples
    - inherently, tuples and lists are different, but logically seem the same.
    - can change an element in a list, but cannot change them in a tuple
'''

oddNumbers = (1,3,5,7)
print(type(oddNumbers))
print(oddNumbers[1])
#oddNumbers.sort() # ERROR

oddNumbers2 = [1,3,5,7]
oddNumbers2[2] = 9
print(oddNumbers2)
#oddNumbers[2] = 9 # ERROR! Cannot replace item in tuples
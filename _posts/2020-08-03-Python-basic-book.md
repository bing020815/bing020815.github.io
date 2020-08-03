---
layout: post
title: "Pyhon Baisc: PYTHON FOR EVERYBODY"
date: 2020-08-03
theme: minimal
mathjax: true
categories: Python
---
<div id='top'>
  <p align="center"><img src="{{site.baseurl}}/assets/images/post/python/python-basic.png" title=""></p>
  <p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">Pyhon Baisc: <a href="https://www.amazon.com/Python-Everybody-Exploring-Data/dp/1530051126">PYTHON FOR EVERYBODY</a></p>
</div>

## Table of contents:  
* [Chapter 1. Introduction](#introduction) 
* [Chapter 2. Variables](#variables)  
* [Chapter 3. Conditional Execution](#conditional-execution)  
* [Chapter 4. Functions](#functions)  
* [Chapter 5. Iteration](#iteration)  
* [Chapter 6. Strings](#strings)  
* [Chapter 7. Files](#files)  
* [Chapter 8. List](#list)  
* [Chapter 9. Dictionaries](#dictionaries)  
* [Chapter 10. Tuples](#tuples)  

<br>

## Introduction
### Errors
In python, there are three general type of errors:
  + Syntax errors 
    - Violated the "grammar" rules of python.
  + Logic errors
    - A mistake in the order of the statements.
  + Semantic errors
    - The program is perfectly correct but it does not do what you intended for it to do.

### Debugging
1. Reading
2. Running
3. Ruminating
 + syntax
 + runtime
 + semantic
4. retreating

<br>

## Variables
### Data Type
* String: str
* Integers: int
* Number with a decimal point: float  

__PS__: Variable name cannot start with a number

{% highlight python %}
# This is a statement/assignment:
x = 2
{% endhighlight %}

{% highlight python %}
# This is a script:
print(1)
print(x)
{% endhighlight %}


### Operation
* *Order of operations:*  
Python follows the order of operations, PEMDAS, (Parenthese, Exponentiation, Multiplication, Division, Addition, Substraction)

* *Modulus Operator:*  
{% highlight python %}
quotient = 7 //3
print(quotient)
{% endhighlight %}
```
2
```

{% highlight python %}
remainder = 7 % 3
print(remainder)
{% endhighlight %}
```
1
```

* *String Operation:*
{% highlight python %}
# Case 1
first = '100'
second = '150'
print(first + second)
{% endhighlight %}
```
100150
```
{% highlight python %}
# Case 2
first = 'Test'
second = 3
print(first * second)
{% endhighlight %}
```
TestTestTest
```

<br>

## Conditional Execution
### Bools
* Boolean Expression: TRUE/FALSE
* Data Type: bool

### Operation
* Logical Operator:
  + and
  + or
  + not

Condition expression tables:

|x != y|x is not equal to y|
|x > y|x is greater than y|
|x < y|x is less than y|
|x >= y|x is greater than or equal to y|
|x <= y|x is less than or equal to y|
|x is y|x is the same as y|
|x is not y|x is not the same as y|
|x == y|x is equal to y|

{% highlight python %}
inp = input("Enter Fahrenhiet:")
try:
    fahr = float(inp)
    cel = (fahr-32.0) * 5.0/9.0
    print(cel)
except:
    print(cel)
{% endhighlight %}
```
Enter Fahrenhiet:123
50.55555555555556
```
<br>

## Functions  
A function is a named sequence of statements that performs a comptation.

### Built-in function
* max: In a string, Z would be the largest one
* min: In a string, a space would be the smallest
* len: In a string, returns the # of characters

### Conversion functions
* int
  + Takes any value and converts it to an integer if it can
  + It can convert floating-point values to integers but it does not round off
  + It will chops off the fraction part
* float
  + It converts integers and strings to floating-point numbers
* str
  + It converts its argument to a string

### Math functions
A 'math' module needs to be imported by using:
{% highlight python %}
import math
{% endhighlight %}
* A module contains the functions and variables defined in the module.
* To access one of the function, you have to specify the name of the module and the name of the function, separted by a dot

{% highlight python %}
ratio = 12/24
result = 10 * math.log10(ratio)
print(result)
{% endhighlight %}
```
-3.010299956639812
```

{% highlight python %}
radians = 0.7
height = math.sin(radians)
print(height)
{% endhighlight %}
```
0.644217687237691
```

{% highlight python %}
degrees = 45
radians = degrees/360.0*2*math.pi
math.sin(radians)
{% endhighlight %}
```
0.7071067811865475
```

### Random numbers
* random: (From __random__ module)
  + It returns a random float between 0.0 and 1.0 (including 0.0 but not 1.0)
* randint
  + It takes the parameters 'low' and 'high' and returns an integer between 'low' and 'high'
* choice
  + It choose an element from a sequence at random

{% highlight python %}
# random
import random
for i in range(10):
    x = random.random()
    print(x)
{% endhighlight %}
```
0.7305591062488854
0.8859907707980562
0.449918375542002
0.7643633082695483
0.42944509322878277
0.8951958910887714
0.3319489418362195
0.11402093233851263
0.7428676466169906
0.9881847290549769
```

{% highlight python %}
# randint
random.randint(5,10)
{% endhighlight %}
```
8
```

{% highlight python %}
# randint
random.randint(5,10)
{% endhighlight %}
```
7
```

{% highlight python %}
# choice
t = [1,2,3]
random.choice(t)
{% endhighlight %}
```
3
```

{% highlight python %}
# choice
random.choice(t)
{% endhighlight %}
```
1
```
The __random__ module also provides functions to generate random values form continuous distributions inclusing "Gaussian", "exponential", "gamma" and a few more.


### Define a new function  
A function definition specifies the name of a new function and the sequence of statements that exceute when the function is called.
* `def`: It indicates that this is a function definition

{% highlight python %}
def print_lyrics(): 
    print("I'm a lumberjack, and I am okay.")
    print('I sleep all night and I work all day.')
print_lyrics()
{% endhighlight %}
```
I'm a lumberjack, and I am okay.
I sleep all night and I work all day.
```
* Defining a function also create a variable with the same name.
* The value of the function is a function object, which has type "function"
* Function can be used inside another function
* The statements inside the function do not get executed until the function is called

A function that can yeild a result is called __fruitful functions__; on the other hand, a function that can perform action but don't return a value  is called __void functions__. 
* Void function might display something on the screen or have some other effects but they do not have a return value.
* If you try to assign the result from a void function to a variable, you will get a speial value called "None"
{% highlight python %}
def print_twice(string):
    print(string)
    print(string)

result = print_twice('test') 
{% endhighlight %}
```
test
test
```

{% highlight python %}
# nothing was assigned to the result variable
print(result) 
{% endhighlight %}
```
None
```
In order to return a result from a function, use "`return`" statement.
{% highlight python %}
def addtwo(a,b):
    added = a+b
    return added
    
x = addtwo(3,5)
print(x)
{% endhighlight %}
```
8
```

<br>

## Iteration
### Loops
Python has three iteration/loops functions:
* if - looping with conditions
* for - looping through a know set of items
* while - loops until some condition becomes False

{% highlight python %}
# The script has five iterations:
n = 5
while n > 0:
    print(n)
    n = n-1
print('blast off')
{% endhighlight %}
```
5
4
3
2
1
blast off
```
### Endless Loop
The  `while True` statement creates an endless loops:
{% highlight python %}
while True:
    line = input('> ')
    if line == 'done':
        break
    print(line)
print('Done!')
{% endhighlight %}

<br>

## Strings
String literals in python are surrounded by either single quotation marks, or double quotation marks. `'hello'` is the same as `"hello"`. Each string has its index. The expression in brackets is called an index. Index starts from 0 to n-1. n is the length of a string.

{% highlight python %}
fruit = 'banana'
letter = fruit[1]
print(letter)
{% endhighlight %}
```
a
```

Getting the length of string using `len()`:
{% highlight python %}
fruit = 'banana'
len(fruit)
{% endhighlight %}
```
6
```

{% highlight python %}
length=len(fruit)
last = fruit[length-1]
print(last)
{% endhighlight %}
```
a
```

### Negative indices
Index can be expressed as a negative number:
{% highlight python %}
fruit[-1]
{% endhighlight %}
```
'a'
```

{% highlight python %}
length=len(fruit)
fruit[-2]
{% endhighlight %}
```
'n'
```

### Loops application
Use while loop to write a traversal:
{% highlight python %}
index=0
while index < len(fruit):
    letter = fruit[index]
    print(f'{index}: {letter}')
    index = index + 1
{% endhighlight %}
```
0: b
1: a
2: n
3: a
4: n
5: a
```

Use for loop to write a traversal:
{% highlight python %}
for char in fruit:
    print(char)
{% endhighlight %}
```
b
a
n
a
n
a
```

Use while loop to write a reverse traversal:
{% highlight python %}
index = 1
while index-1 < len(fruit):
    letter = fruit[-index]
    print(f'{index}: {letter}')
    index = index + 1
{% endhighlight %}
```
1: a
2: n
3: a
4: n
5: a
6: b
```
### String slices
Selecting a slice is similar to selecting a character.
{% highlight python %}
s = 'Monty Python'
print(s[0:5])
print(s[6:12])
{% endhighlight %}
```
Monty
Python
```
The operator returns the part of the sting from the '*n-th*' to '*m-th*' character, including the first but excluding the last.
{% highlight python %}
fruit = 'banana'
fruit[:3]
{% endhighlight %}
```
'ban'
```

{% highlight python %}
fruit[3:]
{% endhighlight %}
```
'ana'
```

If the first index is greater than or equal to the second the result is an empty string.
{% highlight python %}

fruit = 'banana'
fruit[3:3]
{% endhighlight %}
```
''
```

The best you can do is create a new string that is a variation on the original:
{% highlight python %}
greeting = 'Hello World!'
new_greeting = 'J' + greeting[1:]
print(new_greeting)
{% endhighlight %}
```
Jello World!
```
### Looping and counting
Using loop to count charactors:
{% highlight python %}
word = 'banana'
count = 0
for letter in word:
    if letter == 'a':
        count = count + 1
        print(count)
{% endhighlight %}
```
1
2
3
```
### The 'in' operator
{% highlight python %}
'a' in 'banana'
{% endhighlight %}
```
True
```

{% highlight python %}
'seed' in 'banana'
{% endhighlight %}
```
False
```
### String comparison
{% highlight python %}

word = 'banana'
if word == 'banana':
    print('All right, bananas')
{% endhighlight %}
```
All right, bananas
```

### String Methods
* There are string methods can be used
  + __dir__: shows the available methods
  + __type__: type of an object

{% highlight python %}
# check object type
stuff = 'hello world'
type(stuff)
{% endhighlight %}
```
str
```

{% highlight python %}
dir(stuff)
{% endhighlight %}
```
['__add__',
 '__class__',
 '__contains__',
 '__delattr__',
 '__dir__',
 '__doc__',
 '__eq__',
 '__format__',
 '__ge__',
 '__getattribute__',
 '__getitem__',
 '__getnewargs__',
 '__gt__',
 '__hash__',
 '__init__',
 '__init_subclass__',
 '__iter__',
 '__le__',
 '__len__',
 '__lt__',
 '__mod__',
 '__mul__',
 '__ne__',
 '__new__',
 '__reduce__',
 '__reduce_ex__',
 '__repr__',
 '__rmod__',
 '__rmul__',
 '__setattr__',
 '__sizeof__',
 '__str__',
 '__subclasshook__',
 'capitalize',
 'casefold',
 'center',
 'count',
 'encode',
 'endswith',
 'expandtabs',
 'find',
 'format',
 'format_map',
 'index',
 'isalnum',
 'isalpha',
 'isdecimal',
 'isdigit',
 'isidentifier',
 'islower',
 'isnumeric',
 'isprintable',
 'isspace',
 'istitle',
 'isupper',
 'join',
 'ljust',
 'lower',
 'lstrip',
 'maketrans',
 'partition',
 'replace',
 'rfind',
 'rindex',
 'rjust',
 'rpartition',
 'rsplit',
 'rstrip',
 'split',
 'splitlines',
 'startswith',
 'strip',
 'swapcase',
 'title',
 'translate',
 'upper',
 'zfill']
```

{% highlight python %}
help(str.capitalize)
{% endhighlight %}
```
Help on method_descriptor:

capitalize(...)
    S.capitalize() -> str
    
    Return a capitalized version of S, i.e. make the first character
    have upper case and the rest lower case.
```

Calling a method is similar to calling a function but the syntax is different:

1. upper
2. find
3. strip
4. lower
5. startswith
6. count

{% highlight python %}
# upper
word = 'banana'
new_word = word.upper()
print(new_word)
{% endhighlight %}
```
BANANA
```

{% highlight python %}
# find
word.find('na')
{% endhighlight %}
```
2
```

{% highlight python %}
# find (setting the index where it should start)
word.find('na', 3)
{% endhighlight %}
```
4
```

{% highlight python %}
# strip: get rid of leading and trailing spaces
line = ' Here we go             '
line.strip()
{% endhighlight %}
```
'Here we go'
```

{% highlight python %}
# lower
line = 'Have a nice day'
line.lower()
{% endhighlight %}
```
'have a nice day'
```

{% highlight python %}
# startswith
line = 'Have a nice day'
line.startswith('h')
{% endhighlight %}
```
False
```

{% highlight python %}
line.startswith('H')
{% endhighlight %}
```
True
```

{% highlight python %}
# count
line.count('e')
{% endhighlight %}
```
2
```

### Parsing strings
{% highlight python %}
data = ' from abc@this.is.test Sat Jan 23:45:67 2019'
atpos = data.find('@')
stoppos = data.find(' ', atpos) # find the position of the blank starting the search from the position of at sign
host = data[atpos +1 :stoppos]
print(host)
{% endhighlight %}
```
this.is.test
```

### Format operator
The format operator, `%`, allows us to construct strings, replacing parts of the strings with the data stored in variables. `%d` means that the second operand should be formatted as an integer:

{% highlight python %}
camels=42
"I have spotted %d camels" %camels
{% endhighlight %}
```
'I have spotted 42 camels'
```

Other format operators, such as `%g` is to format a floating-point number and `%s` is to format a string: 
{% highlight python %}
'In %d years, I have spotted %g %s.' %(3, 0.1, 'camels')
{% endhighlight %}
```
'In 3 years, I have spotted 0.1 camels.'
```
<br>

## Files
### Use open()

Count each of the lines in a files:
{% highlight python %}
fhand = open('inbox-short.txt')
count = 0
for line in fhand:
    count = count +1
    print('Line count:', count)
{% endhighlight %}

If the file is relatively small compared to the size of your main memory, using the 'read' method on the file handle.
{% highlight python %}
fhand = open('inbox-short.txt')
inp = fhand.read()
{% endhighlight %}

If the file is too large to fit in main memory, you should write your program to read the file in chunks using a for or while loop.
{% highlight python %}
fhand = open('inbox-short.txt')
count = 0
for line in fhand:
    line = line.strip()
    if line.startswith('From:'):
        print(line)
{% endhighlight %}

As the file processing programs get more complicated, you may want to structure your search loops using "continue"
{% highlight python %}
fhand = open('inbox-short.txt')
count = 0
for line in fhand:
    line = line.strip()
# skip 'uninteresting lines'
    if not line.startswith('From:'):
        continue
# process the 'interesting lines'
    print(line)
{% endhighlight %}

 * find() return -1 if the string was not found
{% highlight python %}
fhand = open('inbox-short.txt')
count = 0
for line in fhand:
    line = line.strip()
    if line.find('@utc.ac.za')==-1:
        continue
    print(line)
{% endhighlight %}

 * try/except for reading file program
{% highlight python %}
fname = input('Enter the file name:')
try:
    fhand=open('inbox-short.txt')
except:
    print('File cannot be opened', fname)
    exit() # terminate the program
count = 0
for line in fhand:
    line = line.strip()
# skip 'uninteresting lines'
    if not line.startswith('Subject:'):
        count= count + 1
print('There were', count, 'subject lives in', fname)
{% endhighlight %}

### writting files
To write a file, you have to open it with mode "w" as a second parameter:
{% highlight python %}

# If the file already exists, opening it in write mode clears out the old data and starts fresh
# + sign allow the 'read' mode
fout = open('output.txt','w+')
print(fout)
{% endhighlight %}
```
<_io.TextIOWrapper name='output.txt' mode='w+' encoding='UTF-8'>
```

The 'write' method of the file handle object puts data into the file, returning the number of characters written.
{% highlight python %}
line1='This is test line\n'
fout.write(line1)
{% endhighlight %}
```
18
```

{% highlight python %}
for line in fout:
    line = line.strip()
    print(line)
{% endhighlight %}
```
This is test line
```

Close the file when writting is done.
{% highlight python %}
fout.close()
{% endhighlight %}

Spaces, tabs, and newlines can be treated as a string by using 'repr'
{% highlight python %}
s='1 2\t 3\n 4'
print(f'Without "repr":\n{s}\n')
print(f'With "repr":{repr(s)}')
{% endhighlight %}
```
Without "repr":
1 2  3
 4

With "repr":'1 2\t 3\n 4'
```
<br>

## List
A list is a sequence of values (elements/items).

* In a string: values are characters
* In a list: values can be any type
* Example: [10, 20, 30, 40]

A list within another list is nested. A list that contains no elements is called an empty list.  
Example:  
* []
* ['Spam', 2.0, 5, [10,20]]

Here, `'Spam'` is string type; `2.0` is float type, `5` is integer; and `[10,20]` is a list.

Functions can be used for list: 
* len(): returns the number of elements in the list
* range(): returns a list of indices from 0 to n-1

### Lists are mutable
{% highlight python %}
# Define a list
cheeses = ['cheddar', 'Edam' , 'Gouda']
# assign a value to the list
cheeses[0] = 'Cheddar'
# call the lis
cheeses
{% endhighlight %}
```
['Cheddar', 'Edam', 'Gouda']
```

### List operation
{% highlight python %}
# Concatenation
a=[1,2,3]
b=[4,5,6]
c=a+b
print(c)
{% endhighlight %}
```
[1, 2, 3, 4, 5, 6]
```

{% highlight python %}
# Repetition
[0]*4
{% endhighlight %}
```
[0, 0, 0, 0]
```

{% highlight python %}
# Repetition
[1, 2, 3]* 3
{% endhighlight %}
```
[1, 2, 3, 1, 2, 3, 1, 2, 3]
```

{% highlight python %}
# Membership
1 in [1,2,3]
{% endhighlight %}
```
True
```

{% highlight python %}
# Iteration
for x in [1, 2, 3]: 
    print(x)
{% endhighlight %}
```
1
2
3
```

{% highlight python %}
# Length
len([1, 2, 3])
{% endhighlight %}
```
3
```

### List slices

{% highlight python %}
t = ['a', 'b', 'c', 'd', 'e', 'f']
t[1:3]
{% endhighlight %}
```
['b', 'c']
```

{% highlight python %}
t[:4]
{% endhighlight %}
```
['a', 'b', 'c', 'd']
```

{% highlight python %}
t[:]
{% endhighlight %}
```
['a', 'b', 'c', 'd', 'e', 'f']
```

{% highlight python %}
t[-1]
{% endhighlight %}
```
'f'
```

{% highlight python %}
t[:-1]
{% endhighlight %}
```
['a', 'b', 'c', 'd', 'e']
```

{% highlight python %}
t[1:3]=['x','y']
t
{% endhighlight %}
```
['a', 'x', 'y', 'd', 'e', 'f']
```

### List methods
  1. append
  2. extend
  3. sort

{% highlight python %}

# append
t = ['a', 'b', 'c']
t.append(['d','e'])
print(t)
{% endhighlight %}
```
['a', 'b', 'c', ['d', 'e']]
```

{% highlight python %}
# extend
# This method leaves t2 unmodified
t1 = ['a', 'b', 'c']
t2= ['d','e']
t1.extend(t2)
print(t1)
{% endhighlight %}
```
['a', 'b', 'c', 'd', 'e']
```

{% highlight python %}
# sort
t=['a', 'd', 'e', 'b', 'c', 'f']
t.sort()
print(t)
{% endhighlight %}
```
['a', 'b', 'c', 'd', 'e', 'f']
```
DONT USE `t=t.sort()` ! It will return "NONE" !!


### Deleting elements

  1. pop - can save the deleted value
  2. del - Don't need the removed value and know index
  3. remove - know elem,ent but not index

{% highlight python %}
# pop
t = ['a', 'b', 'c']
x=t.pop(1)
print(f't: {t}')
print(f'x: {x}')
{% endhighlight %}
```
t: ['a', 'c']
x: b
```

{% highlight python %}
# del
t = ['a', 'b', 'c']
del t[1:3]
print(t)
{% endhighlight %}
```
['a']
```

{% highlight python %}
# remove
t = ['a', 'b', 'c']
t.remove('b')
print(t)
{% endhighlight %}
```
['a', 'c']
```
* `sum()` can only be used when the elements are numbers
* `max()`, `len()`, etc, can be used with lists of strings and other types

{% highlight python %}
numlist = list()
while True:
    inp = input('Enter a number:')
    if inp == 'done':
        break
    value = float(inp)
    numlist.append(value)
    average = sum(numlist)/len(numlist)
    print(f'Average: {average}')
{% endhighlight %}
```
Enter a number:10
Average: 10.0
Enter a number:85
Average: 47.5
Enter a number:2
Average: 32.333333333333336
Enter a number:done
```

### Lists and strings
Convert a string to a list of char:
  1. list
  2. split
{% highlight python %}
# list - break a string into individual letters
s='spam'
t=list(s)
print(t)
{% endhighlight %}
```
['s', 'p', 'a', 'm']
```

{% highlight python %}
# split - break a string into words
s = "printing      for the    frog"
t=s.split()  #- In default, it will split all the words on varies of white spaces
print(t)
{% endhighlight %}
```
['printing', 'for', 'the', 'frog']
```

{% highlight python %}
print(t[3])
{% endhighlight %}
```
frog
```

{% highlight python %}
# split - with delimiter
s='spam-spam-spam'
delimiter = '-'
s.split(delimiter)
{% endhighlight %}
```
['spam', 'spam', 'spam']
```

Take a list of strings and concatenates the elements:
  * join

{% highlight python %}
# delimiter as a whitespace
t=['printing', 'for', 'the', 'frog']
delimiter=' '
delimiter.join(t)
{% endhighlight %}
```
'printing for the frog'
```

{% highlight python %}
# delimiter as None
t=['printing', 'for', 'the', 'frog']
delimiter=''
delimiter.join(t)
{% endhighlight %}
```
'printingforthefrog'
```

### Parsing lines
* If two list are equivalent, they are not necessarily identical.
* If two list are identical, they are also equivalent.

### Aliasing

{% highlight python %}
a=[1,2,3]
b = a
b is a
{% endhighlight %}
```
True
```
Now, b is refering a. When b is changed, a is also changed.
{% highlight python %}
b[0] = 17
print(a)
{% endhighlight %}
```

[17, 2, 3]
```
In general, it is safter to avoid aliasing when you are working withmutable objects. 
<br>


## Dictionaries
* A dictionary is like a list
* The indices of a dictionary can be any type
* Dictionary: A mapping between a set of indices (which are called keys) and a set of values
* Key-value pair: the associationi of a key and a value
{% highlight python %}
adict=dict()
print(adict)
{% endhighlight %}
```
{}
```
The curly breakets, {}, represent an empty dictionary.  
To add items to the dictionary, use square brackets:
{% highlight python %}
# add a key value pair: 'one':'uno'
adict['one']='uno'
{% endhighlight %}
```
The order of items in a dictionary isunpredictable.
```

{% highlight python %}
adict={'one':'uno', 'two':'dos', 'three':'tres', 'a':'wha'}
print(adict)
{% endhighlight %}
```
{'one': 'uno', 'two': 'dos', 'three': 'tres', 'a': 'wha'}
```

Look up the corresponding values by keys:
{% highlight python %}
print(adict['a'])
{% endhighlight %}
```
wha
```

The len function works on dictionaries; it returns the number of key value pairs:
{% highlight python %}
len(adict)
{% endhighlight %}
```
4
```

The "in" operator works on dictionaries; it tells you whether something appears as a key in the dictionary:
{% highlight python %}
# works with key
'one' in adict
{% endhighlight %}
```
True
```

{% highlight python %}
# does not work with value
'uno' in adict
{% endhighlight %}
```
False
```

Use 'values' to see whether somehing appears as a value in a dictionary:
{% highlight python %}
vals = list(adict.values())
'uno' in vals
{% endhighlight %}
```
True
```

### Dictionary as a set of counters
{% highlight python %}
word = 'brontosaurus'
d = dict()
for c in word:
    if c not in d:
        d[c] = 1
    else:
        d[c] = d[c] + 1
print(d)
{% endhighlight %}
```
{'b': 1, 'r': 2, 'o': 2, 'n': 1, 't': 1, 's': 2, 'a': 1, 'u': 2}
```

### Get
It takes a key and a default value. If the key appears in the dictionary. 'get' returns the corresponding value; otherwise it returns the default value.
{% highlight python %}
counts = {'chuck':1, 'annie':42, 'jan':100}
print(counts.get('jan'))
{% endhighlight %}
```
100
```

{% highlight python %}
print(counts.get('tim'))
{% endhighlight %}
```
None
```

Write a histogram loop
{% highlight python %}
word = 'brontosaurus'
d = dict()
for c in word:
    # get(c,0): if there is not key in the dictionary, return 0
    d[c]=d.get(c,0)+1
print(d)
{% endhighlight %}
```
{'b': 1, 'r': 2, 'o': 2, 'n': 1, 't': 1, 's': 2, 'a': 1, 'u': 2}
```

### Dictionaries and files
{% highlight python %}
fname = input('Enter the file name:')
try:
    fhand=open(fname)
except:
    print('File cannot be opend:', fname)
    exit()
counts = dict()
for line in fhand:
    words=line.split()
    for word in words:
        if word not in counts:
            count[word]=1
        else:
            counts[word]+=1
print(counts)
{% endhighlight %}

### Looping and dictionaries

{% highlight python %}
counts = {'chuck':1, 'annie':42, 'jan':100}
for key in counts:
    print(key, counts[key])
{% endhighlight %}
```
chuck 1
annie 42
jan 100
```

### Using pattern
{% highlight python %}
counts = {'chuck':1, 'annie':42, 'jan':100}
for key in counts:
    if counts[key]>10:
        print(key, counts[key])
{% endhighlight %}
```
annie 42
jan 100
```

### Make the keys in alphabetical order
{% highlight python %}
counts = {'chuck':1, 'annie':42, 'jan':100}

lst = list(counts.keys())
print(lst)
lst.sort()
for key in lst:
    print(key, counts[key])
{% endhighlight %}
```
['chuck', 'annie', 'jan']
annie 42
chuck 1
jan 100
```

### Advanced text parsing (with punctuation)
1. string method:
  * lower
  * punctuation
  * translate
2. fromstr
  * replace the characters
3. tostr
  * with the character in the same position
4. deletstr
  * delete all charactors
{% highlight python %}
import string
string.punctuation
{% endhighlight %}
```
'!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~'
```

To remove punctuation of a text:
{% highlight python %}
fname = input('Enter the file name:')
try:
    fhand=open(fname)
except:
    print('File cannot be opend:', fname)
    exit()
counts = dict()
for line in fhand:
    line = line.translate(line.maketrans(' ','',string.punctuation))
    line=line.lower()
    words=line.split()
    for word in words:
        if word not in counts:
            count[word]=1
        else:
            counts[word]+=1
print(counts)
{% endhighlight %}

<br>

## Tuples
A tuple is a sequence of values much like a list.
THe values stored in a tuple can be any type and they are indexed by integers.

* tuples are immutable
* tuples are also comparable and hashable
* tuples can be sorted and be used as key alues in Python dictionaries
* tuple is a comma-separated list of values

{% highlight python %}
t = 'a', 'b', 'c', 'd', 'e'
t
{% endhighlight %}
```
('a', 'b', 'c', 'd', 'e')
```

{% highlight python %}
t = ('a', 'b', 'c', 'd', 'e')
t
{% endhighlight %}
```
('a', 'b', 'c', 'd', 'e')
```
To create a tuple with a single element, a final comma must be included. Otherwise, python will treats ('a') as an expression with a string:
{% highlight python %}
t1=('a',)
type(t1)
{% endhighlight %}
```
tuple
```

{% highlight python %}
t=tuple()
print(t)
{% endhighlight %}
```
()
```

If the argument is a sequence (string, list, or tuple), the result of the call to tuple is a tuple with the elements of the swquence:
{% highlight python %}
t=tuple('lupins')
print(t)
{% endhighlight %}
```
('l', 'u', 'p', 'i', 'n', 's')
```
<b>Tuple cannot be modified:</b>
{% highlight python %}
t[0]='A'
{% endhighlight %}
```
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-144-2cabaacd7cc5> in <module>()
----> 1 t[0]='A'

TypeError: 'tuple' object does not support item assignment
```

<b>But tuple can be replaced by other tuple:</b>
{% highlight python %}
t=('A', ) + t[1:]
print(t)
{% endhighlight %}
```
('A', 'u', 'p', 'i', 'n', 's')
```

### Comparing tuples
  1. Decorate
  2. Sort
  3. Undercorate
Sort a list of words from longest to shortest:
{% highlight python %}
txt = 'but soft what light in yonder window breaks'
words=txt.split()
t=list()
words.sort(reverse=True)
print('sorted on alphabet:',words)
for word in words:
    t.append((len(word), word)) #tuple
t.sort(reverse=True)
print('sorted on length:',t)
res = list()
for length, word in t:
    res.append(word)
print(res)
{% endhighlight %}
```
sorted on alphabet: ['yonder', 'window', 'what', 'soft', 'light', 'in', 'but', 'breaks']
sorted on length: [(6, 'yonder'), (6, 'window'), (6, 'breaks'), (5, 'light'), (4, 'what'), (4, 'soft'), (3, 'but'), (2, 'in')]
['yonder', 'window', 'breaks', 'light', 'what', 'soft', 'but', 'in']
```

### Tuple assignment
It can be assigned to more than one variable at a time when the left side is a sequence
{% highlight python %}
m=['have', 'fun']
x,y=m
print(x)
print(y)
{% endhighlight %}
```
have
fun
```

{% highlight python %}
m=['have', 'fun']
x=m[0]
y=m[1]
print(x)
print(y)
{% endhighlight %}
```
have
fun
```

{% highlight python %}
m=['have', 'fun']
(x,y)=m
print(x)
print(y)
{% endhighlight %}
```
have
fun
```

<b>Swap the values of two variables in a single statement:</b>
{% highlight python %}
(a,b)=(1,2)
print('before:')
print(a)
print(b)

a,b=b,a
print('\nafter:')
print(a)
print(b)
{% endhighlight %}
```
before:
1
2

after:
2
1
```

Split an email address into a name&domain:
{% highlight python %}
addr='monty@python.org'
uname, domain=addr.split('@')
print(uname)
print(domain)
{% endhighlight %}
```
monty
python.org
```

Dictionaries have a method called "`items`" that returns a list of tuples, where each tuple is akey-value pair:
{% highlight python %}
d={'a':10, 'c':22, 'b':1}
t=list(d.items())
print(t)
{% endhighlight %}
```
[('a', 10), ('c', 22), ('b', 1)]
```

It can be sorted after using `.items()`:
{% highlight python %}
d={'a':10, 'c':22, 'b':1}
t=list(d.items())
t.sort()
t
{% endhighlight %}
```
[('a', 10), ('b', 1), ('c', 22)]
```

Mutiple assignment with dictionaries:
{% highlight python %}
for key, val in list(d.items()):
    print('key:{:1} value:{:2}'.format(key, val))
{% endhighlight %}
```
key:a value:10
key:c value:22
key:b value: 1
```
* Lists are more common than tuples
* There are a few cases you might prefer tuples
* "return" statement
  + it is sytactically simpler to create a tuple than a list
* use a sequence as a dictionary key
  + you have to use an immutable type like a tuple or string
* passing a sequence as an argement to a function, using tuples reduces the potential for unexpected behavior

'sort', 'sorted', 'reverse', 'reversed' do work on tuples


<p align="center"><a href="#top">Top</a></p>


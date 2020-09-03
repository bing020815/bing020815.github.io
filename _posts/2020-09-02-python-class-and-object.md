---
layout: post
title: "Python Baisc: Class and Objects"
date: 2020-09-02
theme: minimal
mathjax: true
categories: Python
---
<div id='top'>
  <p align="center"><img src="{{site.baseurl}}/assets/images/post/python/class-objects.png" title=""></p>
  <p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">Class and Objects</p>
</div>

## Table of contents:  
* [Class And Objects](#class-and-objects) 
* [Basic Python Class](#basic-python-class) 
* [Object Methods](#object-methods) 
	+ [Getter, Deletor and Setter](#getter-deletor-and-setter)
	+ [Dunder Methods](#dunder-methods)
	+ [Class Variable and Instance Variables](#class-variable-and-instance-variables)
	+ [Static Methods](#static-methods)
* [Class Inherent](#class-inherent)  
* [Built-in Functions](#built-in-functions)  
* [Application](#application)  

<br>

## Class And Objects
Python is an object oriented programming language. Almost everything in Python is an `object`, with its properties and methods. A `class` is like an `object` constructor, or a "blueprint" for creating objects.  

For example:   
A factory can have a blueprint of making a car for a specific model. The blueprint is a 'class'.   
Customer can buy a customized car, leather interior, roof, navigation system ...etc, for that specific model. The customized car here is an `object`.  

<br>

## Basic Python Class
In python, there are built-in data types, such as numeric (`int`, `float`), Boolean (`True`, `False`), Sequence Type (`string`, `list`, `tuple`) and Dictionary (`dict`). Python has an built-in function `type()` to ascertain the data type of a certain value.  

However, a custom datatype can be built by using python class.   

Let's say we want to have a __Book__ datatype in python. We want the __Book__ datatype contains the information of book name, publish year, author name, book price, and if it is kindle version.

{% highlight python %}
class Book:
    '''This is the comment section that you are able to access through "__doc__" attribute.'''

    # class variable
    num_of_books = 0  
    # When access a class variable, it should be called through a class itself or an instance of a class


    # The __init__ method is roughly what represents a constructor in Python
    # It runs everytime when a new instance has been created 
    # 'self' refers as an instance of a class
    # 'name', 'publish_year', 'author', 'price', 'is_kindle' are parameters
    def __init__(self, name, publish_year, author, price, is_kindle):
    # 'self.name', 'self.publish_year', 'self.author', 'self.price', 'self.is_kindle' are attributes, also called instance variables
        self.name = name
        self.publish_year = publish_year        
        self.author = author        
        self.price = price 
        self.is_kindle = is_kindle 

        Book.num_of_books += 1 # it increases everytime when a instance has been created
    
    def pass_statement(self):
        #class definitions cannot be empty, but if you have a class definition with no content, put in the pass statement to avoid getting an error
        pass
{% endhighlight %}

`Class` datatype can contain two types of variable, `instance variable` and `class variable`. `instance variable` are used for data that is unique to each instance, such as 'name', 'publish_year', 'author', 'price', 'is_kindle'.  `class variables` are the variables that are shared among all instances of a class. The example here can be 'num_of_books'. It can be called through a class itself or an instance of a class.   

All classes have a function called `__init__()`, which is always executed when the class is being initiated. Use the `__init__()` function to assign values to object properties, or other operations that are necessary to do when the object is being created.  

Now, the `__Book__` data type has been created. The next step is to instanciate the class to create an object, a book.   

{% highlight python %}
# instantiate the `Book` class
book1 = Book('How to master python', 2020, "Bing-Je", 20, False)
# call the instance attribute, name
book1.name  
{% endhighlight %}
```
'How to master python'
```


{% highlight python %}
# call the instance attribute, publish_year 
book1.publish_year
{% endhighlight %}
```
2020
```


{% highlight python %}
# call the instance attribute, price
book1.price
{% endhighlight %}
```
20
```


{% highlight python %}
# call the instance attribute, author
book1.author
{% endhighlight %}
```
'Bing-Je'
```


{% highlight python %}
# call the instance attribute, is_kindle
book1.is_kindle
{% endhighlight %}
```
False
```

Now, we have the first object. Let's create another object, second book.

{% highlight python %}
# instantiate the `Book` class
book2 = Book('The Road Ahead: Completely Revised and Up-to-Date', 1996, 'Bill Gates', 24, True)
# call the instance attribute, name
book2.name
{% endhighlight %}
```
'The Road Ahead: Completely Revised and Up-to-Date'
```


{% highlight python %}
# call the instance attribute, is_kindle, for book2
book2.is_kindle
{% endhighlight %}
```
True
```


{% highlight python %}
# call the instance attribute, is_kindle, for book1
book1.is_kindle
{% endhighlight %}
```
False
```

A class must be instantiated in order to get the instance attribute/instance variable.

{% highlight python %}
try:
    Book.is_kindle
except AttributeError:
    print('class does not inherent from a class or does not have the instance attribute/instance variable, "is_kindle"!')
{% endhighlight %}
```
class does not inherent from a class or does not have the instance attribute/instance variable, "is_kindle"!
```

Using `__dict__` attribute and check the current parameters that are assigined to a class or a instance.

{% highlight python %}
# Check the instance, book1
book1.__dict__
{% endhighlight %}
```
{'author': 'Bing-Je',
 'is_kindle': False,
 'name': 'How to master python',
 'price': 20,
 'publish_year': 2020}
```

The `__dict__` attribute only shows the instance variables when the method is called from a `name space`, book1.

{% highlight python %}
# Check Book class
Book.__dict__
{% endhighlight %}
```
mappingproxy({'__dict__': <attribute '__dict__' of 'Book' objects>,
              '__doc__': 'This is the comment section that you are able to access through "__doc__" attribute.',
              '__init__': <function __main__.Book.__init__>,
              '__module__': '__main__',
              '__weakref__': <attribute '__weakref__' of 'Book' objects>,
              'num_of_books': 2,
              'pass_statement': <function __main__.Book.pass_statement>})
```

The `num_of_book` parameter, `class variable`, indicates the number of instances has been instanciated for the class.   

The `__doc__` attribute shows the information about the class.  

{% highlight python %}
Book.__doc__
{% endhighlight %}
```
'This is the comment section that you are able to access through "__doc__" attribute.'
```

Alright, that is the basis of the python class and object.



<br>


## Object Methods

Within a python `class`, it can define mutiple functions as the method of an `object`. When an `object` is instantiated based on the `class`, it is automatically assigned the functions as methods that can be used in advanced.

The methods can be categorized into three:
* __Regular Method__
    + Regular method in a class automatically take the `instance` as the first argument 
    + By convention, we ususally call the first argument as 'self'

* __Class Method__
    + Class method will add a decorator, `@classmethod`, on the top
    + The method in a class automatically take the `class` as the first argument 
    + By convention, we ususally call the first argument as 'cls'
    
* __Static Method__
    + Static methods will add a decorator,`@staticmethod`, on the top
    + Static methods do not take the `instance` or the `class` as the first argument automatically
    + They behave just like normal functions, yet they should have some logical connection to our class.
    + If a function of a class does not access the `instances` or the `class` anywhere within the function,  it should be used as a static method


There are some special methods, such as __magic method__, also known as __dunder method__. These methods allow us to emulate built-in types or implement operator overloading.
* `__init__()`
	- The `__init__` method for initialization is invoked without any call, when an instance of a class is created
	- It contains a collection of statements(i.e. instructions) that are executed at time of object creation
	- The keyword `self` represents the instance of a `class` and binds the attributes with the given arguments
* `__repr__`
    - To be an unambiguous representation of the object
    - It should be used for debugging or logging 
    - It is meant to be seen by other developers
    - This method can fix the vague object description when we use `print()` on a object
* `__str__()`
    - It is meant to be more readable representation of an object
    - It is meant to be used as a display to the end-user
* `__add__()`
    - Can be set to perform addition on numbers or strings
* `__len__()`
    - It help perfrom the `len()` on objects.


{% highlight python %}
# importing datetime module and random module for the functions created in the Robot class
# importing datetime module and random module for the functions created in the Robot class
from datetime import datetime
import random

class Robot:
    
    # class variables
    battery_amt = 50
    # When access a class variable, it should be called through a class itself or an instance of a class

    def __init__(self, robotname, ownername, birth):
        self.robotname = robotname
        self.ownername = ownername
        self.birth = birth

    @property     # allow user to access 'id' as an instanace attribute
    def id(self):
        return "{}'s {}".format(self.ownername, self.robotname)

    @id.setter  # allow user to change the 'id' also change the attributes of 'robotname' and 'ownername'
    def id(self, identity):
        """ identity: 'someone's robot """
        owner, robot = identity.split("'s ")
        self.ownername = owner
        self.robotname = robot

    @id.deleter  # allow user to delete the attributes of 'robotname' and 'ownername'
    def id(self):
        print('Delete Name')
        self.ownername = None
        self.robotname = None

    # saying hello with user name; regular method
    def say_hello(self):
        return 'Hello, {}!'.format(self.ownername)
        
    # return the current time; regular method    
    def tell_me_time(self):
        current_time= datetime.now()
        return 'Current time is {}'.format(current_time)

    # return what day is today randomly; regular method    
    def what_day_is_today(self):
        day = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 
               'Friday', 'Saturday', 'Sunday']
        today = random.choice(range(7))
        return 'Today is {}!'.format(day[today])

    # method can access a class variable as an attribute of an instance; regular method
    def charge_battery(self, amount):
        self.battery_amt = int(self.battery_amt + amount)

    @classmethod    # using decorator to refer a method with a class instead of instances
    def set_battery(cls, amount):   # using 'cls' as convention to refer the class
        cls.battery_amt = amount  # call a class variable from a class

    @classmethod  # using class method as an alternative constructor
    def from_string(cls, robot_string, separator):
        """ robot_string: 'robotname-onwername-mm/dd' ; separator : '-' """
        robotname, ownername, birth = robot_string.split(separator)
        return cls(robotname, ownername, birth)

    @staticmethod    # staticmethod does not access a class or an instance within the function
    def lucky_number_1_to_10():
        import random
        return random.randint(1,10)

    def __repr__(self): # at least has this method to show more infomation of an instance; dunder method
        return "'{}', '{}', '{}'".format(self.robotname, self.ownername, self.birth)

    def __str__(self):  # dunder method
        return "'{} - {} - {}'".format(self.robotname, self.ownername, self.birth)

    def __add__(self, other):  # dunder method
        return self.say_hello + other.say_hello

    def __len__(self):  # dunder method
        return len(self.robotname)
{% endhighlight %}

Now, we have created a new `class`, __Robot__ data type. We are ready to create instances, `objects`.

{% highlight python %}
alexa = Robot('alexa', 'Bing', '08/15')
siri = Robot('siri', 'Bing-Je', '12/30')
{% endhighlight %}

{% highlight python %}
alexa.say_hello()
{% endhighlight %}
```
'Hello, Bing!'
```

{% highlight python %}
alexa.tell_me_time()
{% endhighlight %}
```
'Current time is 2020-09-02 20:44:05.000624'
```


{% highlight python %}
alexa.what_day_is_today()
{% endhighlight %}
```
'Today is Monday!'
```

### Getter, Deletor and Setter


The `property decorator` using as a `getter` allows us to define Class methods that we can access like attributes. Here we have the `.id()` method to be access as an attribute.

{% highlight python %}
print(alexa.id)
{% endhighlight %}
```
Bing's alexa
```

The `property decorator`can be used as a `deleter` to delete the instance attributes.

{% highlight python %}
del alexa.id
print(alexa.id)
print(alexa.ownername)
print(alexa.robotname)
{% endhighlight %}
```
Delete Name
None's None
None
None
```

The `property decorator`can be also used as a `setter` in order to update the instance attribute.

{% highlight python %}
alexa.id = "Bing's alexa"
print(alexa.ownername)
print(alexa.robotname)
{% endhighlight %}
```
Bing
alexa
```

### Dunder Methods

With the `__repr__()` and `__str__()` set in the class, we can have the unambiguous representation of the object. `__add__()` help perform the string addtion of instance attributes. `__len__()` special dunder method help perfrom the `len()` on objects.


{% highlight python %}
print(alexa)
print(siri)
{% endhighlight %}
```
'alexa - Bing - 08/15'
'siri - Bing-Je - 12/30'
```


{% highlight python %}
# string addtion on instance attributes
print(alexa.ownername + siri.ownername)
{% endhighlight %}
```
BingBing-Je
```


{% highlight python %}
# len() on the objects
print(len(alexa))
print(len(siri))
{% endhighlight %}
```
5
4
```

### Class Variable and Instance Variables

`class variable` can be assigned to an instance through methods. Calling a `class variable` will not assign the `class variable` as an attribute of the instance.

{% highlight python %}
# call attributes
alexa.__dict__
{% endhighlight %}
```
{'birth': '08/15', 
'ownername': 'Bing', 
'robotname': 'alexa'}
```

The class variable has not been assigned to the instance attributes for `alexa` object.

{% highlight python %}
# accessing a class variable through methods
alexa.charge_battery(10)

# new attribute for the instance
alexa.battery_amt
{% endhighlight %}
```
60
```


{% highlight python %}
# call attributes
alexa.__dict__
{% endhighlight %}
```
{'battery_amt': 60,
 'birth': '08/15',
 'ownername': 'Bing',
 'robotname': 'alexa'}
```

Now, A new instance attribute, battery_amt, has been added for `alexa` object through accessing the class variable.

__#__ The `class variable` can be changed through a class method.

{% highlight python %}
# class attribute
Robot.battery_amt  
{% endhighlight %}
```
50
```

The `battery_amt` is a class variable with e default setting as 50. Using a class method, set_battery to change the default value to 30.

{% highlight python %}
# class method
Robot.set_battery(30)

# class attribute
Robot.battery_amt  
{% endhighlight %}
```
30
```


{% highlight python %}
# the instance attribute remains the same
alexa.__dict__
{% endhighlight %}
```
{'battery_amt': 60,
 'birth': '08/15',
 'ownername': 'Bing',
 'robotname': 'alexa'}
```

__#__ Using a `class method` from an instance will not only update the `class variable` but also that `instance attribute`.

{% highlight python %}
# runing class method from an instance still works
alexa.set_battery(60)

# the class variable has been changed
Robot.battery_amt 
{% endhighlight %}
```
60
```


{% highlight python %}
# the class attribute for that instance has also been changed
alexa.__dict__
{% endhighlight %}
```
{'battery_amt': 60,
 'birth': '08/15',
 'ownername': 'Bing',
 'robotname': 'alexa'}
```


{% highlight python %}
# assiging the class variable to a new instance with the updated class variable
siri.battery_amt
{% endhighlight %}
```
60
```

__#__ Using `class method` as an alternative constructor to create multipe objects/instances

{% highlight python %}
robot_string1 = 'rbt-JJ-01/25'
rbt = Robot.from_string(robot_string1, '-')
{% endhighlight %}

{% highlight python %}
# calling the class variable
rbt.battery_amt
{% endhighlight %}
```
60
```

{% highlight python %}
# the class variable was not assigned to the instance as an attribute
rbt.__dict__
{% endhighlight %}
```
{'birth': '01/25', 'ownername': 'JJ', 'robotname': 'rbt'}
```

### Static Methods
 `staticmethods` do not pass any instance or class, meaning it does not access an instance or a class anywhere within a function. Call a `staticmethod` from a class.

{% highlight python %}
# call a staticmethod
Robot.lucky_number_1_to_10()
{% endhighlight %}
```
4
```

<br>

## Class Inherent


A `class` can inherent the attribute and method from the other `class`, parent class.  Let's say we want to create an advance robot to have advanced functions or improved functions. Here, we are going to create a new `class`, __AdvancedRobot__ data type. The __AdvancedRobot__ data type can not only have the basic functions that a __Robot__ `object` has but also have advanced functions such as playing music and reporting the location. 

{% highlight python %}
# child classes can inherent methods, class variables and instance attributes from parent class
class AdvancedRobot(Robot): 
    # use Robot class as input to inherent attributes and functions/methods

    battery_amt = 65

    def __init__(self, robotname, ownername, birth, location):
        # 'robotname', 'ownername', 'birth' are handled by the init method of Robot class, parent class/ base class.
        super().__init__(robotname, ownername, birth) 
        self.locattion = location

    
    # change the output of time for differencing from Robot class
    @staticmethod    # staticmethod does not access a class or an instance within the function
    def tell_me_time():
        current_time= datetime.now().time()
        print('Current time is {}'.format(current_time))
        
    @staticmethod    # staticmethod does not access a class or an instance within the function    
    def where_am_I():
        place = ['Japan', 'USA', 'Taiwan', 'Korea', 
               'Germany', 'UK', 'France']
        myplace = random.choice(range(7))
        print('You are in {}!'.format(myplace))    
    
    @staticmethod    # staticmethod does not access a class or an instance within the function
    def play_music():
        print("Playing music ...")
    
class RobotManager(Robot):
    battery_amt = 70

    # always set the default value an immutable
    def __init__(self, robotname, ownername, birth, robot_list=None): 
        # 'robotname', 'ownername', 'birth' are handled by the init method of Robot class, parent class/ base class.
        Robot.__init__(self, robotname, ownername, birth) 
        if robot_list is None:
            self.robot_list = []
        else:
            self.robot_list = robot_list
        
    # add a robot into managing list; regular method
    def add_robot(self, robot):
        if robot not in self.robot_list:
            self.robot_list.append(robot)

    # remove a robot into managing list; regular method
    def remove_robot(self, robot):
        if robot in self.robot_list:
            self.robot_list.remove(robot)

    # print a list of robot name along with owner name managed by the robot manager; regular method
    def print_robots(self):
        for robot in self.robot_list:
            print('Robot: {} ; Owner: {}'.format(robot.robotname.capitalize(), robot.ownername))

{% endhighlight %}

`super().__init__()` or `parent_class.init__(self,)` from the init method of a subclass to call the parent init method to inherits the instance attributes.

Python will look for the chain of the inheritence to get what is inherited from the parent class. This chain is called method resolutional order. The `help()` can help visualize the method resolutional order in this case.

{% highlight python %}
print(help(AdvancedRobot))
{% endhighlight %}
```
Help on class AdvancedRobot in module __main__:

class AdvancedRobot(Robot)
 |  Method resolution order:
 |      AdvancedRobot
 |      Robot
 |      builtins.object
 |  
 |  Methods defined here:
 |  
 |  __init__(self, robotname, ownername, birth, location)
 |      Initialize self.  See help(type(self)) for accurate signature.
 |  
 |  play_music(self)
 |  
 |  tell_me_time(self)
 |      # change the output of time for differencing from Robot class
 |  
 |  where_am_I(self)
 |  
 |  ----------------------------------------------------------------------
 |  Data and other attributes defined here:
 |  
 |  battery_amt = 65
 |  
 |  ----------------------------------------------------------------------
 |  Methods inherited from Robot:
 |  
 |  __add__(self, other)
 |  
 |  __len__(self)
 |  
 |  __repr__(self)
 |      Return repr(self).
 |  
 |  __str__(self)
 |      Return str(self).
 |  
 |  charge_battery(self, amount)
 |      # method can access a class variable as an attribute of an instance; regular method
 |  
 |  say_hello(self)
 |      # saying hello with user name; regular method
 |  
 |  what_day_is_today(self)
 |      # return what day is today randomly; regular method
 |  
 |  ----------------------------------------------------------------------
 |  Class methods inherited from Robot:
 |  
 |  from_string(robot_string, separator) from builtins.type
 |      robot_string: 'robotname-onwername-mm/dd' ; separator : '-'
 |  
 |  set_battery(amount) from builtins.type
 |  
 |  ----------------------------------------------------------------------
 |  Static methods inherited from Robot:
 |  
 |  lucky_number_1_to_10()
 |  
 |  ----------------------------------------------------------------------
 |  Data descriptors inherited from Robot:
 |  
 |  __dict__
 |      dictionary for instance variables (if defined)
 |  
 |  __weakref__
 |      list of weak references to the object (if defined)
 |  
 |  id

None
```

By creating a new instance, we can prove that the AdvancedRobot `object` has perfect inherented everything from __Robot__ `class`.

{% highlight python %}
# instantiate the 'RobotManager' class
google = AdvancedRobot('google', 'BingJe', '08/15', 'living room')
{% endhighlight %}

{% highlight python %}
# check the class variable
google.battery_amt
{% endhighlight %}
```
65
```

{% highlight python %}
# call attributes
google.__dict__
{% endhighlight %}
```
{'birth': '08/15',
 'locattion': 'living room',
 'ownername': 'BingJe',
 'robotname': 'google'}
```

The class variable has not been assigned to the instance attributes for google object.

{% highlight python %}
# accessing a class variable through methods
google.charge_battery(10)

# a new attribute for the instance
google.battery_amt
{% endhighlight %}
```
75
```

{% highlight python %}
# call attributes
google.__dict__
{% endhighlight %}
```
{'battery_amt': 75,
 'birth': '08/15',
 'locattion': 'living room',
 'ownername': 'BingJe',
 'robotname': 'google'}
```

Now, A new instance attribute, battery_amt, has been added for google object through accessing the class variable.

{% highlight python %}
# call a static method
google.tell_me_time()
{% endhighlight %}
```
Current time is 02:28:13.928534
```


{% highlight python %}
# call a static method
google.what_day_is_today()
{% endhighlight %}
```
'Today is Sunday!'
```


{% highlight python %}
# call a static method
google.play_music()
{% endhighlight %}
```
Playing music ...
```


{% highlight python %}
# instantiate the 'RobotManager' class
jarvis = RobotManager('javis', 'BingJe', '08/15')
{% endhighlight %}

{% highlight python %}
# call attributes
jarvis.__dict__
{% endhighlight %}
```
{'birth': '08/15',
 'ownername': 'BingJe',
 'robot_list': [],
 'robotname': 'javis'}
```

The robot managing list is empty. Use the regular methods to update the managing list.

{% highlight python %}
# call a regular method
jarvis.add_robot(alexa)

# call a regular method
jarvis.add_robot(siri)

# call a regular method
jarvis.add_robot(google)
{% endhighlight %}


{% highlight python %}
# call a regular method
jarvis.print_robots()
{% endhighlight %}
```
Robot: Alexa ; Owner: Bing
Robot: Siri ; Owner: Bing-Je
Robot: Google ; Owner: BingJe
```

{% highlight python %}
# call a regular method to remove a namespace from the list
jarvis.remove_robot(siri)
{% endhighlight %}

{% highlight python %}
# call a regular method
jarvis.print_robots()
{% endhighlight %}
```
Robot: Alexa ; Owner: Bing
Robot: Google ; Owner: BingJe
```

<br>

## Built-in Functions

`isinstance()` can check if an object is an instance.  
`issubclass()` can check if a subclass is of another class.

{% highlight python %}
isinstance(google, Robot)
{% endhighlight %}
```
True
```

{% highlight python %}
issubclass(RobotManager, Robot)
{% endhighlight %}
```
True
```

<br>

## Application
Multiple Choice Question Application

{% highlight python %}
# create a list of questions
question_prompts = [
    "What color are apples?\n(a) Red/Green\n(b) Purple\n(c) Orange\n\n",
    "What color are bananas?\n(a) Teal\n(b) Magneta\n(c) Yellow\n\n",
    "What color are strawberries?\n(a) Yellow\n(b) Red\n(c) Blue\n\n",
    ]
{% endhighlight %}


{% highlight python %}
# create 'Question' class to call the question and answer as its attributes
class Question:
    def __init__(self, prompt, answer):
        self.prompt = prompt
        self.answer = answer
{% endhighlight %}

{% highlight python %}
# create a list that contains question objects and answers for each question
questions = [
    Question(question_prompts[0], 'a'),
    Question(question_prompts[1], 'c'),
    Question(question_prompts[2], 'b'),
]
{% endhighlight %}


{% highlight python %}
# check the instance attribute
questions[1].prompt
{% endhighlight %}
```
'What color are bananas?\n(a) Teal\n(b) Magneta\n(c) Yellow\n\n'
```

{% highlight python %}
# create the run_question function
def run_qeustions(questions):
    score = 0
    for q in questions: # q is Question object
        answer = input(q.prompt) # call the prompt attribute from the class
        if answer == q.answer:  # compare the answer attribute from the class
            score += 1
    if score < 3:
        print('\nYou got {} question(s) wrong ! Sorry :('.format(3-score))
    else:
        print('\nYou got {} questions right ! Congrats !!'.format(score))
{% endhighlight %}


{% highlight python %}
run_qeustions(questions)
{% endhighlight %}
```
What color are apples?
(a) Red/Green
(b) Purple
(c) Orange

a
What color are bananas?
(a) Teal
(b) Magneta
(c) Yellow

b
What color are strawberries?
(a) Yellow
(b) Red
(c) Blue

c

You got 2 question(s) wrong ! Sorry :(
```

{% highlight python %}
run_qeustions(questions)
{% endhighlight %}
```
What color are apples?
(a) Red/Green
(b) Purple
(c) Orange

a
What color are bananas?
(a) Teal
(b) Magneta
(c) Yellow

c
What color are strawberries?
(a) Yellow
(b) Red
(c) Blue

b

You got 3 questions right ! Congrats !!
```

<br>
Reference:   
* [Python OOP Tutorials - Working with Classes](https://www.youtube.com/watch?v=ZDa-Z5JzLYM&list=PL-osiE80TeTsqhIuOqKhwlXsIBIdSeYtc&index=1)  
* [Dunder or magic methods in Python](https://www.geeksforgeeks.org/dunder-magic-methods-python/)  
* [Google Colab](https://colab.research.google.com/drive/1jgVIjPjNqJNmFhYMEyXdBv9CViIimy3E?usp=sharing)  


<p align="center"><a href="#top">Top</a></p>


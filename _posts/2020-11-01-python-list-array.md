---
layout: post
title: "Python Tips: Array and List"
date: 2020-10-01
theme: minimal
mathjax: true
categories: Python
---
<div id='top'>
  <p align="center"><img src="{{site.baseurl}}/assets/images/post/python/array-vs-list.png" title=""></p>
  <p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">Array and List</p>
</div>

## Table of contents:  
* [Array and List](#array-and-list) 
* [Array Broadcasting](#array-broadcasting) 
	+ [Scalar and One-Dimensional Array](#scalar-and-one-dimensional-array)
	+ [One-Dimensional Array and Two-Dimensional Array](#one-dimensional-array-and-two-dimensional-array)
	+ [More Complicated Cases in Broadcasting of Both Arrays](#more-complicated-cases-in-broadcasting-of-both-arrays)
* [Array Broadcasting Functionality on List and Array](#array-broadcasting-functionality-on-list-and-array)  

<br>

## Array and List
As learning Python, people usually get confused between `Array` and `List`. `List` is a python built-in method and the `Array` is built in <a href="https://numpy.org/">NumPy</a>. Both are the methods that are commonly used in Python in order to store data. It can store any datatype such as numbers, string, etc. They can both be indexed and iterated. However, they do not serve the same purposes. The main difference is that the `Array` has the <b>Array Broadcasting</b> functionality in <a href="https://numpy.org/">NumPy</a> but `List` does not have. 

<br>

## Array Broadcasting
Broadcasting is simply a set of rules for applying binary ufuncs (e.g., addition, subtraction, multiplication, etc.) on arrays of different sizes. Broadcasting in NumPy follows a strict set of rules to determine the interaction between the two arrays:

1. If the two arrays differ in their number of dimensions, the shape of the one with fewer dimensions is padded with ones on its leading (left) side.
2. If the shape of the two arrays does not match in any dimension, the array with shape equal to 1 in that dimension is stretched to match the other shape.
3. If in any dimension the sizes disagree and neither is equal to 1, an error is raised.


### Scalar and One-Dimensional Array
{% highlight python %}
import numpy as np
a = np.array([0, 1, 2])
b = np.array([5, 5, 5])
a + b
{% endhighlight %}
```
array([5, 6, 7])
```

{% highlight python %}
a = np.array([0, 1, 2])
a + 5
{% endhighlight %}
```
array([5, 6, 7])
```


### One-Dimensional Array and Two-Dimensional Array
{% highlight python %}
M = np.ones((3, 3))
M
{% endhighlight %}
```
array([[1., 1., 1.],
       [1., 1., 1.],
       [1., 1., 1.]])
```


{% highlight python %}
M + a
{% endhighlight %}
```
array([[1., 2., 3.],
       [1., 2., 3.],
       [1., 2., 3.]])
```


### More Complicated Cases in Broadcasting of Both Arrays
{% highlight python %}
a = np.arange(3)
b = np.arange(3)[:, np.newaxis] # increase a dimension and make it as a column vector
print(a)
print(b)
{% endhighlight %}
```
[0 1 2]
[[0]
 [1]
 [2]]
```


{% highlight python %}
a + b
{% endhighlight %}
```
array([[0, 1, 2],
       [1, 2, 3],
       [2, 3, 4]])
```

<br>

## Array Broadcasting Functionality on List and Array
Now, we have some basic understanding on the Array Broadcasting functionality. Let's setup a 2-d array, 1-d array and a list to do the experiment.
{% highlight python %}
import numpy as np
# create a 2-d array
array_2d = np.random.rand(2,3)
array_2d
{% endhighlight %}
```
array([[0.58758076, 0.74464029, 0.68320516],
       [0.98230461, 0.24750985, 0.05020555]])
```


{% highlight python %}
# create a 1-d array
array_1d = np.array([1,2,3,4])
array_1d
{% endhighlight %}
```
array([1, 2, 3, 4])
```


{% highlight python %}
# create a list
alist = list(array_1d)
alist
{% endhighlight %}
```
[1, 2, 3, 4]
```


{% highlight python %}
# Multiplication operation on the 2-d array
array_2d*2
{% endhighlight %}
```
array([[1.17516152, 1.48928058, 1.36641033],
       [1.96460922, 0.49501969, 0.1004111 ]])
```


{% highlight python %}
# Multiplication operation on the 1-d array
array_1d*2
{% endhighlight %}
```
array([2, 4, 6, 8])
```


{% highlight python %}
# Multiplication operation on the list
alist*2
{% endhighlight %}
```
[1, 2, 3, 4, 1, 2, 3, 4]
```

The broadcasting functionality works fine on arrays but not on the list. The list was repeated with the multiplication operation.

<br>

{% highlight python %}
# Division operation on the 2-d array
array_2d/2
{% endhighlight %}
```
array([[0.29379038, 0.37232015, 0.34160258],
       [0.4911523 , 0.12375492, 0.02510277]])
```


{% highlight python %}
# Division operation on the 1-d array
array_1d/2
{% endhighlight %}
```
rray([0.5, 1. , 1.5, 2. ])
```

{% highlight python %}
# Division operation on the list
alist = [1, 2, 3, 4]
alist/2
{% endhighlight %}
```
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-15-388b6a901f4d> in <module>
      1 # Division operation on the list
      2 alist = [1, 2, 3, 4]
----> 3 alist/2

TypeError: unsupported operand type(s) for /: 'list' and 'int'
```

The result above shows that the broadcasting functionality cannot be applied on the list. Thus, we can see the main different between `Array` and `List`.


<br>
Reference:   
* [A Gentle Introduction to Broadcasting with NumPy Arrays](https://machinelearningmastery.com/broadcasting-with-numpy-arrays/)
* [Computation on Arrays: Broadcasting](https://jakevdp.github.io/PythonDataScienceHandbook/02.05-computation-on-arrays-broadcasting.html)     


<p align="center"><a href="#top">Top</a></p>


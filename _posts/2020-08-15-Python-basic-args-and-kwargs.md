---
layout: post
title: "Python Baisc: *args and **kwargs"
date: 2020-08-15
theme: minimal
mathjax: true
categories: Python
---
<div id='top'>
  <p align="center"><img src="{{site.baseurl}}/assets/images/post/python/args-and-kwargs.png" title=""></p>
  <p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">*args and **kwargs</p>
</div>


## Table of contents:  
* [\*args](#args) 
    + [List Unpacking](#list-unpack)
    + [List Concatenation](#list-concat)
* [\*\*kwargs](#kwargs)  
    + [Dictionary Concatenation](#dict-concat)

## \*args and \*\*kwargs
<b>\*args</b> and <b>\*\*kwargs</b> allow user to pass multiple arguments(args) and keyward arguments(kwargs) to a function. <b>\*args</b> can unpack iterable and <b>\*\*kwargs</b> is for unpacking dictionaries.

<br>
<h3 id='args'> <p><strong>*args</strong></p></h3>
When we declare a function to sum up numbers, we often need to pass arguments. There are several ways to do so. The most common method is using a sigle <b>list</b> as the function argument. However, using *args as the alternative method can make the code elegant.

The first example using list as the argument::
{% highlight python %}
def sum_num(list_num):
    total=0
    for n in list_num:
        total += n
    return total

numbers = [1, 2, 3, 4, 5]
sum_num(numbers)
{% endhighlight %}

```
15
```

Using *args instead of a list:
{% highlight python %}
def sum_num_args(*args):
    total=0
    for n in args:
        total += n
    return total

sum_num_args(1, 2, 3, 4, 5)
{% endhighlight %}

* It can takes multiple arguments.

{% highlight python %}
sum_num_args(1, 2, 3, 4, 5)
{% endhighlight %}

```
15
```

<h4 id='list-unpack'><strong>List unpacking</strong></h4>
The idea of unpacking is to, well, unpack any iterable object. The single asterisk `*` is used to unpack any iterable.
{% highlight python %}
num_arr = [1, 2, 3, 4, 5]
print(*num_arr)
{% endhighlight %}

```
1 2 3 4 5
```
The result above shows that the print function can print the element of the list by using `*args`

<h4 id='list-concat'><strong>List concatenation</strong></h4>
Another thing that *args can do is list concatenation:
{% highlight python %}
nums1 = [1, 2, 3, 4, 5, 6]
nums2 = [7, 8, 9, 10]
nums = [*nums1, *nums2]
print(nums)
{% endhighlight %}

```
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```


<br>
<h3 id='kwargs'> <strong>**kwargs</strong></h3>
`**kwargs` are used to unpack dictionaries.

Let's try a calculation function that take **a**, **b** and **c** using traditional positional arguments:
{% highlight python %}
dic={'a':1 , 'b':20, 'c':12}
def calculate(a, b, c):
    total = a*10 + b*5 + c*1
    return total

calculate(dic['a'], dic['b'], dic['c'])
{% endhighlight %}

```
122
```

However, if we use the `**kwargs`, we can get the same results.
{% highlight python %}

calculate(**dic)
{% endhighlight %}

```
122
```
It is clear to see that using `**kwargs` is simpler, cleaner and more elegant.


<h4 id='dict-concat'><strong>Dictionary concatenation</strong></h4>
The dictionary concatenation is the same as the list concatenation. It will concatenate two different dictionaries into one. But, if there are duplicate keys, the value of the second dictionary will be used.

{% highlight python %}
# No key duplication
dic1 = {'a': 1, 'b': 2}
dic2 = {'c': 3, 'd': 4}
d = {**dic1, **dic2}
print(d)
{% endhighlight %}

```
{'a': 1, 'b': 2, 'c': 3, 'd': 4}
```
The key **b** has the value of `2`. 

{% highlight python %}
# key duplication
dic1 = {'a': 1, 'b': 2}
dic2 = {'b': 3, 'c': 4}
d = {**dic1, **dic2}
print(d)
{% endhighlight %}

```
{'a': 1, 'b': 3, 'c': 4}
```
Now, the key **b** has the value of `3`. 



<p align="center"><a href="#top">Top</a></p>


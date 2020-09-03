---
layout: post
title: "Python Baisc: List Comprehension"
date: 2020-08-13
theme: minimal
mathjax: true
categories: Python
---
<div id='top'>
  <p align="center"><img src="{{site.baseurl}}/assets/images/post/python/list-comprehension.png" title=""></p>
  <p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">List Comprehension</p>
</div>

## Table of contents:  
* [Simple List Comprehension](#example1) 
* [Adding Condition](#example2)  
* [Adding if... else... statement](#example3)  
* [Nested ifs in list comprehension](#example4) 
	+ [1. Two ifs](#example4-1)
	+ [2. Ifs and else with three outputs](#example4-2)


## List Comprehension
List comprehensions provide a concise way to create lists. It is frequently used to make new lists where every element is the result of some operations applied to anthor iterable object.

<br>
<h3 id='example1'> <strong>Simple List Comprehension</strong></h3>
Create a list and square the number from 0 to 9:

#### <u>For Loop Method</u>:
{% highlight python %}
import numpy as np
Alist=list()
for i in range(10):
    Alist.append(np.square(i))
print(Alist)
{% endhighlight %}

```
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

#### <u>List Comprehension Method</u>:
{% highlight python %}
import numpy as np
Alist = [np.square(i) for i in range(10)]
print(Alist)
{% endhighlight %}

```
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

<br>
<h3 id='example2'> <strong>Adding Condition</strong></h3>
Square the number from 0 to 9, and store the odd number to a list:

#### <u>For Loop Method</u>:
{% highlight python %}
import numpy as np
odd=list()
for i in range(10):
    num = np.square(i)
    if num % 2 !=0:
        odd.append(num)
print(odd)
{% endhighlight %}

```
[1, 9, 25, 49, 81]
```

#### <u>List Comprehension Method</u>:
* The `if` statement is put at the end
{% highlight python %}
import numpy as np
odd = [np.square(i) for i in range(10) if np.square(i)%2 !=0]
print(odd)
{% endhighlight %}

```
[1, 9, 25, 49, 81]
```

<br>
<h3 id='example3'> <strong>Adding if... else... Statement</strong></h3>
Square the number from 0 to 9 and plus 1 for each of number. Then, create a list to store a list of strings.When the number is an odd number, store 'odd'. Otherwise, store 'even'.

#### <u>For Loop Method</u>:
{% highlight python %}
import numpy as np
stringlist=list()
for i in range(10):
    num = np.square(i) + 1
    if num % 2 !=0:
        stringlist.append('odd')
    else:
        stringlist.append('even')
print(stringlist)
{% endhighlight %}

```
['odd', 'even', 'odd', 'even', 'odd', 'even', 'odd', 'even', 'odd', 'even']
```

#### <u>List Comprehension Method</u>:
The position of `if` statement has been moved to front and followed by the else statement
{% highlight python %}
import numpy as np
stringlist = ['odd' if (np.square(i)+1)%2 !=0 else 'even' for i in range(10)]
print(stringlist)
{% endhighlight %}

```
['odd', 'even', 'odd', 'even', 'odd', 'even', 'odd', 'even', 'odd', 'even']
```

<br>
<h3 id='example4'> <strong>Nested ifs in list comprehension</strong></h3>
<h4 id='example4-1'> 1. Two ifs</h4>

#### <u>For Loop Method</u>:
{% highlight python %}
import numpy as np
str5list=list()
for i in range(10):
    num = np.square(i) + 1
    if (num % 2 != 0):
        if (num % 5 == 0):
            str5list.append(num)
print(str5list)
{% endhighlight %}

```
[5, 65]
```

#### <u>List Comprehension Method</u>:
{% highlight python %}
import numpy as np
str5list = [(np.square(i)+1) for i in range(10) if ((np.square(i)+1)%2 !=0) if ((np.square(i)+1)%5 ==0)]
print(str5list)
{% endhighlight %}

```
[5, 65]
```

<h4 id='example4-2'> 2. Ifs and else with three outputs</h4>

#### <u>For Loop Method</u>:
{% highlight python %}
import numpy as np
str5list=list()
for i in range(10):
    num = np.square(i) + 1
    if (num % 2 != 0):
        str5list.append('odd')
    else:
        if (num % 5 == 0):
            str5list.append('odd and True')
        else:
            str5list.append('false')
print(str5list)
{% endhighlight %}

```
['odd',
 'false',
 'odd',
 'odd and True',
 'odd',
 'false',
 'odd',
 'odd and True',
 'odd',
 'false']
```

#### <u>List Comprehension Method</u>:
{% highlight python %}
import numpy as np
str5list = ['odd'  if ((np.square(i)+1)%2 !=0) else 'odd and True' if ((np.square(i)+1)%5 ==0) else 'false' for i in range(10)]
print(str5list)
{% endhighlight %}

```
['odd',
 'false',
 'odd',
 'odd and True',
 'odd',
 'false',
 'odd',
 'odd and True',
 'odd',
 'false']
```


<p align="center"><a href="#top">Top</a></p>


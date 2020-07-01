---
layout: post
title: "Statistics Summary Part 1: Statistics Basic"
date: 2020-06-26
theme: minimal
mathjax: true
categories: Math
---
<div id='top'>
  <p align="center"><img src="{{site.baseurl}}/assets/images/post/statistics/statistics101.png" title=""></p>
  <p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">Statistics 101</p>
</div>

## Statistics Basic
There are some baisc terms in the statistics:
1. Population
2. Sample
3. Mean
4. Median
5. Mode
6. Variance
7. Standard Deviation
8. Standard Error

Among these terms,the `Mean`, `Mode` and `Median` are called *<u><a href="https://en.wikipedia.org/wiki/Central_tendency">Measures of Central Tendency</a></u>*. `Variance`, `Standard Deviation` and `Standard Error` are also called *<u>Measures of Dispersion</u>*.

__(1). Population:__ 

The entire group that one desires information about.

__(2). Sample:__ 

A subset of the population taken because the entire population is usually too large to analyze. Its characteristics are taken to be representative of the population.

__(3). Mean:__ 

Also called the arithmetic mean or average.
The sum of all the values in the sample divided by the number of values in the sample/population. $\mu$ is the mean of the population; 	$\overline{x}$ is the mean of the sample.

__(4). Median:__ 

The value separating the higher half of a sample/population from the lower half. Found by arranging all the values from lowest to highest and taking the middle one (or the mean of the middle two if there are an even number of values)

__(5). Mode:__ 

The mode of a set of data values is the value that appears most often.

__(6). Variance:__ 

Measure dispersion around the mean. Determined by averaging the squared differences of all the values from the mean.

Variance of a population is $\sigma^2$.
<p align="center">$
\sigma^2 = \frac{\Sigma{(x-\mu)^2}}{n}
$</p>

It can be calculated by subtracting the square of the mean from the average of the squared scores:
<p align="center">$
\sigma^2 = \frac{\Sigma{x^2}}{n}-\mu^2
$</p>

Variance of a sample is $s^2$; denominator is $n-1$.
<p align="center">$
s^2 = \frac{\Sigma{(x-\overline{x})^2}}{n-1}
$</p>

It can be calculated by:
<p align="center">$
s^2 = \frac{\Sigma{x^2}-\frac{(\Sigma{x})^2}{n}}{n-1}
$</p>

__(7). Standard Deviation:__ 

Square root of the variance. Also measures dispersion around the mean. <u>It quantifies the variation within a set of measurements.</u>

$\sigma$ is the standard deviation of the population and $s$ is the standard deviation of the sample.

__(8). Standard Error:__ 

<u>The standard error quantifies the variation in the means from multiple sets of measurements.</u> It is an estimate of the standard deviation of the sampling distribution - the set of all samples of size $n$ that can be taken from a population. It measures how far the sample mean of the data is likely to be from the true population mean. It is always smaller than `Standard Deviation`.

The standard error of the mean (SEM) can be expressed as:

<p align="center">$
\sigma_\bar{x} = \frac{\sigma}{\sqrt{n}}
$</p>

where $\sigma$ is the `standard deviation of the population` and $n$ is the `size (number of observations) of the sample`.

Since the `population standard deviation` is seldom known, the standard error of the mean is usually estimated as the sample standard deviation divided by the square root of the sample size (assuming statistical independence of the values in the sample).

<p align="center">$
s_\bar{x} \approx \frac{s}{\sqrt{n}}
$</p>

where $s$ is the `sample standard deviation` (i.e., the sample-based estimate of the standard deviation of the population), and $n$ is the `size (number of observations) of the sample`.

In those contexts where `standard error of the mean` is defined not as the `standard deviation of the sample mean`, but as its estimate, this is the estimate typically given as its value. Thus, it is common to see standard deviation of the mean alternatively defined as:

<p align="center">$
s_\bar{x} = \frac{s}{\sqrt{n}}
$</p>

The standard deviation of the sample mean is equivalent to the standard deviation of the error in the sample mean with respect to the true mean, since the sample mean is an unbiased estimator. Therefore, the standard error of the mean can also be understood as the standard deviation of the error in the sample mean with respect to the true mean (or an estimate of that statistic).


<p align="center"><a href="#top">Top</a></p>


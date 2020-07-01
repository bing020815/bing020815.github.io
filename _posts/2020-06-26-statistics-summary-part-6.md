---
layout: post
title: "Statistics Summary Part 6: Multiple Experiments"
date: 2020-07-01
theme: minimal
mathjax: true
categories: Math
---
<div id='top'>
  <p align="center"><img src="{{site.baseurl}}/assets/images/post/statistics/binomial_distribution.png" title="" style="width: 40%"><img src="{{site.baseurl}}/assets/images/post/statistics/poisson-distribution.png" title="" style="width: 40%"></p>
  <p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">Binomial Distribution and Poisson Distribution; <a href="https://www.statisticshowto.com/probability-and-statistics/binomial-theorem/binomial-distribution-formula/">Source 1</a> and <a href="https://www.statisticshowto.com/poisson-distribution/">Source 2</a></p>
</div>


## Binomial Distribution

A binomial distribution can be thought of as simply the probability of a `SUCCES`S or `FAILURE` outcome in an experiment or survey that is repeated multiple times. 

The binomial is a type of distribution that has two possible outcomes. For example, a coin toss has only two possible outcomes: heads or tails and taking a test could have two possible outcomes: pass or fail. 

<ul style="list-style: none;">
  <li>The formula for Binomial Distribution is:</li>
  <li style="display: inline; margin-right: 10%">$
  P(X = m) = \frac{n! \times p^m \times (1-p)^(n-m)}{m! \times (n-m)!}
$</li>
  <li style="display: inline; ">$\text{where `m` is outcome of event X in `n` total trials with `p`=probability of X occuring once}$</li> 
</ul>


__Example:__   
What is the probability that a couple has one boy out of five children?

<ul style="list-style: none;">
  <li>Number of trials (n) = 5</li>
  <li>Probability of getting a boy (p) = 0.5</li>
  <li>Number of outcomes (m) = 1</li>
  <li><p align="center">$
  P(X = 1) = \frac{n! \times p^m \times (1-p)^(n-m)}{m! \times (n-m)!} = \frac{5! \times 0.5^1 \times (1-0.5)^(5-1)}{1! \times (5-1)!} = 0.15625
$</p></li>
</ul>

<br>



## Poisson Distribution

A Poisson distribution is a tool that helps to predict the probability of certain events from happening when you know how often the event has occurred. It gives us the probability of a given number of events happening in a fixed interval of time.

The binomial distribution works for a small number of trials but as n gets too large, the factorials become unwieldy.
THe Poisson distribution is an estimate of the binomial distribution for large n.

<ul style="list-style: none;">
  <li>The formula for Poisson Distribution is:</li>
  <li style="display: inline; margin-right: 10%">$
  P(X = m) = \frac{e^{-\lambda} \times (\lambda)^m}{m!}
$</li>
  <li style="display: inline; ">$\text{where $\lambda$ (event rate) is also known as the number of expected outcomes for event X }$</li> 
</ul>

__Example:__   
The average number of major storms in your city is 2 per year. What is the probability that exactly 3 storms will hit your city next year?

<ul style="list-style: none;">
  <li>Number of expected outcomes for event X ($\lambda$) = 3</li>
  <li>e = 2.71828</li>
  <li>Number of outcomes (m) = 3</li>
  <li><p align="center">$
  P(X = 3) = \frac{e^{-\lambda} \times (\lambda)^m}{m!} = \frac{2.71828^{-2} \times (2)^3}{3!} = \frac{0.13534 \times 8}{6}= 0.180
$</p></li>
</ul>

<p align="center"><a href="#top">Top</a></p>


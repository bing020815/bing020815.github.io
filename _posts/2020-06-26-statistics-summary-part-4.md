---
layout: post
title: "Statistics Summary Part 4: Chi-Square Test"
date: 2020-06-30
theme: minimal
mathjax: true
categories: Math
---
<div id='top'>
  <p align="center"><img src="{{site.baseurl}}/assets/images/post/statistics/statistics101.png" title=""></p>
  <p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">Statistics 101</p>
</div>


## Chi-Square Test

A chi-square test, also written as $X^2$ test, is a statistical hypothesis test that is valid to perform when the test statistic is chi-square distributed under the null hypothesis, specifically Pearson's chi-square test and variants thereof. Pearson's chi-square test is used to determine whether there is a statistically significant difference between the expected frequencies and the observed frequencies in one or more categories of a contingency table.

<p align="center"><img src="{{site.baseurl}}/assets/images/post/statistics/chi-square-table.jpg" title=""></p>
<p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">Chi-square table; <a href="https://www.oreilly.com/library/view/random-data-analysis/9780470248775/app1.xhtml">Source</a></p>

There are two types of chi-square tests. Both use the chi-square statistic and distribution for different purposes:
1. [For Goodness of Fit](#goodnessoffit)
2. [For Independence](#independence)

We are going to discuss each of cases in detail.

<h3 id="goodnessoffit"><strong>(1). Goodness of Fit Test:</strong></h3> 

The goodness of fit test is used to test if sample data fits a distribution from a certain population (i.e. a population with a normal distribution or one with a Weibull distribution). In other words, it tells you if your sample data represents the data you would expect to find in the actual population.

<ul style="list-style: none;">
  <li>$H_0: \text{The observed pattern fits the given distribution}$</li>
  <li>$H_a: \text{The observed pattern does not fit the given distribution}$</li>
  <li>The chi-square statistic:</li>
    <ul style="list-style: none;">
      <li style="display: inline; margin-right: 10%">$X^2 = \Sigma{\frac{(O-E)^2}{E}}$</li>
      <li style="display: inline;">Where $O$ is the observed value and $E$ is the expected value</li>
      <li style="font-size: 0.8em; color: grey; font-style: italic; margin-right: 10%">Formula for categorical discrete data</li>
    </ul>
  <li>$\text{Degree of freedom = number of categories in the distribution -1}$</li>
</ul>

Get the p-value from the Chi-square table using the calculated $X^2$ and `df` values:
* If the p-value is less than $\alpha$, $p < \alpha$, <u>the observed data does not fit the expected distribution</u>
* If the p-value is greater than $\alpha$, $p > \alpha$, <u>the data likely fits the expected distribution</u>


__Example 1:__  
You breed Puffskeins and would like to determine the pattern of inheritance for coat color and purring ability. Puffskeins come in either pink or purple and can either purr or hiss. You breed a puredbred, pink purring male with a purebred, purple hissing female. All individuals of the $F_1$ generation are pink and purring. The $F_2$ offspring are shown below. Do the alleles for coat color and purring ability assort independently (assume $\alpha = 0.05$)?

|Pink and Purring|Pink and Hissing|Purple and Purring|Purple and Hissing|
|:---:|:---:|:---:|:---:|
|143|60|55|18|


Hypothesis:  
Independent assortment means the distribution of $F_1$ generation has a phenotypic ratio of 9:3:3:1 (hypothetically).
<p align="center">$H_0: \text{The observed distribution of $F_2$ offspring fits the distribution of $F_1$ generation}$</p>
<p align="center">$H_a: \text{The observed distribution of $F_2$ offspring does not fit the distribution of $F_1$ generation}$</p>

Calculate the expected values:

|Pink and Purring|Pink and Hissing|Purple and Purring|Purple and Hissing|
|:---:|:---:|:---:|:---:|
|155.25|51.75|51.75|17.25|

The chi-square statistic:  
<p align="center">$
  X^2 = \Sigma{\frac{(O-E)^2}{E}}=\frac{(143-155.25)^2}{155.25} + \frac{(55-51.75)^2}{51.75} + \frac{(55-51.75)^2}{51.75}  + \frac{(18-17.25)^2}{17.25} \approx 2.519
$</p>
The degrees of freedom:  
<p align="center">$df=4-1=3$</p>

From the Chi-square table, the p-value is greater than `0.1` ($\alpha = 0.05$). So, we we fail to reject $H_0$. The observed distribution of $F_2$ offspring fits the distribution of $F_1$ generation.The alleles for coat color and purring ability do assort independently in Puffskeins.


__Example 2:__  
You are studying the pattern of dispersion of king penguins and the diagram below represents an area you sampled. Each dot is a penguin. Do the penguins display a uniform distribution (assume $\alpha=0.05$)

<p align="center"><img src="{{site.baseurl}}/assets/images/post/statistics/goodness-of-fit-example2.png" title=""></p>

Hypothesis:  
<p align="center">$H_0: \text{There is a uniform distribution of penguins}$</p>
<p align="center">$H_a: \text{There is not a uniform distribution of penguins}$</p>
There are a total of 25 penguins. So, if there is a uniform distribution, there should be 2.778 penguins per square.  
There actual observed values are 2, 4, 4, 3, 3, 3, 2, 3, 1, so the $X^2$ statistic is:
<p align="center">$
  X^2 = \Sigma{\frac{(O-E)^2}{E}}= \frac{(2-2.778)^2}{2.778} + \frac{(4-2.778)^2}{2.778} + \frac{(4-2.778)^2}{2.778} + \frac{(3-2.778)^2}{2.778} + \frac{(3-2.7787)^2}{2.778} + \frac{(3-2.778)^2}{2.778} + \frac{(2-2.778)^2}{2.778} + \frac{(3-2.778)^2}{2.778} + \frac{(1-2.778)^2}{2.778} \approx 2.72
$</p>
The degrees of freedom:  
<p align="center">$df=9-1=8$</p>

From the Chi-square table, the p-value is greater than `0.95` ($\alpha = 0.05$). So, we fail to reject $H_0$. The penguins do display a uniform distribution.

<br>

<h3 id="independence"><strong>(2). Independence Test:</strong></h3> 

A chi-square test for independence compares two variables in a contingency table to see if they are related (independence). In a more general sense, it tests to see whether distributions of categorical variables differ from each another. 
* A very small chi square test statistic means that your observed data fits your expected data extremely well. 
  + In other words, there is a relationship.
* A very large chi square test statistic means that the data does not fit very well. 
  + In other words, there is not a relationship.

Workflow:

<ul style="list-style: none;">
  <li>$H_0: \text{The two variables are independent (not related)}$</li>
  <li>$H_a: \text{The two variables are not independent (related)}$</li>
  <li>It does not make any assumptions about an expected distribution</li>
  <li>The observe values, $\#_1, \#_2, \#_3, \#_4$, are usually presented as a table. Each row is a category of variable 1 and each column is a category of variable 2</li>
<p align="center"><img src="{{site.baseurl}}/assets/images/post/statistics/chi-square-contingency-table.png" title=""></p>
  <li>The proportion of category x of variable 1 is the number of individuals in category x divided by the total number of individuals, $\frac{\#_1 + \#_3}{\#_1 + \#_2 + \#_3 + \#_4}$.</li>
  <li>Assuming independence, the expected number of individuals that fall within category a of variable 2 is the proportion of category x multiplied by the number of individuals in category a, $(\frac{\#_1 + \#_3}{\#_1 + \#_2 + \#_3 + \#_4})(\#_1 + \#_2)$.</li>
  <li>The expected value is:</li>
  <li><p align="center">$E = \frac{(\#_1 + \#_3)(\#_2 + \#_4)}{\#_1 + \#_2 + \#_3 + \#_4} = \frac{(\text{row total})(\text{column total})}{\text{grand total}}$</p></li>
  <li>The chi-square statistic:</li>
    <ul style="list-style: none;">
      <li style="display: inline; margin-right: 10%">$X^2 = \Sigma{\frac{(O-E)^2}{E}}$</li>
      <li style="display: inline;">Where $O$ is the observed value and $E$ is the expected value</li>
      <li style="font-size: 0.8em; color: grey; font-style: italic; margin-right: 10%">Formula for categorical discrete data</li>
    </ul>
  <li>Degree of freedom:</li>  
    <ul style="list-style: none;">
      <li style="display: inline; margin-right: 10%">$\text{df = (r-1)(c-1)}$</li>
      <li style="display: inline;">Where $r$ is the number of rows and $c$ is the number of columns</li>
    </ul>
  <li>Read the p-value from $X^2$ table.</li>
  
</ul>  



__Example:__   
Given the data below, is there a relationship between fitness level and smoking habits (assume $\alpha = 0.05$)?
<p align="center"><img src="{{site.baseurl}}/assets/images/post/statistics/independent-example.png" title=""></p>

Hypothesis:  
<p align="center">$H_0: \text{Fitness level and smoking habits are independent (not related)}$</p>
<p align="center">$H_a: \text{Fitness level and smoking habits are not independent (related)}$</p>

Use the expected value formula, $\frac{(\text{row total})(\text{column total})}{\text{grand total}}$, to get the expected counts:
<p align="center"><img src="{{site.baseurl}}/assets/images/post/statistics/independent-example-expected-counts.png" title=""></p>

The chi-square statistic:  
<p align="center">$$
  X^2 = \Sigma{\frac{(O-E)^2}{E}} = \frac{(113-123.75)^2}{123.75} + \frac{(113-124)^2}{124} + \frac{(110-124.26)^2}{124.26} + etc... = 91.73
$$</p>
And the degrees of freedom are:  
<p align="center">$df = (r-1)(c-1) = (4-1)(4-1) = 9$</p>

From the Chi-square table, the p-value is less than `0.005` ($\alpha = 0.05$). So, we reject $H_0$ and conclude that there is a relationship between fitness level and smoking habits.

<p align="center"><a href="#top">Top</a></p>


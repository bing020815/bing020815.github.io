---
layout: post
title: "Regression: Normal Distribution"
date: 2020-06-15
theme: minimal
mathjax: true
---
<div id='top'>
  <p align="center"><img src="{{site.baseurl}}/assets/images/post/regression/gaussian.png" title=""></p>
  <p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">Typical Normal (Gaussian) Distribution; <a href="https://blogs.sas.com/content/iml/2019/07/22/extreme-value-normal-data.html">Source</a></p>
</div>


Normal distribution (Gaussian distribution) is one of the most important concepts.

Whenever we run a model or perform data analysis, we need to check the distribution of the dependent variable and independent variables and to see if they are normally distributed. If some variables are skewed or not normally distributed, it will affect the accountability of significant factors.

The variable that should be normally distributed is `prediction error`.

<p align="center">$\text{Y} = \text{Coef} * \text{X} + \text{C} + \text{Error}$</p>
<p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">Simple linear regression equation</p>

If the `prediction error` is <u>normal distribution with the mean of zero</u>, the siginificant factors conlcuded from the regression is reliable. However, if te the `distribution of error` significantly <u>deviates from the mean of zero and not being normally distributed</u>, the factors that we choose to be significant may not actually be significant enough to contribute to the output `y`.  

To select the significant predicting factors, after we have constructed a model and prediction, we should plot a chart to see the distribution of prediction error.  
{% highlight python %}
# create a normal distributed data and non-normal data
import numpy as np
from scipy import stats
sample_normal=np.random.normal(loc=0, scale=4, size = 1000)
sample_nonnormal = stats.loggamma.rvs(c= 5, loc=0, scale=1, size=1000, random_state=1) + 20
{% endhighlight %}

## Test normality

To test normality of data, we can plot distribution plot, QQ-plot or using [Shapiro-Wilk test](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.shapiro.html)

__(1). Distribution plot:__  
    Simply plot the distribution curve and see whether the plot follows bell **curve shape**. Non-normal sample is clearly left tailed.

{% highlight python %}
import seaborn as sns
import matplotlib.pyplot as plt
sns.distplot(sample_normal)
plt.axvline(x=np.mean(sample_normal), color='k', linestyle='--')
plt.title('Distribution of Normally distributed sample')
plt.show()

sns.distplot(sample_nonnormal)
plt.axvline(x=np.mean(sample_nonnormal), color='k', linestyle='--')
plt.title('Distribution plot of Non-Normally distributed sample')
plt.show()
{% endhighlight %}

<p align="center"><img src="{{site.baseurl}}/assets/images/post/regression/normal_barplot.png" title=""><img src="{{site.baseurl}}/assets/images/post/regression/nonnormal_barplot.png" title=""></p>

__(2). Shapiro-Wilk test:__  
    Use the `Shapiro-Wilk test`, based on decided p-value threshold, usually <u>we reject H0 at <i>5% significance level</i> meaning if p-value is greater than 0.05 then we accept it as normal distribution</u>:

**PS**: If sample size is greater than 5000, you should use test statistics instead of p-value as the indicator to decide.

{% highlight python %}
# null hypothesis: the data was drawn from a normal distribution
test1= stats.shapiro(sample_normal)
test2 = stats.shapiro(sample_nonnormal)
print ('Test Statistics: {}\nP-value: {}\nFail to reject H0: the data was drawn from a normal distribution\n'.format(test1[0], test1[1]))
print ('Test Statistics: {}\nP-value: {}\nReject H0: the data was not drawn from a normal distribution\n'.format(test2[0], test2[1]))
{% endhighlight %}

```
Test Statistics: 0.9982317686080933
P-value: 0.3935606777667999
Fail to reject H0: the data was drawn from a normal distribution

Test Statistics: 0.9849225282669067
P-value: 1.2197391541235447e-08
Reject H0: the data was not drawn from a normal distribution
```

__(3). QQ-plot:__ 
    Very popular plot to see whether the distribution of data follow normal distribution.

{% highlight python %}
import statsmodels.api as sm
fig = sm.qqplot(sample_normal,line='s')
plt.title('Distribution of Normally distributed sample')
plt.show()

fig = sm.qqplot(sample_nonnormal,line='s')
plt.title('Distribution plot of Non-Normally distributed sample')
plt.show()
{% endhighlight %}

<p align="center"><img src="{{site.baseurl}}/assets/images/post/regression/normal_qq.png" title=""><img src="{{site.baseurl}}/assets/images/post/regression/nonnormal_qq.png" title=""></p>


## Fix the normality issue

Usually there are 2 reasons why this issue (error does not follow normal distribution) would occur:
1. Dependent or independent variables are not normally distributed (based on skewness or kurtosis of the variable)
2. Existence of a few outliers/extreme values which disrupt the model prediction

The solution for those are:
1. Remove `outlier` from both `dependent` and `independent variables`
2. Transform some non-normal variables to normal by using transformation function, such as `box-cox transformation`


Below is the mathematic formula for __Box-Cox transformation__. Lambda value will be decided based on the data points to provide the best normal distribution shape after the transformation. We can directly use Python package to help us transform the data.

<p align="center">$
\begin{equation}
       y_i^{(\lambda)}= 
        \begin{cases}
            \frac{y_i^{\lambda}-1}{\lambda} & \text{if $\lambda \neq 0 $,} \\
            \ln y_i & \text{if $\lambda = 0$}
        \end{cases}
    \end{equation}
$</p>

{% highlight python %}
#transform the data using box-cox transformation
sample_transformed, lambd = stats.boxcox(sample_nonnormal)
#plot the distribution curve and QQ-plot for transformed data
sns.distplot(sample_nonnormal)
plt.title('Distribution plot of Non-Normally distributed sample')
plt.axvline(x=np.mean(sample_nonnormal), color='k', linestyle='--')
plt.show()

sns.distplot(sample_transformed)
plt.title('Distribution plot of transformed Non-Normally distributed sample')
plt.axvline(x=np.mean(sample_transformed), color='k', linestyle='--')
# plt.ylim(bottom = 0 , top = 0.001)
plt.show()

fig = sm.qqplot(sample_transformed,line='s')
plt.title('QQ-plot of Non-Normally distributed sample')
plt.show()

print("Shapiro-Wilk test\n")
test3= stats.shapiro(sample_normal)
print ('Test Statistics: {}\nP-value: {}\nFail to reject H0: the data was drawn from a normal distribution\n'.format(test3[0], test3[1]))
{% endhighlight %}

<p align="center"><img src="{{site.baseurl}}/assets/images/post/regression/nonnormal_barplot.png" title=""><img src="{{site.baseurl}}/assets/images/post/regression/transform_distribution.png" title=""><img src="{{site.baseurl}}/assets/images/post/regression/transform_qq.png" title=""></p>
```
Shapiro-Wilk test

Test Statistics: 0.9982317686080933
P-value: 0.3935606777667999
Fail to reject H0: the data was drawn from a normal distribution
```
Although the transformed non-normal distribution looks a bit weird, according to the `Shapiro-Wilk test` and `QQ-plot`, we can see that the non-normal distributed sample is normally distributed after the `box-cox transformatio`.

In conclusion, if you try to find `significant predicting factors` or define the `confidence interval`, please remember to check the `distribution of the error term` after the model has being built.   
 
If dependent variables or independent variables are not normal distributed then we can use `box-cox transformation` to transform it to make error term more normally distributed.

Except for the normality statistical assumption, there are other statistical assumptions in regression model, such as `Multi-Collinearity` in Regression.


Reference: [Is Normal Distribution Necessary in Regression?](https://towardsdatascience.com/is-normal-distribution-necessary-in-regression-how-to-track-and-fix-it-494105bc50dd)

<p align="center"><a href="#top">Top</a></p>


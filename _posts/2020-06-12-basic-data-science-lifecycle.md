---
layout: post
title: "Basic Data Science Lifecycle"
date: 2020-06-12
theme: minimal
mathjax: true
---
<div id='top'>
</div>
The basic data science lifecycle consists of four parts, `Gathering Data`, `Cleaning/Formatting Data`, `Analysis`, and `Conclusion`. Each part is equally important and crucial.    
Here is a diagram of basic data science lifecycle:   

<img src="{{site.baseurl}}/assets/images/post/DS_lifecycle.png" title="Basic Data Science Lifecycle" class="align-center" style="width: 90%">

## Gathering Data
There are two kinds of data when we talk about data collection:
* Observational data
* Experimental data

	
The data format can also be categorized into two:
+ Structured data
+ Unstructured data


**Observational data** data usually are collected from Surveys, Interviews, Phone Calls, or Websites through an API. It can be both structured and unstructured type of data.  
**Experimental data**, on the other hand, are different. It is usually in a structured format to contain the experiment records for both Control Group and Treatment Group for statistic analysis. Because data are messy, we collect dirty data easily without cautious design. An intellectual collecting method can help eliminate the risk of dirty data. It can reduce the bias, have the data that can represent the population, have good data to avoid <abbr title="Garbage in, garbage out">GIGO</abbr>.
  

## Cleaning/Formatting Data
To clean and format data, some steps need to be done, such as **data cleansing**, **data wrangling**. Usually, there is a pipeline that will be built to contain the process of **data cleansing**, **data wrangling**. **Data cleansing** includes the job of dealing with missing values, duplicates, and inaccurate data, such as typo. **Data wrangling** involves *transforming data*, such as converting the data into the same unit or the same format, and *mapping data*. It includes the *Normalization*, *Standardization*, and *Transformation*.

*Normalization* is to bound values between to numbers, such as 0 and 1. The classic examples of normalization have "min-max scaler" and "z-score scaler".

*Standardization* is to let the data have a mean of zero and variance of 1. The "standard scaler" is usually used for standardizing data.

*Transformation* is to apply math functions or other functions on data. The math functions are "log", "square  root" or "box-cox". Other user-defined functions can be used to achieve feature engineering.

The last step in this part is to have **visualization**. **visualization** is important. Humans can interpret data through visualization and they are eye-catching for both technical person and non-technical person.


## Analysis
This part is to build models and perform analyses based on the models performance and results. There are two type of models, **Supervised** and **unsupervised.** When we build a model, first thing to check is to see if data have labels or not. If it does not have labels, there are several ways to do here, such as using clustering technique, unsupervised learning, to have cluster labels or getting labels by hand. The purpose of supervised learning is to do modeling and classification tasks. The classic supervised learning algorithm are "logistics", "SVM", "Naive Bayes", "Decision Tree" and "KNN" The purpose of unsupervised learning is to discover. The example of unsupervised learning algorithms are "K-Means", "PCA", "Topic Modeling", and "Asscoiation Rule"

The last step of analysis is to evaluate models. Having the correct evaluation metric is important. The classic evaluation metrics for classification tasks are Accuracy, Precision, Recall/Sensitivity, and F1-score derived from the confusion matrix. Some may use ROC curve as the evaluation metric as well.

Explanation of the metric terms:
* Accuracy Rate
	+ It is focusing on the cases that were correctly predicted
* Precision Rate
	+ It is focusing on the predicted cases that were truly true
* Recall/Sensitivity
	+ It is focusing on the true cases that were correctly found
* F1-Score
	+ Harmonic mean of precision and recall, a hybrid version of the overall score
	+ Hybrid version of the overall score
* ROC Curve
	+ A plot of the True Positive Rate on the y-axis versus the False Positive rate on the x-axis for every possible classification threshold

The choice of the evaluation metric depends on the business objective.



## Conclusion
The last part of basic data science life cycle is to bring the conclusion on the table. Usually, a report should have the introduction of the data and the process, the methods implemented during process, results that are written for both technical person and non-technical person, and conclusion for non-technical audiencea only in order to complete a story.


<p align="center"><a href="#top">Top</a></p>



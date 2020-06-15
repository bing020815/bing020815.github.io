---
layout: post
title: "Basic Data Science Lifecycle"
date: 2020-06-12
---

<div id='post-topic'>
<p>The basic data science lifecycle consists of four parts, `Gathering Data`, `Cleaning/Formatting Data`, `Analysis`, and 'Conclusion'. Each parts are equally important and crucial. 
Here is a diagram of basic data science lifecycle:<br>
<img src="{{site.baseurl}}/assets/images/post/DS_lifecycle.png" title="Basic Data Science Lifecycle"  style="width: 90%">
</p>
</div>
  

<div id='gathering-data'>
<h2>Gathering Data</h2> 
There are two kinds of data when we talk about data collection:
<ul>
	<li>Observational data</li>
	<li>Experimental data</li>
</ul>
	
<p>The data format can also be categorized into two:</p>
<ul style="list-style: circle;">
	<li>Structured data</li>
	<li>Unstructured data</li>
</ul>

<p><b>Observational data</b> data usually are collected from Surveys, Interviews, Phone Calls or Websites throguh a API. It can be both structured and unstructured type of data. <b>Experimental data</b>, on the other hand, are different. It is usually in a structured format to contain the experiment records for both Control Group and Treatment Group for statistic analysis.</p>
<p>Because data are messy, we can easily collect the dirty data without cautious design. An intellectual collecting method can help eliminate the risk of dirty data. It can reduce the bias, have the data that can represent population, have good data to avoid GIGO.</p>
</div>
  

<div id='cleaning-data'>
<h2>Cleaning/Formatting Data</h2>
<p>To clean and format data, some of steps need to be doned, such as <b>data cleansing</b>, <b>data wrangling</b>. Ususally, there is a pipeline will be built to contain the process of <b>data cleansing</b>, <b>data wrangling</b>. <b>Data cleansing</b> includes the job of dealing with missing values, duplicates and inaccurate data, such as typo. <b>Data wrangling</b> involves <i>transforming data</i>, such as converting the data into the same unit or the same format, and <i>mapping data</i>. It includes the <i>Normalization</i>, <i>Standardization</i> and <i>Transformation</i>. </p>

<p>Normalization is to bound values between to numbers, such as 0 and 1. The classic examples of normalization have "min-max scaler" and "z-score scaler" </p>

<p>Standardization is to let the data have mean of zero and variance of 1. The "standard scaler" is usually used for standardizing data.</p>

<p>Transformation is to apply math functions or other functions on data. The math functions are "log", "sqare root" or "box-cox". Other user-defined functions can be used to achieve feature engineering.</p>

<p>The last step in this part is to have <b>visualization</b>. <b>visualization</b> is important. Human can interpret data through visualization and they are eye-catching for both technical person and non-technical person.</p>
</div>  

<div id='analysis'>
<h2>Analysis</h2>
<p>This part is to build models and perform analysis based on the models performance and results. There are two type of models, <b>Supervised</b> and <b>unsupervised.</b> When we build a model, first thing to check is to see if data have label or not. If it does not have label, several ways to do here such as using clustering technique, unsupervised learning, to have cluster label or getting labels by hand. The purpose of supervised learning is to do modeling and classification tasks. The classic supervised learning algorithm are "logistics", "SVM", "Naive Bayes", "Decision Tree" and "KNN" The purpose of supervised learning is to do discovery. The example of unsupervised learning algorithms are "K-Means", "PCA", "Topic Modeling", and "Asscoiation Rule"</p> 

<p>The last step of analysis is to evaluate models. Having the correct evaluation metric is important. The classic evaluation metric for classification tasks are Accuracy, Precision, Recall/Sensitivity and F1-score derived from confusion matrix. Some may use ROC curve as the evaluation metric as well.
</ul>
<p>Explanation of the metric terms:</p>
<ul >
	<li>Accuracy Rate</li>
		<ul style="list-style: circle;">
			<li>It is focusing on the cases that were correctly predicted</li>
		</ul>
	<li>Precision Rate</li>
			<ul style="list-style: circle;">
			<li>It is focusing on the predicted cases that were truly true</li>
		</ul>
	<li>Recall/Sensitivity</li>
		<ul style="list-style: circle;">
			<li>It is focusing on the true cases that were correctly found</li>
		</ul>
	<li>F1-Score</li>
		<ul style="list-style: circle;">
			<li>Harmonic mean of precision and recall, a hybrid version of the overall score</li>
			<li>Hybrid version of the overall score</li>
		</ul>
	<li>ROC Curve</li>
		<ul style="list-style: circle;">
			<li>A plot of the True Positive Rate on the y-axis versus the False Positive rate on the x-axis for every possible classification threshold</li>
		</ul>
</ul>

<p>The choice of the evaluation metric depends on the business objective. </p>
</div>


<div id='conclusion'>
<h2>Conclusion</h2>
<p>The last part of basic data science life cycle is to bring the conclusion on the table. Usually a report should have the introduction of the data and process, the methods implemented during process, results that are written for both technical person and non-technical person, and colcusion for non-technical audience only to complet a story. </p>
</div>

<a href="#post-topic"><p align='center' style="color:#455bff">Top</p></a>


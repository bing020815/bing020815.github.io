---
layout: post
title: "Confusion Matrix"
date: 2020-08-07
theme: minimal
mathjax: true
categories: Data-science
---
<div id='top'>
  <p align="center"><img src="{{site.baseurl}}/assets/images/post/data-science/confusion_matrix0.png" title=""></p>
  <p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">Confusion Matrix</p>
</div>


## Confusion Matrix
A confusion matrix is a table that is often used to describe the performance of a classification model (classifier) on a set of test data for which the true values are known. It allows the visualization of the performance of an algorithm.  

In the confusion matrix, there are many evaluation metrics can be derived for evaluating model performance:   

* Accuracy
* Precision
* Recall/sensitivity
* F1-score

`Accuracy rate` is <u>focusing on the cases that were correctly predicted</u>. `Precision` is <u>focusing on the predicted cases that were truly true</u>. (When the precision is higher, it reduces the False Positive/Type I Error). `Recall`, also known as sensitivity, is <u>focusing on the true cases that were correctly found</u>. (When the recall is higher, it reduces the False Negative/Type II Error). And `F1-score` is simply <u> a harmonic mean of precision and recall</u>, a hybrid version of the overall score.  

There are four type of states to describe in confusion matrix:  

* TP (true positive)
	+ An outcome where the model **correctly predicts the positive** class
* TN (true negative) 
	+ An outcome where the model **correctly predicts the negative** class
* FP (false positive / type I error) 
	+ An outcome where the model **incorrectly predicts the positive** class
* FN (false negative / type II error)
	+ An outcome where the model **incorrectly predicts the negative** class
	
<br>
<p align="center"><img src="{{site.baseurl}}/assets/images/post/data-science/confusion_matrix.png" title="" ></p>
<p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">Confusion Matrix Summary Table</p>



Recall and precision for each class:
<div id='postive' style="float: left; margin-right: 10%;">
<ul style="list-style: none; ">
  <li>$Recall_{class=Yes} = \frac{a}{(a + b)} $</li>
  <li>$Precision_{class=Yes} = \frac{a}{(a + c)}$</li>
  <li>$F_1 = \frac{2}{ \frac{1}{P} + \frac{1}{R} } = \frac{2PR}{(P+R)}$</li>
</ul></div>

<div id='negative'>
<ul style="list-style: none; display: inline;">
  <li>$Recall_{class=No} = \frac{d}{(c + d)} $</li>
  <li>$Precision_{class=No} = \frac{d}{(b + d)} $</li>
  <li>where $ \text{ $P = Precision_{class}$ , and $R = Recall_{class}$ }$</li>
</ul></div>

<br>

## Example:   
Calculate precisions, recalls, and F-measure for the following prediction result. See result table below: 
<p align="center"><img src="{{site.baseurl}}/assets/images/post/data-science/confusion_matrix_calculation.png" title="" style="width: 40%"></p>

<div id='postive' style="float: left; margin-right: 10%;">
<ul style="list-style: none; ">
  <li>Class = Positive:</li>
  <li>$Recall_{class=positive} = \frac{a}{(a + b)} = \frac{70}{(70 + 10)} = 0.875$</li>
  <li>$Precision_{class=positive} = \frac{a}{(a + c)} = \frac{70}{(70 + 10)} = 0.875$</li>
  <li>$F1_{class=positive} = \frac{2}{ \frac{1}{P} + \frac{1}{R} } = \frac{2PR}{(P+R)} = \frac{2*0.875*0.875}{0.875+0.875} \approx 0.875$</li>
</ul></div>

<div id='negative'>
<ul style="list-style: none; display: inline;">
  <li>Class = Negative:</li>
  <li>$Recall_{class=negative} = \frac{d}{(c + d)} = \frac{10}{(10 + 10)} = 0.5$</li>
  <li>$Precision_{class=negative} = \frac{d}{(b + d)} = \frac{10}{(10 + 10)} = 0.5$</li>
  <li>$F1_{class=negative} = \frac{2}{ \frac{1}{P} + \frac{1}{R} } = \frac{2PR}{(P+R)} = \frac{2*0.5*0.5}{0.5+0.5} = 0.5$</li>
</ul></div>

<br>
Reference:   
[Confusion matrix](https://en.wikipedia.org/wiki/Confusion_matrix)  
[Metrics and scoring: quantifying the quality of predictions](https://scikit-learn.org/stable/modules/model_evaluation.html#confusion-matrix)



<p align="center"><a href="#top">Top</a></p>

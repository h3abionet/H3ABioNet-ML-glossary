---
title: Measuring model performance
keywords: regression model performance
tags: [regression_performance]
last_updated: Jun 22, 2020

toc: false
sidebar: performance_sidebar
permalink: regression_performance.html
folder: categories/performance
author_profile: true
authors:
 - Olivier Sheik Amamuddy
 - Liqian Ma
 - Amel Ghouila
 - Shakun Baichoo
 - Dassen Sathan
 - Christopher Fields
---

## Assessing the performance of regression models
Mearusing the performance of continuous values inherits the various statistical metrics designed to compare the level of agreement between two samples. One generally aims at maximising theses values. Some example metrics are listed below:

* __mean squared error (MSE)__
The MSE is simply computed by averaging the deviations from the computed mean. If one wants to increase the predictive performance of a regression model, then the differences between the actual and predicted values have to be minimised.
* __Pearson's correlation (R)__
R is a very heavily used method to compare the level of agreement between two lists of numbers.
* __Coefficient of determination (R<sup>2</sup>)__
(R<sup>2</sup>) can be computed as the square of the correlation value. It measures how close data points are a fitted regression line. Similar to the correlation, it shows how good good a linear relationship is between the actual and the predicted values <a href="http://www.learningaboutelectronics.com/Articles/R-squared-calculator.php">ref</a>.

---
title: Assessment of model performance
keywords: model performance
tags: [model_performance]
last_updated: Jun 22, 2020

toc: false
sidebar: performance_sidebar
permalink: performance_intro.html
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

## Assessment of model performance
Assessing the predictive performance of machine learning models is a crucial, but can be potentially complex <a href="https://link.springer.com/chapter/10.1007/978-3-319-18305-3_4">ref</a>. First of all, one has to know whether one is dealing with regression (continuous data) of classification (discrete labels), as there are specific metrics that have been designed/selected to report their degree of correctness. Some commonly used metrics for evaluations of regression models include the mean squared error (MSE) and the squared correlation (R<sup>2</sup>). In the case of classification models, the commonly metrics used to evaluate mode performance consist of values derived from the so-called "confusion matrix". Some examples of such metrics are specificity, sensitivity and accuracy, amongs others.

The composition and distribution of samples used during training play a very important in influencing how a model will perform on unseen data. For this reason, the calculated metrics can be reported as averages based on the same performace metrics being evaluated on shuffled portions from the data. Above all, it is important to ensure the correctness of labeling and description of each sample.

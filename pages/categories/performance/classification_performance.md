---
title: Measuring model performance
keywords: classification model performance
tags: [classification_performance]
last_updated: Jun 22, 2020

toc: false
sidebar: performance_sidebar
permalink: classification_performance.html
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

## Assessment of classification models
A tabulation of the actual and predicted target values is done, to summarise the counts of samples that are correctly and incorrectly predicted. In predicting two values (eg. yes or no), typically the table would have two rows and two columns. The actual labels are read horizontally, while the predictions are read vertically <a href="https://www.wellformedness.com/blog/a-tutorial-on-contingency-tables/"></a>. However, this order can be reversed as well, but this should be mentioned. An example is given in the table below:

<table>
  <tr>
    <th>Predictions/Actual labels</th>
    <th>positive</th>
    <th>negative</th>
  </tr>
  <tr>
    <td>positive</td>
    <td>True positives</td>
    <td>False negatives</td>
  </tr>
  <tr>
    <td>negative</td>
    <td>False positives</td>
    <td>True negatives</td>
  </tr>
</table>

By using this table, one can compute various metrics, such as:
* The sensitivity
This tells how well the model predicts the positive cases
* The specificity
This tells how well the model predicts the negative cases
* The Accuracy
This quantifies how extent that a model predicts both positives and negatives samples correctly.

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

## Assessing the performance of classification models
A tabulation of the actual and predicted target values is done, to summarise the counts of samples that are correctly and incorrectly predicted. In predicting two values (eg. yes or no), typically the table would have two rows and two columns. The actual labels are read horizontally, while the predictions are read vertically <a href="https://www.wellformedness.com/blog/a-tutorial-on-contingency-tables/"></a>. However, this order can be reversed as well, but this should be mentioned. An example is given in the table below:




<table>
  <tr>
    <th colspan="3">Table 1: Contingency table</th>
  </tr>
  <tr>
    <td></td>
    <td colspan="2"><b>Actual labels</b></td>
  </tr>
  <tr>
    <td><b>Predicted labels</b></td>
    <td>positive</td>
    <td>negative</td>
  </tr>
  <tr>
    <td><b>positive</b></td>
    <td>True positives</td>
    <td>False negatives</td>
  </tr>
  <tr>
    <td><b>negative</b></td>
    <td>False positives</td>
    <td>True negatives</td>
  </tr>
</table>

By using this table, one can compute various metrics (some of which are listed below), and in the best of cases aim for values converging towards 100% correctness:
* __Sensitivity__
This tells how well the model predicts the positive cases
* __Specificity__
This tells how well the model predicts the negative cases
* __Accuracy__
This quantifies how extent that a model predicts both positives and negatives samples correctly.

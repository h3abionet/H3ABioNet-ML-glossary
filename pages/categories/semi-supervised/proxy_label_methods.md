---
title: Semi-supervised Learning
keywords: semi-supervised learning
tags: [semi-supervised_learning]
last_updated: Jul 30, 2020

toc: false
sidebar: semi-supervised_learning_sidebar
permalink: proxy_label_methods.html
folder: categories/semi-supervised
author_profile: true
authors:
 - Mohammed Sabry
---

### Proxy-label Methods:
Proxy-label methods are used to produce proxy labels for unlabeled data points, these proxy labels are then used as targets with labeled data in the training process. Despite these proxy labels may be noisy or weak, however they provide additional information to the training process about the relevant task. 

<strong>Some of the methods used to produce proxy labels are:</strong>
* Self Training:
In this method we train a model on labeled data and use this model to predict the classification probability of different classes on unlabeled data, and then the confident predictions or predictions above certain threshold are added to the training set and the training process is repeated all over again until the model can no further produce confident classification or this repetition can be for specific iteration(left to the problem at hand to decide). 
The drawbacks of this method are:
  * The model is unable to correct his own mistakes, thus wrong classification or bias can be amplified quickly through the model's training process.
  * Computational cost(repeating the training process).

* Multi-view Training:
In this method we use multi models trained on different views of the dataset. One of the methods used in Multi-view training is Co-training, in Co-training we construct two different views from the dataset for each data point, then train two models on these two different views, and then add the confident proxy label output of unlabeled data point of one model to the training set of the other model.  

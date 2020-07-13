---
title: Model cross-validation
keywords: cross-validation
tags: [crossvalidation]
last_updated: Jun 22, 2020

toc: false
sidebar: performance_sidebar
permalink: crossvalidation.html
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

## Model cross-validation and resampling 
In order to obtain a fairer estimate of a a trained model's performance on unseen data, the training data samples can be shuffled (resampled) several times to produce a performance score that can be reported as an averaged with an associated deviation. There are many such resampling methods and their use can be influenced by the number of training samples. Depending on the field and the type study, obtaining data samples can often incur an element of cost. This can unfortunately influence the set up of experimental designs, in order to find a trade-off between statistical significance and the budget to be allocated for the research. Common examples of include the Leave One Out Cross Validation (LOOCV), k-fold CV and bootstrapping.

* __LOOCV__ is performed by training on all data samples with the exception one. Each sample sequencially becomes a test sample on each round of training. This technique is often used when the number of samples is small as it would tremendously increase the amount of time needed when the number of samples is large.
* __k-fold CV__ is a generalisation of the LOOCV. Instead of one sample appearing in the test subset, it consists of more sample. The "k" in k-fold CV determines the number of subsets to take from the entire data. It is usually set to 5 or 10, depending on the amount of samples of computational resources available.
* __Bootstrapped performance__ is simply determined by repeatedly selecting random training and test samples from the dataset. The resampling allows duplication of samples to occur either in the training set or the testing set, but samples selected for training do not occur in the test set <a url="https://ogrisel.github.io/scikit-learn.org/sklearn-tutorial/modules/generated/sklearn.cross_validation.Bootstrap.html>ref.</a>

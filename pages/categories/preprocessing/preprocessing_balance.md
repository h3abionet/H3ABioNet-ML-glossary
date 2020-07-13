---
title: Preprocessing
keywords: Preprocessing
tags: [preprocessing]
last_updated: Jul 13, 2020

toc: false
sidebar: preprocessing_sidebar
permalink: preprocessing_balance.html
folder: categories/preprocessing
author_profile: true
authors:
 - Mohammed Sabry
---

# Balanced/unbalanced datasets:
Unbalanced dataset is when the majority of observations belong to one specific class than the others, and by nature machine learning algorithms are lazy learners, they will classify every observation to that common class and obtain high accuracy easily. 
Therefore, no usefulness from a model that consumes unbalanced dataset, for example, consider a fraudulent transaction dataset where fraud transactions are minor class compare to all transactions, train a model on this dataset before pre-processing it can give a high accuracy (by classifying every observation to the major class), but overall the model fails miserably in detecting fraud transactions which is the main purpose of this model.   

Some of balancing dataset techniques:
* Undersampling: The idea is to reduce the ratio of observations between the majority and minority class, by randomly selecting observations in the desired ratio or use other methods like k-nearest neighbors algorithm(KNN) that can berserves signals which may be lost by random selection.
* Oversampling: This method populates the minority class with synthetical observations based on the available data. Some algorithms that are used for this: Variational Autoencoders (VAE), and Synthetic Minority Over-sampling Technique(SMOTE).

<img src="/figures/Unbalanced_datasets.png" width="500" height="250">

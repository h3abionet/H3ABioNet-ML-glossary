---
title: Supervised Learning
keywords: supervised learning, classification, regression
tags: [supervised_learning]
last_updated: Feb 20, 2020

toc: false
sidebar: supervised_learning_sidebar
permalink: K-Nearest-Neighbours-2-5.html
folder: categories/supervised
author_profile: true
authors:
 - Liqian_Ma
 - Amel_Ghouila
 - Shakun_Baichoo
---

## K-Nearest Neighbours 

The K-nearest neighbours stores all available cases and classifies new cases by a majority vote of its k-neighbors. The case being assigned to the class is most common amongst its K nearest neighbours measured by a distance function. This means that the algorithm takes a bunch of labelled points, and learns from them how to label other points by looking at the closest points to the new point (i.e. its nearest neighbours) and having the neighbours vote – so that the label most commonly selected for the new vote is the final label for the new point. 

## Applications

Predict gene function from heterogeneous data [ref](https://doi.org/10.1186/1471-2105-7-S1-S11).

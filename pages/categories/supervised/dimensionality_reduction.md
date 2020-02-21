---
title: Supervised Learning
keywords: supervised learning, classification, regression
tags: [supervised_learning]
last_updated: Feb 20, 2020

toc: false
sidebar: supervised_learning_sidebar
permalink: Dimensionality-Reduction-Algorithms-2-7.html
folder: categories/supervised
author_profile: true
authors:
 - Liqian Ma
 - Amel Ghouila
 - Shakun Baichoo
 - Dassen Sathan
 - Olivier S.A.
 - Christopher Fields
---

## Dimensionality Reduction Algorithms 

Feature Reduction or dimensionality reduction is a crucial step in machine learning, when a dataset contains many variables or characteristics for each individual element in the dataset, especially when comparing the number of records to the number of variables for each record.  Feature extraction involves the transformation of the raw data into new features that is the original feature space is mapped onto a new, reduced feature  space – a dataset with fewer variables that might be generated through combinations of the original variables. The new reduced space can be created either by selecting a subset of the original, adding new dimensions or selecting from both new and original dimensions. Reduction can be performed using multiple methods for filtering such as Variance, Correlation, Random Forests, Principal Component Analysis (PCA) and backward/forward feature construction or elimination (By minimising the model training error). 

## Applications

Take PCA as an example:

1. Visualize microarray gene expression data [ref](https://doi.org/10.1186/1471-2105-11-567). 
2. Discover biomarker discovery from high-throughput biological data [ref](https://doi.org/10.1093/bib/bbn005).

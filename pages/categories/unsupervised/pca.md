---
title: Introduction to unsupervised learning
keywords: unsupervised learning, clustering, dimensionality reduction
tags: [unsupervised_learning]
last_updated: Feb 28, 2020
toc: false
sidebar: unsupervised_learning_sidebar
permalink: pca.html
folder: categories/unsupervised
author_profile: true
authors:
 - Olivier Sheik Amamuddy
 - Liqian Ma
 - Amel Ghouila
 - Shakun Baichoo
 - Dassen Sathan
 - Christopher Fields
---

## Principal Components Analysis
PCA is a popular unsupervised feature reduction technique, where linear combinations of the correlated variables are created to reduce the features space. PCA decomposes the multivariate dataset into components that explain a maximum amount of the variance between datapoints, and the components are ranked in order of the explained variance. The first principal component (PC1), thus explains the most variance in the dataset. The number of PCs to be used can be determined by a cumulative frequency cutoff (e.g. the number of PCs that together explain 80% of variance). Depending on the application, the dataset may have to be normalised, as variables on the greatest scale will dominate. Not directly interpretable.

## Applications
Due to its usefulness at data reduction, PCA finds wide applications, such as:
 * the clustering and visualisation of correlated genes in gene expression studies <a href="https://www.nature.com/articles/srep25696">ref</a>, 
  * data visualisation/pre-processing in machine learning <a href="http://www.nlpca.org/pca_principal_component_analysis.html">ref</a>, 
  * and the analysis of protein dynamics <a href="https://www.sciencedirect.com/science/article/pii/S1093326314001703">ref</a>.

---
title: Introduction to unsupervised learning
keywords: unsupervised learning, clustering, dimensionality reduction
tags: [unsupervised_learning]
last_updated: Feb 28, 2020
toc: false
sidebar: unsupervised_learning_sidebar
permalink: dbscan.html
folder: categories/unsupervised
author_profile: true
authors:
 - Liqian Ma
 - Amel Ghouila
 - Shakun Baichoo
 - Dassen Sathan
 - Olivier S.A.
 - Christopher Fields
---
## DBSCAN (Density-based spatial clustering of applications with noise)
As opposed to k-means, the DBSCAN algorithm does not require a user-defined k (number of clusters). It assigns densely-connected sample points to the same cluster, putting aside the less densely regions within the data points. As such it is robust to the presence of outliers and is able to form clusters of arbitrary shape. It is however non-deterministic <a href="https://en.wikipedia.org/wiki/DBSCAN">ref</a> and its performance degrades at high dimensions <a href="https://europepmc.org/article/PMC/5135122">ref</a>.

## Applications
 * Single neuronal methylomes obtained from mice and human frontal cortices were compared using DBSCAN <a href="https://science.sciencemag.org/content/357/6351/600">ref</a>
 * Edge detection of skin lesions obtained from dermoscopic images <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3236834/">ref</a>

---
title: Introduction to unsupervised learning
keywords: unsupervised learning, clustering, dimensionality reduction
tags: [unsupervised_learning]
last_updated: Feb 28, 2020
toc: false
sidebar: unsupervised_learning_sidebar
permalink: self_organizing_map.html
folder: categories/unsupervised
author_profile: true
authors:
 - Olivier S.A.
 - Liqian Ma
 - Shakun Baichoo
 - Amel Ghouila
 - Christopher Fields
 - Dassen Sathan
---

## Self-Organizing Map (SOM) 
A data visualization technique which has been invented by Professor Teuvo Kohonen and is based on dimension reduction using self-organizing neural networks. SOM, just like PCA, is also based on dimension reduction. However SOM produces a map, typically of 2 dimensions, and plots the similarities of the data by grouping similar data items together.

## Applications
 * The SOM method was applied to whole genome expression profiles from multiple individuals and tissues to produces clusters of co-regulated genes in <a href="https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-12-306>ref</a>. It is packaged as an R package ('oposSOM').
 
 * Using a variant of the SOM algorithm, a batch-learning SOM (BLSOM) was used to classify metagenomic sequence fragments according to phylotypes using information about oligonucleotide compositions <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5029494>ref</a>.
 
 * Genomic encoding methods were investigated with two variations of the SOM algorithm (Kohonen’s SOM and the growing cell structures approach). The resulting sequence clustering was in agreement with the sampled phylogenetic relationships <a href="https://academic.oup.com/bioinformatics/article/31/5/736/2748205">ref</a>.

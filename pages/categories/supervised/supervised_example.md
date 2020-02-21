---
title: Supervised Learning
keywords: supervised learning, classification, regression
tags: [supervised_learning]
last_updated: Feb 20, 2020

toc: false
sidebar: supervised_learning_sidebar
permalink: Supervised-Learning-1-1.html
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

### An example of how supervised learning can be applied to genomics

Let’s consider the problem of splice site prediction as a supervised classification problem. The instances to be classified will be DNA sequences of a given size (for example, 22 base pairs, 10 upstream and 10 downstream the 2 bp splice site). The attributes of a given instance will be the nucleotide at each position in the sequence. In this example, we can assume that we are looking for donor sites, so the possible values for the class will be true donor site or false donor site. As we are approaching the problem as supervised classification, we need a set of labelled examples, i.e. a set of sequences of true and false donor sites along with their labels. At this point, we can use this training set to build a classifier. Once the classifier has been trained, we can use it to label new sequences, using the nucleotide present at each position as an input to the classifier and getting the assigned label (true or false donor site) as an output.

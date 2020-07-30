---
title: Semi-supervised Learning
keywords: semi-supervised learning
tags: [semi-supervised_learning]
last_updated: Jul 30, 2020

toc: false
sidebar: semi-supervised_learning_sidebar
permalink: graph_based_methods.html
folder: categories/semi-supervised
author_profile: true
authors:
 - Mohammed Sabry
---

### Graph-Based SSL:
In this method, we construct a graph, its nodes are all the data points in the dataset(labeled or unlabeled), and its edges may be representing the similarity between data points or they can represent any other prior knowledge you want to construct. After graph construction, there are many methods used to apply semi-supervised learning:
* Label Propagation:
In this method we propagate labels of the labeled data points to unlabeled data points according to the similarity between them.
* Node Embeddings:
Node embedding is to represent each node as a vector in a vector space where relationships in this space reflect the node's position in the graph and the relationship with their neighbours. Using this embedding we can train a classifier over the labeled nodes and then use it to predict unlabeled nodes.
There are many approaches to learn these node embeddings, one of them is  to use graph neural  networks.

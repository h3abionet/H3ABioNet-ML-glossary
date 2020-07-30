---
title: Semi-supervised Learning
keywords: semi-supervised learning
tags: [semi-supervised_learning]
last_updated: Mar 17, 2020

toc: false
sidebar: semi-supervised_learning_sidebar
permalink: semi-supervised_example.html
folder: categories/semi-supervised
author_profile: true
authors:
 - Zahra Mungloo-Dilmohamud
---

## Examples of the application semi-Supervised learning 
Semi-supervised learning models are becoming widely applicable in a plethora of fields <a href="https://medium.com/@jrodthoughts/understanding-semi-supervised-learning-a6437c070c87">(Rodrigues, 2017)</a>.  Below are some examples of scenarios that require intensive human intervention and where SSL techniques can make a big difference.

### 1. Medical Image Recognition and Analysis
In medical image analysis or computer-aided diagnosis (CAD), it is cheap and easy to have scanned images of the patients, however it is expensive to label them. The labeling process requires an expert such as a physician or radiologist to highlight the abnormal areas. (<a href="https://arxiv.org/abs/1706.00996">Shaaban et al, 2017</a>)
### 2. Protein Sequence Classification and Prediction
Inferring the function of proteins and  recognizing the (3D) structure or of a single protein requires months  and expert annotators. SSL techniques such as cluster kernels  (<a href="https://arxiv.org/abs/1706.00996">Shaaban et al, 2017</a>, <a href="https://papers.nips.cc/paper/2496-semi-supervised-protein-classification-using-cluster-kernels.pdf">Weston et al, 2015</a>) have proved to be successful.
### 3. Speech Recognition and Analysis
Labeling audio files is typically a very intensive task that requires a lot of human resources and applying SSL techniques can help to improve traditional speech analytic models.
### 4. Web Content Classification, Aggregation and Crawling engines
Organizing the knowledge available in billions of web pages will advance different segments of AI. Unfortunately, that task typically requires human intervention to classify and aggregate the content.


There are a few essential characteristics that should be present on a problem to be effectively solvable using SSL (<a href="https://towardsdatascience.com/supervised-learning-but-a-lot-better-semi-supervised-learning-a42dff534781">Ye, 2020<a>) . These are: 

* <strong>Sizable Unlabeled Dataset:</strong> In SSL scenarios, the seize of the unlabeled dataset should be substantially bigger than the labeled data. Otherwise, the problem can be simply addressed using supervised algorithms.
* <strong> Input-Output Proximity Symmetry:</strong> SSL operates by inferring classification for unlabeled data based on proximity with labeled data points. Inverting that reasoning, SSL scenarios entail that if two data points are part of the same cluster (determined by a K-means algo or similar) their outputs are likely to be in close proximity as well. Complementarily, if two data points are separated by a low density area, their output should not be close.
* <strong>Relatively Simple Labeling and Low-Dimension Nature of the Problem:</strong> It is important that the problem of inferring of the labeled data does not become more complicated than the original problem. Also, problems that use datasets with many dimensions or attributes are likely to become really challenging for SSL algorithms as the labeling task will become very complex.

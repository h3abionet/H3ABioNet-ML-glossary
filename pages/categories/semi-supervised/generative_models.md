---
title: Semi-supervised Learning
keywords: semi-supervised learning
tags: [semi-supervised_learning]
last_updated: Jul 30, 2020

toc: false
sidebar: semi-supervised_learning_sidebar
permalink: generative_models.html
folder: categories/generative_models
author_profile: true
authors:
 - Mohammed Sabry
---

### Generative Models:
Generative models try to understand the ground truth distribution of the input space. Semi-supervised learning with generative models can be viewed as an extension of supervised learning, classification in addition to information about the input space presented by unlabeled data. we can leverage this additional information presented by the unlabeled data to understand the distribution of the input space and hence the shape of the latent space which can help in classifying the data and generalizing to unseen data. One of the methods used is Extending variational Autoencoders, it uses three components to leverage all the information in the dataset: Encoder, classifier and Decoder. Encoder used to encode data points to their corresponding latent space, and the classifier used to classify data points and leverage the information of the labeled data, then these two outputs are used together to form a latent vector and feed it to a decoder to reconstruct the data point.

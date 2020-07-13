---
title: Preprocessing
keywords: Preprocessing
tags: [preprocessing]
last_updated: Jul 13, 2020

toc: false
sidebar: preprocessing_sidebar
permalink: preprocessing_intro.html
folder: categories/preprocessing
author_profile: true
authors:
 - Mohammed Sabry
---

# Scaling:
Some machine learning algorithms are very sensitive to distance and tuned to work well in specific ranges e.g. [-1, 1] range. For example, scaling to this range for gradient descent optimizer makes the loss surface smooth. Therefore, models tend to converge faster, and the [-1, 1] range offers the highest floating point precision. 

Some of Scaling techniques:
Min-max scaling: The minimum value that the input can take is scaled to –1 and the maximum possible value to 1:
x_scaled = $\frac{2*x - max_x - min_x}{max_x - min_x}$.
Clipping:The numeric value is linearly scaled between these two reasonable bounds, and then clipped to lie in the range [–1, 1].
Z-score normalization: scaling the input using the mean and standard deviation estimated over the training dataset:
x_scaled = $\frac{x - mean_x}/{stddev_x}$

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

# Batch Effect:
Batch effect is a technical variation which might confound the biological signal. This technical variation originates from: different dates of sequencing, people doing the sequencing, chemistry protocol, or read length. 

Some techniques to correct batch effect:
* Combat: uses the bayesian shrinkage towards the mean, this implies that for correcting each sequence(e.g. genes) we use a mean information from other sequences.

---
title: Assessment of model performance
keywords: performance example
tags: [performance_example]
last_updated: Jun 22, 2020

toc: false
sidebar: performance_sidebar
permalink: performance_example.html
folder: categories/performance
author_profile: true
authors:
 - Olivier Sheik Amamuddy
 - Liqian Ma
 - Amel Ghouila
 - Shakun Baichoo
 - Dassen Sathan
 - Christopher Fields
---

## Which performance metrics should one use?
Machine learning problems boil down to predicing discrete [eg. yes/no questions, taxonomy, levels of a factor (high, medium, low)] or continuous variables (e.g. height, weight, temperature, time). In the following paragraphs, we include some example of the machine learning applications and the metrics that were used to assess performance.

* Researchers trained several artificial neural network models to predict drug resistance in HIV for several antiretrovirals using protein sequences as features <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5558779/">ref</a>. The authors were able to show that by improving data filtering, drug resistance could be improved for the majority class (one virus subtype). The outputs were continuous variables (drug fold resistance ratios from the PhenoSense assay) and were evaluated using the coefficient of determination (R<sup>2</sup>), which is the squared correlation.
* More recently, Nagano and co-workers used ensembles of machine leaning models to predict plant fresh weight at harvest using leaf movement data obtained from regular snapshots of growing seedlings <a href="https://www.frontiersin.org/articles/10.3389/fpls.2019.00227/full">ref</a>. The model has important implications in the agricultural sector, where optimum harvest is important. The model performance was reported as a correlation.


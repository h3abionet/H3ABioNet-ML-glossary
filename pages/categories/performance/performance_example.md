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
Machine learning problems boil down to predicing discrete [eg. yes/no questions, taxonomy, levels of a factor (high, medium, low)] or continuous variables (e.g. height, weight, temperature, time). In the following paragraph, we include some example of machine learning applications and the metrics that were used to assess their performance.

* Researchers trained several artificial neural network models to predict drug resistance in HIV for several antiretrovirals using protein sequences as features <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5558779/">ref</a>. The authors were able to show that by improving data filtering, drug resistance could be improved for the majority class (one virus subtype). The outputs were continuous variables (drug fold resistance ratios from the PhenoSense assay) and were evaluated using the coefficient of determination (R<sup>2</sup>), which is the squared correlation.
* In 2019, Nagano and co-workers used ensembles of machine leaning models to predict plant fresh weight at harvest using leaf movement data obtained from regular snapshots of growing seedlings <a href="https://www.frontiersin.org/articles/10.3389/fpls.2019.00227/full">ref</a>. The model has important implications in the agricultural sector, where optimum harvest is important. The model performance was reported as a correlation.
* More recently, Stokes and co-workers discovered a novel and potent antibiotic "Halicin" using a deep learning model. The compound was shown to be active  against a wide range of pathogens, including Mycobacterium tuberculosis, carbapenem-resistant Enterobacteriaceae, Clostridioides difficile and pan-resistant Acinetobacter baumannii <a href="https://www.cell.com/cell/fulltext/S0092-8674(20)30102-1#secsectitle0030">ref</a>. The output of the model was either "inhibitory" or "not inhibitory", and thus the metric used was one of that is typically used for assessing classification models. The receiver operating characteristic curve-area underthe curve (ROC-AUC) was used to report the performance of the model.


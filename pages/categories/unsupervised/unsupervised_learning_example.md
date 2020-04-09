---
title: Introduction to unsupervised learning
keywords: unsupervised learning, clustering, dimensionality reduction
tags: [unsupervised_learning]
last_updated: Feb 28, 2020
toc: false
sidebar: unsupervised_learning_sidebar
permalink: unsupervised_learning_example.html
folder: categories/unsupervised
author_profile: true
authors:
 - Olivier S.A.
 - Liqian Ma
 - Amel Ghouila
 - Shakun Baichoo
 - Christopher Fields
 - Dassen Sathan
---

## Example
Let's take as example a set of unlabelled HIV *pol* nucleotide sequences obtained from a laboratory. By "unlabelled" in this case, we mean that we do not know the strain or possible provenance of the virus. The *pol* sequence contains several enzymes essential for the pathogens replication, and segments from it are routinely sequenced to determine the efficacy of antiretroviral treatment in HIV patients. Mutations are so numerous that the virus strains are classified into several denominations, and have drug resistance patterns associated with them, which can assist in guiding therapy. While the determination of drug resistance generally requires an alignment to a canonical reference sequence in many cases, one can additionally perform a multiple sequence alignment against previously characterized sequences and apply hierarchical clustering to estimate the relationship of the unknown sequence with known strains.

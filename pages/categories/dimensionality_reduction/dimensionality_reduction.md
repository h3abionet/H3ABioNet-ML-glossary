The curse of dimensionality has been one of the major problems in machine learning, which greatly alters the accuracy of a predictor. Dimension reduction has become an important technique for reducing these huge dimensions to improve predictive performance.
Feature selection can be used to filter uninformative features from the dataset, and will keep a subset of the original features. Some supervised algorithms have inbuilt feature selection, e.g. random forests and regularised regression (Ridge regression and Lasso regression). Other feature selection approaches include variance thresholds, correlation thresholds, genetic algorithms, stepwise search.

Feature extraction will make a new set of features from combinations of the original features. It can be unsupervised (e.g. Principal component analysis, PCA) or supervised (e.g. Linear discriminant analysis, LDA). 


| Supervised | Unsupervised |
|---|---|
| Input data is labelled | Input data is unlabelled |
| Uses training dataset | Uses just input dataset |
| Known number of classes | Unknown number of classes |
| Guided by expert (labelled data provided) | Self guided learning (using some criteria) |
| Goal: predict class or value label | Goal: analyse data, determine data structure/grouping |
| Classification and regression | Clustering, dimensionality reduction, density estimation |

---
title: Preprocessing
keywords: Preprocessing
tags: [preprocessing]
last_updated: Jul 13, 2020

toc: false
sidebar: preprocessing_example
permalink: preprocessing_example.html
folder: categories/preprocessing
author_profile: true
authors:
 - Dassen Sathan
---

## 
To illustrate the concept of feature extraction and reduction, a dataset from the Wisconsin Breast Cancer Dataset will be used and it is composed of 30 features . 

```python
from sklearn.datasets import load_breast_cancer
import pandas as pd
cancer = load_breast_cancer()
cancer_df=pd.DataFrame(cancer.data,columns=cancer.feature_names)
cancer_df.iloc[:, 2:].head(10) 
```

Using head() we can see clearly the different features such as mean perimter, mean area etc but such high dimensionality imposes difficulties for classic ML algorithms. For this reason we have to use feature extractiona nd reduction technique and a usefulmethod is the principal component analysis (PCA). The number of features has been reduced to 3 principal components that can be easily isualized using a 3D scatter plot. The cancer is either malignant (shown as red dot) or benign (shown as green star)

```python
from sklearn.decomposition import PCA
from sklearn.preprocessing import scale
from matplotlib.patches import FancyArrowPatch
from mpl_toolkits.mplot3d import proj3d
import numpy as np
import matplotlib.pyplot as plt
class Arrow3D(FancyArrowPatch):
    def __init__(self, xs, ys, zs, *args, **kwargs):
        FancyArrowPatch.__init__(self, (0,0), (0,0), *args, **kwargs)
        self._verts3d = xs, ys, zs

    def draw(self, renderer):
        xs3d, ys3d, zs3d = self._verts3d
        xs, ys, zs = proj3d.proj_transform(xs3d, ys3d, zs3d, renderer.M)
        self.set_positions((xs[0],ys[0]),(xs[1],ys[1]))
        FancyArrowPatch.draw(self, renderer)

labels=cancer.target
cdict={0:'red',1:'green'}
labl={0:'Malignant',1:'Benign'}
marker={0:'o',1:'*'}
alpha={0:.3, 1:.5}
scaled = scale(cancer_df, with_mean=True, with_std=False) 
pca_model = PCA(n_components=3)
pca= pca_model.fit_transform(scaled) 
pca_exp_mn = pca_model.explained_variance_ratio_  
max_Var=np.transpose(pca_model.components_[0:3, :]) 
pca_1, pca_2, pca_3 = pca_exp_mn[0]*100, pca_exp_mn[1]*100, pca_exp_mn[2]*100
fig = plt.figure(figsize=(15, 15))
ax = fig.add_subplot(111, projection='3d')
#ax = Axes3D(fig)
ax.xaxis.pane.fill, ax.yaxis.pane.fill, ax.zaxis.pane.fill = False, False, False
ax.set_title("PCA illustration ")
ax.legend(['Malignant', 'Benign'], fontsize=15, loc='best')
ax.set_xlabel('PC-1 : %.2f [%%]'%pca_1, fontsize=13)
ax.set_ylabel('PC-2 : %.2f [%%]'%pca_2, fontsize=13)
ax.set_zlabel('PC-3 : %.2f [%%]'%pca_3, fontsize=13)
y_M, y_B =1, 0           # Logical statement for Benign indication
xs, ys, zs = pca[:,0], pca[:,1], pca[:,2]

s_x, s_y, s_z = 1.0/(xs.max() - xs.min()), 1.0/(ys.max() - ys.min()), 1.0/(zs.max() - zs.min())
for l in np.unique(labels):
    ix=np.where(labels==l)
    ax.scatter(xs[ix],ys[ix],zs[ix],c=cdict[l],s=40,label=labl[l],marker=marker[l],alpha=alpha[l])
    n = max_Var.shape[0]
    for i in range(n):
        mean_x, mean_y, mean_z = max_Var[i,0], max_Var[i,1], max_Var[i,2]
        a = Arrow3D([mean_x,0.0], [mean_y,0.0], [mean_z,0.0], mutation_scale=15, lw=3, arrowstyle="<|-", color="r")
        ax.add_artist(a)
    
        if labels is None:
            ax.text(max_Var[i,0]* 1.15, max_Var[i,1] * 1.15, max_Var[i,2] * 1.15, "Var"+str(i+1), 
                    color = 'g', fontsize=14, ha = 'center', va = 'center')
        else:
            ax.text(max_Var[i,0]* 1.15, max_Var[i,1] * 1.15, max_Var[i,2] * 1.15, labels[i],      
                    color = 'g', fontsize=14, ha = 'center', va = 'center')
```

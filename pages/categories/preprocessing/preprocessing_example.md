---
title: Preprocessing
keywords: Preprocessing
tags: [preprocessing]
last_updated: Feb 25, 2021

toc: false
sidebar: preprocessing_sidebar
permalink: preprocessing_example.html
folder: categories/preprocessing
author_profile: true
authors:
 - Dassen Sathan
---

## Preprocessing example, using feature extraction and reduction
To illustrate the concept of feature extraction and reduction, a dataset from the Wisconsin Breast Cancer Dataset will be used and it is composed of 30 features.

```python
from sklearn.datasets import load_breast_cancer
import pandas as pd
cancer = load_breast_cancer()
cancer_df=pd.DataFrame(cancer.data,columns=cancer.feature_names)
cancer_df.iloc[:, 2:].head(10) 
```
<div class="datatable-begin"></div>
|mean perimeter|mean area|mean smoothness|mean compactness|mean concavity|mean concave points|mean symmetry|mean fractal dimension|radius error|texture error|perimeter error|area error|smoothness error|compactness error|concavity error|concave points error|symmetry error|fractal dimension error|worst radius|worst texture|worst perimeter|worst area|worst smoothness|worst compactness|worst concavity|worst concave points|worst symmetry|worst fractal dimension|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
122.8|1001.0|0.1184|0.2776|0.3001|0.1471|0.2419|0.07871|1.095|0.9053|8.589|153.4|0.006399|0.04904|0.05373|0.01587|0.03003|0.006193|25.38|17.33|184.6|2019.0|0.1622|0.6656|0.7119|0.2654|0.4601|0.1189
132.9|1326.0|0.08474|0.07864|0.0869|0.07017|0.1812|0.05667|0.5435|0.7339|3.398|74.08|0.005225|0.01308|0.0186|0.0134|0.01389|0.003532|24.99|23.41|158.8|1956.0|0.1238|0.1866|0.2416|0.186|0.275|0.08902
130.0|1203.0|0.1096|0.1599|0.1974|0.1279|0.2069|0.05999|0.7456|0.7869|4.585|94.03|0.00615|0.04006|0.03832|0.02058|0.0225|0.004571|23.57|25.53|152.5|1709.0|0.1444|0.4245|0.4504|0.243|0.3613|0.08758
77.58|386.1|0.1425|0.2839|0.2414|0.1052|0.2597|0.09744|0.4956|1.156|3.445|27.23|0.00911|0.07458|0.05661|0.01867|0.05963|0.009208|14.91|26.5|98.87|567.7|0.2098|0.8663|0.6869|0.2575|0.6638|0.173
135.1|1297.0|0.1003|0.1328|0.198|0.1043|0.1809|0.05883|0.7572|0.7813|5.438|94.44|0.01149|0.02461|0.05688|0.01885|0.01756|0.005115|22.54|16.67|152.2|1575.0|0.1374|0.205|0.4|0.1625|0.2364|0.07678
82.57|477.1|0.1278|0.17|0.1578|0.08089|0.2087|0.07613|0.3345|0.8902|2.217|27.19|0.00751|0.03345|0.03672|0.01137|0.02165|0.005082|15.47|23.75|103.4|741.6|0.1791|0.5249|0.5355|0.1741|0.3985|0.1244
119.6|1040.0|0.09463|0.109|0.1127|0.074|0.1794|0.05742|0.4467|0.7732|3.18|53.91|0.004314|0.01382|0.02254|0.01039|0.01369|0.002179|22.88|27.66|153.2|1606.0|0.1442|0.2576|0.3784|0.1932|0.3063|0.08368
90.2|577.9|0.1189|0.1645|0.09366|0.05985|0.2196|0.07451|0.5835|1.377|3.856|50.96|0.008805|0.03029|0.02488|0.01448|0.01486|0.005412|17.06|28.14|110.6|897.0|0.1654|0.3682|0.2678|0.1556|0.3196|0.1151
87.5|519.8|0.1273|0.1932|0.1859|0.09353|0.235|0.07389|0.3063|1.002|2.406|24.32|0.005731|0.03502|0.03553|0.01226|0.02143|0.003749|15.49|30.73|106.2|739.3|0.1703|0.5401|0.539|0.206|0.4378|0.1072
83.97|475.9|0.1186|0.2396|0.2273|0.08543|0.203|0.08243|0.2976|1.599|2.039|23.94|0.007149|0.07217|0.07743|0.01432|0.01789|0.01008|15.09|40.68|97.65|711.4|0.1853|1.058|1.105|0.221|0.4366|0.2075
<div class="datatable-end"></div>

Using the `head()` method we can clearly see the **28 features** corresponding to each column name of the data set (e.g. mean perimeter, mean area, etc) for first 10 biological samples. Because of limitations in hardware resources and the training efficiency of certain ML algorithms, high dimensionality may often pose difficulties due to sheer size of the dataset. For this reason we commonly have to employ feature extraction and reduction techniques. One such useful method is the principal component analysis (PCA). In the following steps the number of features is been reduced to 3 principal components that can be easily visualized using a 2D/3D scatter plot. The cancer is either malignant (shown as red dot) or benign (shown as green star)

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
![image]({{ site.baseurl }}/figures/pcafig.png)

## Interactivity console
Here is an interactive console with the loaded cancer dataset to try out:
<iframe src="https://trinket.io/embed/python3/788f9c9f54" width="100%" height="356" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>


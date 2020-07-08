# To do / Future work


### Clustering Approach
 - Preprocessing data layers should be generalized, so that the clustering step can work on any selected variables without having to hard code them into the clustering functions. Currently, the clustering step expects an explicit list of variables to cluster on (monthly median NDVI, NDVI Std., mean NDWI), which have to be restructured to fit as inputs to the clustering model. Since the monthly median NDVI data has a time dimension and the others do not, the inputs for the cluster model have to be manually restructured and put back together. Changing the inputs in the preprocessing step requires them to be restructured again to pass to the clustering model.
 - Incorporate the edge detection during the masking process. Maybe pass the edge filter to the masked imagery so that it can be more sensitive to field boundaries instead of road edges.
 - Use the clustered outputs as field objects and use object-based analysis to merge and split. Many of the clusters effectively delineate individual fields. The challenge is that depending on the number of clusters (the k value in k-means) it is very difficult to get clean outputs. Potentially, after the first crop mask is applied, the remaining pixels could be clustered again, which would better identify different crop types and thus different field boundaries.

### Edge detection
 - The `compute_edges()` function takes an edge finding algorithm as an input parameter (set to sobel edges by default), but it might not work for all edge algorithms depending on what the algorithm expects for an input. This can be generalized and reworked. The [North et al paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8584043) on finding field boundaries provides a promising generalizable approach to edge detection.  


### Data Access
 - The data is currently stored at MSI and downloaded via a batch script from the Sentinel-2 database. Currently, the only data on MSI is for the state of Minnesota from May through October 2019. 

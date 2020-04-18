# Clustering
K-means
- Initialize random centroids
- Find distance between centroids and xi
- Assign xi to clusters by min distance
- Assign centroids to midpoint of each cluster
- Repeats steps 2-4 until convergence

## Hierarchical Clustering
Agglomerative Clustering (bottom-up approach)
- Compute the proximity matrix
 | A | B | C | D
--- | --- | --- | --- | ---
A | 0 | 3 | 5 |
B | 3 | 0 | 2 |
C | | 2 | 0 |
D | | | | 0

- Let each point be a cluster
- Merge 2 closest clusters, update proximity
- Repeat step 3 until only one cluster remains 

Dendrogram:
- Distance vs Clusters

Health of this hierarchy
- The largest distance range within which there were no new splits

## Linkage Criteria
Single Linkage (min linkage)
- L(a,b) = min(D(xai,xbj))

Complete Linkage
- L(a, b) = max(D(xai,xbj))

Average Linkage
- L(a,b) = 1/(na\*nb)sum(sum((D(xai,xbj))))

Ward's Linkage
- Distance between the centroids of each cluster

## Preprocessing
Pick distance function

Pick linkage criteria

## DBSCAN
Density Based Spatial Clustering with an Application to Noise

Parameters
- Number of points there should be in each cluster
- Radius of each cluster

### HDBSCAN
Hierarchical Density Based Spatial Clustering with an Application to Noise

Parameters
- Number of points there should be in each cluster
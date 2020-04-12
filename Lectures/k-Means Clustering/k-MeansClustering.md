# Unsupervised Machine Learning
Clustering
- Group data using some pattern recognition algorithm

## k-Means Clustering
Step 0: define k
- specify how many clusters to look for in the data

Step 1: randomly intialize k centroids
- centroids = μi
- data points = xi

Step 2: find distance between each data point and each centroid

Step 3: assign cluster to data point based on minimum distance
- min ||(xi-μi)||

Step 4: find the average of each cluster
- this becomes the new centroid

Step 5: repeat steps 2-4 until the centroids obtain convergence
- position of centroids does not change after additional iterations

## Elbow-method
Method of finding optimal k

Find k value that gives a low SSE value
- Issue if k becomes too large (can make each point its own cluster => SSE = 0)

Optimal point is when SSE begins to normalize

Does not detail how accurate clusters are
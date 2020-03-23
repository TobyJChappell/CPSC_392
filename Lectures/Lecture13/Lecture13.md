# k-Nearest Neighbors
Requires training and testing data (supervised machine learning).

Comparing single closest neighbor, k=1

k=even number will select a random label if there exists a tie 
- Assuming binary classification
- Should be avoided (random selection is bad)

Given N training data points, kNN identifies k nearest neighbors of some data point c, regardless of labels
- Does not use probabilities
- Uses majority vote
- Classify based on distances from other data points

## Euclidian Distance
sqrt((x1-x2)^2+(y1-y2)^2)

sqrt(Σ((xi-x)^2))

(Σ((xi-x)^2))^(1/2)

## Minkowski Distance
(Σ(|xi-yi|^p))^(1/p)

Euclidian Distance
- p=2

Manhattan Distance
- p=1

## Cosine Distance
a\*b = ||a||\*||b||cos(θ)

cos(θ)= (a\*b)(||a||\*||b||)

Similarity between two vectors:
- cos(0) = 1 (very similar)
- cos(90) = 0 (some similarity)
- cos(180) = -1 (no similarity)

## Algorithm
Determine the value of k

For each testing data point
- Find the distance between the test point and all training points
- Sort the distances (small to large) and select the top k testing points
- Find the simple majority label from the k candidates
- This is the predicted label for test data point
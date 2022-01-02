# Validation
## k-Fold Cross Validation
Instead of splitting the data into a training and testing set and validating the model once, we repeat the process, k times

Allows us to create unique training and testing sets with each validation

Steps:
- Shuffle the data randomly
- Split the data into k groups
- For each unique group
    * Take the group as test data set
    * Combine the remaining groups as training sets
    * Fit the model on the training set and evaluate it on the test set
    * Record the evaluation score and discard the model
 
# Transformations
One of the most important assumptions when fitting a linear regression model is that there exists a linear relationship between the independent and the dependent variables

Often times the linear relationship is not clear

In that case, different transformations can be applied to the data to make the linear relationship
clearer

ŷ = b + b x 
- a unit increase in x is associated with an average of b units increase in y i01i 1
log(ŷ )= b + b x
- a unit increase in x is associated with an average of b units increase in log(y) i01i 1
log(ŷi)= b0 + b1 log(xi)
- a k-fold increase in x is associated with kb multiplicative increase in y
    * If x doubles, y changes by a multiplicative factor of 2b

## Standardization
Independent variables may correspond to different units when modeling a multiple linear regression model

Convert to z-score so that all variables are standardized

Z ~ N(0,1)
- z = (x - mean) / stdev 
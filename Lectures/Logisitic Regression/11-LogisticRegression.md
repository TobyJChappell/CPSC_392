# Logistic Regression
## Machine Learning
Supervised Learning
- Train machine using data which is already labeled with the correct answer

Unsupervised Learning
- Machine finds patters or discovers information on its own

### Supervised Learning
Regression
- Predicts a single output value using training data

Classification
- Group the output inside a class or category

## Logisitic Regression
Model the probability of an event occuring depending on the values of independent variables

Estimate the probability that an event will occur for some observations vs the probability that the event does not occur

**Predict** the effect of variables on some vinary or multiclass response

**Classify** observations by estimating the probability that na observation is in a particular category

Logistic regression is a classification model

### Example
Hours | Passed
--- | ---
1 | 0
2 | 0
4 | 0
8 | 1
9 | 1

Given a number of hours spent studying, did I pass?
- P(yi = 1 | xiθ) = θ^T(xbar)
    * Probability that a given dependent value is 1 given same x and same parameters θ
    
h(x) = σ(θ^T(xbar)) = 1/(1+e^(-θ^T(xbar)))
- σ = sigmoid/logistic function

P(yi = 1 | xiθ) = 1-h(x)
P(yi = 1 | xiθ) = h(xi)^yi(1-h(x))^(1-yi)
- Bernoulli Distribution => very good for binary classification

The entire data: x, y
- L(θ) = P(yi = 1 | xiθ) = ∏(h(xi)^yi(1-h(xi))^(1-yi)
    * L(θ) is the likelihood function for θ
    * Represents how plausible my model is given all of my data points

### Log Likelihood
- ℒ(θ) = Σ(yilog(h(xi))+(1-yi)log(1-h(x)))
- = Σ(yilog(σ(θ^T(xbar)))+(1-yi)log(1-σ(θ^T(xbar))))
- δℒ(θ)/δθ = y/(σ(θ^T(xbar)))(δσ/δθ(θ^T(xbar))) + ... + (1-yi)/(1-σ(θ^T(xbar)))(δσ/δθ(θ^T(xbar)))
    * δσ/δθ(θ^T(xbar)) = δσ(θ^T(xbar))/δσ(θ^T(xbar))\*δ(θ^T(xbar))/δθ
    * = σ(θ^T(xbar))(1-σ(θ^T(xbar)))
- δℒ(θ)/δθ = y-σ(θ^T(xbar))xbar = y-σ(h(x))xbar

θ+ = (θ-)+α(δℒ(θ)/δθ)

## Confusion Matrix
Displays predicted values vs. actual values
- True Positive: Predicted positive and was positive
- True Negative: Predicted negative and was negative
- False Positive: Predicted positive and was negative
- False Negative: Predicted negative and was positive

### Confusion Matrix (Measures)
Recall = TP/(TP+FN)
- Out of all the positive classes, how much we predicted correctly (should be as high as possible)

Precision = TP/(TP + FP)
- Out of all the positive classes we have predicted correctly, how many are actually positive

Acuracy = (TP+TN)/Total
- Out of all classes, how much did we predict correctly

## Assumptions
There is minimal or no mutlicollinearity between independent variables

Independent variables are linearly related to the log of odds of the dependent variable
- y = 1/(1+e^(-x))

Requires a large sample size to predict properly

Observations are independent of each other
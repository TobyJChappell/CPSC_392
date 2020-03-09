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

### Logisitic Regression
Model the probability of an event occuring depending on the values of independent variables

Estimate the probability that an event will occur for some observations vs the probability that the event does not occur

**Predict** the effect of variables on some vinary or multiclass response

**Classify** observations by estimating the probability that na observation is in a particular category

Logistic regression is a classification model

#### Example
Hours | Passed
--- | ---
1 | 0
2 | 0
4 | 0
8 | 1
9 | 1

Given a number of hours spent studying, did I pass?
- P(yi = 1 | xiθ) = θ^T(xbar)
 - Probability that a given dependent value is 1 given same x and same parameters θ
h(x) = σ(θ^T(xbar)) = 1/(1+e^(-θ^T(xbar)))
- σ = sigmoid function


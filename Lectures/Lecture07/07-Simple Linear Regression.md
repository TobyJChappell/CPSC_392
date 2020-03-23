# Simple Linear Regression

## Dataset 1

You have randomly selected 5 tests from a pool of tests and want to see if you can predict the test score using only this data.

Number | Score
--- | ---
1 | 7
2 | 10
3 | 6
4 | 4
5 | 8

### Model
Mean = (7+10+6+4+8)/5 = 7

Can plot Score vs. Number and draw score = mean for regression line

### Residual/Error
Distance between the best fit line to the observed values.

Number | Residual | Residual^2
--- | --- | ---
1 | 0 | 0
2 | 3 | 9
3 | -1 | 1
4 | -3 | 9
5 | 1 | 1

SSE = Sum of Squared Errors = Sum(Residual^2) = 20

Goal is to create linear model to minimize the SSE.

## Dataset 2
The SSE of the model with just test scores is 20. Let’s introduce a new independent variable, total hours of study, and see if we can create a linear regression model using this attribute

Number | Hours of Study | Score
--- | --- | ---
1 | 3 | 7
2 | 7 | 10
3 | 4 | 6
4 | 1 | 4
5 | 5 | 8

### Lines
Equation of a Line
y = mx+b
- m = slope (rise/run)
- b = y-intercept (point where x = 0)

Simple Linear Regression Line
E(y) = β0+β1x
- β1 = slope parameter
- β2 = y-intercept parameter
- E(y) = mean or expected value of y, given some x

Linear Regression for a Sample
ŷ = b0+b1x
- ŷ (y-hat) = estimator of E(y)
- b1 = sum((xi-xbar)(yi-ybar))/sum(xi-xbar)^2
- b0 = ybar - b1(xbar)

### Model

xbar = 4
ybar = 7

x | y | xi-xbar | yi-ybar | (xi-xbar)(yi-ybar) | (xi-xbar)^2
--- | --- | --- | --- | --- | ---
3 | 7 | -1 | 0 | 0 | 1
7 | 10 | 3 | 3 | 9 | 9
4 | 6 | 0 | -1 | 0 | 0
1 | 4 | -3 | -3 | 9 | 9
5 | 8 | 1 | 1 | 1 | 1

sum((xi-xbar)(yi-ybar)) = 19
sum((xi-xbar)^2) = 20

b1 = 19/20 = 0.95
b0 = 7 - 0.95(4) = 3.2

y-hat = 3.2+0.95xi

### Least Square Criterion
min(sum(yi-yhat)^2)
- y = observed value of test score i
- yhat = predicted value of test score
 
Goal is to minimize the sum of the squared differences between the actual value of dependent variable and the estimated (predicted) value

yi | yhat | (yi-yhat)^2
--- | --- | ---
7 | 6.05 | (7-6.05)^2
10 | 9.85 | (10-9.85)^2
6 | 7 | (6-7)^2
4 | 4.15 | (4-4.15)^2
8 | 7.95 | (8-7.95)^2

sum(yi-yhat)^2 = 1.95

### SSR & SST
SST = Sum of Squared Total
- Equals SSE when no independent variable used in the model

SSR = Sum of Squared Regression
- SSR = SST - SSE

SSR = 20 - 1.95 = 18.05

### Coefficient of Determination
r^2 = SSR/SST

r^2 = 18.05/20 = 0.9025 = 90.25%

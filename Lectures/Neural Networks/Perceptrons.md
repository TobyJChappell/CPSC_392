# Perceptrons
1. Input shape = deconstruct into small segments
2. Larger segment
3. Orientation
4. Classify

Don't rely just on the inputs => need to have weights as well

## Neural Network
Find dot products of inputs/weights and pass it to a step function

Inputs: x0, x1, ... , xn = X
- x0 is always 1, called "bias"

Weights: w0, w1, ..., wn = W^T

Output Function: output(x) = 
- 1 if ∑wi\*xi > 0
- -1 if ∑wi\*xi < 0

Can use neural network fo single perceptron to solve problem if problem is linearly separable

## Learning Weights Using an Algorithm
Minimize error

P: output of a perceptron

t: truth value we want

Error: t-P

Rule:
1. Initialize all weights randomly
2. Iterate through data: ∆wi = λ(t-P)\*xi
    - λ = learning rate
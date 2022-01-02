# Naive Bayes
## Marginal Probability
- P(outlook = sunny) = 5/14 = 0.357
- P(outlook = overcast) = 4/14 = 0.286
- P(outlook = rainy) = 5/14 = 0.357

0 <= P(attribute) <= 1

ΣP(attribute) = 1

Normal Distribution
- P(x) = 1/(sqrt(2πσ^2))\*e^(-1/2\*(((x-μ)^2)/σ^2))

## Joint Probability
P(A, B) => "probability of both A and B"

| High | Normal
-- | -- | --
Sunny | 3/14 | 2/14
Overcast | 2/14 | 2/14
Rainy | 2/14 | 3/14

P(outlook = sunny, humidity = high) = 3/14

ΣP(row/column) = marginal probability

## Conditional Probability
P(A | B) => "probability of A given B"

P(A | B) = P(A, B)/P(B)

P(outlook = sunny | humidity = high) = P(sunny, high)/P(high) = (3/14)/(7/14) = 0.429

## Bayes Rule
P(B | A) = P(B, A)/P(A) = P(A, B)/P(A)

P(A | B) = P(A, B)/P(B)

P(A, B) = P(A | B)\*P(B)

P(B | A) = (P(A | B)\*P(B))/P(A)

Independence
- P(A, B) = P(A)\*P(B)
- P(A, B | C) = P(A | C)\*P(B | C)

P(play tennis | sunny) = P(sunny | play tennis)\*P(play tennis)/P(sunny)

P(class | data) = P(data | class)\*P(class)/P(data)
- P(data | class) = likelihood
- P(class) = prior
- P(data) = evidence

P(class | data) =~ P(data | class)\*P(class)
- Ignore evidence

P(sunny, true, high | play tennis) =~ P(sunny | play)\*P(true | play)\*P(high | play)\*P(play)

## Navie Bayes
Attributes: A= A1, A2, ... , An

Target Class: C

If we assume all Ai are conditionally independent, given C, we can create a Naive Bayes classifier:

P(class | A) =~ P(A | class)\*P(class) = P(class)\*Π(P(Ai | class))
- = log(P(class))+Σ(log(P(Ai | class))

### Example
Question: Will I play tennis if outlook is overcast?

P(yes | overcast) = P(overcast | yes)\*P(yes)/P(overcast) = 1.00
- P(overcast) = 4/14 = 0.29
- P(yes) = 9/14 = 0.64
- P(overcast | yes) = 4/9 = 0.44

Probability that I will play tennis given that the outlook was overcast is 1.00

P(no | overcast) = P(overcast | no)\*P(no)/P(overcast) = 1.00
- P(overcast) = 4/14 = 0.29
- P(no) = 5/14 = 0.36
- P(overcast | no) = 0/5 = 0

1.00 > 0, so use P(yes | overcast)

Evidence is just a normalizing factor, so we can remove it.

P(class | data) = P(data | class)\*P(class)

### Example
Will I play tennis if outlook = overcast and temp = mild?

P(yes | overcast, mild) = P(overcast, mild | yes)\*P(yes)

P(no | overcast, mild) = P(overcast, mild | no)\*P(no)

There exists a dependence between outlook and temperature.
- P(A, B | C) = P(A | B, C)\*P(B | C)

P(overcast, mild | yes) = P(overcast | mild, yes)\*P(mild | yes)\*P(yes)
- Requires us to compute multiple probabilities that can end up being really small

Naive Bayes assumes there is indepence between attributes even if dependence exists
- P(overcast, mild | yes) = P(overcast | yes)\*P(mild | yes)\*P(yes)
- P(overcast, mild | no) = P(overcast | no)\*P(mild | no)\*P(no)

P(overcast, mild | yes) = 0.12
- P(overcast | yes) = 4/9 = 0.44
- P(mild | yes) = 4/9 = 0.44
- P(yes) = 9/14 = 0.64

P(overcast, mild | no) = 0
- P(overcast | no) = 0/9 = 0
- P(mild | no) = 2/5 = 0.4
- P(no) = 5/14 = 0.36

0.12 > 0 => P(overcast, mild | yes)
# Probability

## Multiplication Rule of Probability

* For indenpendent events, $P(A \cap B) = P(A)P(B)$.
* For dependent events, $P(A \cap B) = P(B)P(A|B)$.

## Conditional Probability

### 1. Bayes' rule
- The conditional probability of event A given event B is given by

$$P(A|B)=\frac{P(B|A)P(A)}{P(B)}$$

- If $P(A|B)=P(A)$, then A and B are independent, since knowing about B tells nothing about the probability of A having also occurred.

- If $P(A \cap B|C) = P(A|C)P(B|C)$, A and B are conditionally independent given the occurrence of C.

### 2. Law of total probability
- Given several disjoint events with B having occurred, the probability of an event A having also occurred can be broken down with
$$P(A) = P(A|B_1)P(B_1)+...+P(A|B_n)P(B_n)$$

## Probability Distributions

### Binomial distribution

* The *binomial distribution* is the discrete probability distribution of the number of successes in a sequence of $n$ independent experiments, each asking a yes-no question, and each with its own boolean value outcome: success (with probability $ = p$) or failure (with probability $ = 1 - p$).
* For a single trial / experiment, the binomial distribution is a Bernoulli distribution.
* The *binomial distribution* gives the probability of $k$ number of successes in $n$ independent trials, where each trial has probability of $p$ of success. Its probability mass function (PMF) is given by

$$P(X = k) = \binom{n}{k}p^k(1 - p)^{n - k}$$
* The mean and variance are: $\mu = np$, $\sigma^2 = np(1-p)$.

## References
* [Ace the Data Science Interview book](https://www.acethedatascienceinterview.com/)
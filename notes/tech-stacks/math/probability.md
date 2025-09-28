# Probability

## Multiplication Rule of Probability

* For indenpendent events, $P(A \cap B) = P(A)P(B)$.
* For dependent events, $P(A \cap B) = P(B)P(A|B)$.

## Probability Distributions

### Binomial distribution

* The *binomial distribution* is the discrete probability distribution of the number of successes in a sequence of $n$ independent experiments, each asking a yes-no question, and each with its own boolean value outcome: success (with probability $ = p$) or failure (with probability $ = 1 - p$).
* For a single trial / experiment, the binomial distribution is a Bernoulli distribution.
* The *binomial distribution* gives the probability of $k$ number of successes in $n$ independent trials, where each trial has probability of $p$ of success. Its probability mass function (PMF) is given by

$$P(X = k) = \binom{n}{k}p^k(1 - p)^{n - k}$$
* The mean and variance are: $\mu = np$, $\sigma^2 = np(1-p)$.

## References
* [Ace the Data Science Interview book](https://www.acethedatascienceinterview.com/)
---
layout: page
title: Conditional Probability
permalink: /notes/probability/conditional-probability/
---

## Bayes' rule
- The conditional probability of event A given event B is given by

$$P(A|B)=\frac{P(B|A)P(A)}{P(B)}$$

- If $P(A \| B)=P(A)$, then A and B are independent, since knowing about B tells nothing about the probability of A having also occurred.

- If $P(A \cap B \| C) = P(A\|C)P(B\|C)$, A and B are conditionally independent given the occurrence of C.

## Law of total probability
- Given several disjoint events with B having occurred, the probability of an event A having also occurred can be broken down with
$$P(A) = P(A|B_1)P(B_1)+...+P(A|B_n)P(B_n)$$
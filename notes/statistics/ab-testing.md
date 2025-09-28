---
layout: page
title: A/B Testing
permalink: /notes/statistics/ab-testing/
---

A/B testing is a randomized control experiment to determine whether a new feature brings improvement to the product according to a chosen success metric.

A standard A/B test is usually conducted with the following standard procedures.

1. Formulate a hypothesis
2. Setting a success metric
3. Create test groups
4. Calculate sample sizing
5. Launch test & collect data
6. Conduct analysis
7. Check for statistical significance
8. Present findings

## Propose success metrics
Success metrics can be proposed using the AARRR Pirate Metrics framework.
* **User acquisition metrics** try to capture how people are finding and trying out your product.
* **User activation metrics** refer to the point at which a user has successfully onboarded and reached the spot where they experience the core value of the product.
* **User retention metrics** aims to measure whether or not users keep coming back to a product or service over a prolonged period of time.
* **User referal metrics** aims to measure whether users share the product with others. In practice, users typically invite others only after having been activated, engaged, and retained on the product for a while.
* **User revenue metrics** aims to measure how users are willing to pay for the product or service.
![AARRR Framework](/images/notes/statistics/ab-testing/aarrr-framework.jpg)

## Decide on sample size
Power analysis is typically used to determine what sample size will ensure a high probability that we correctly reject the null hypothesis.

The following parameters are required for deciding the sample size.

* Alpha value ($\alpha$): the probability of rejecting the null hypothesis when it is true, i.e. $P(\text{reject null} \mid \text{null true})$. It is also known as the critical value.
* Power ($1-\beta$): the probability of finding a statistical difference between the groups in A/B test when a difference is actually present, i.e. $P(\text{reject null} \mid \text{null false})$. It is usually set at 0.8 by convention.
* Minimum detectable effect (MDE): the smallest effect that will be detected $(1-\beta)\%$ of the time. This is usually decided by consulting the stakeholder.

## Test Statistics

Test statistics are used for determining whether the null hypothesis or the alternative hypothesis should be accepted as correct, or whether there are significant differences between the means of two groups in the context of A/B testing.

### Z-Test
* Assumption: the test statistic follows a normal distribution under the null hypothesis.
* Use case: generally used when the sample size is large (to invoke CLT) or when the population variance is known.
* Derivation of the Z-test formula:

$$Z = \frac{\overline{X} - \mu_{\overline{X}}}{\sigma_{\overline{X}}}$$

where $\sigma_{\overline{X}}$ is the sample standard deviation.

If CLT holds:

$$\sigma_{\overline{X}} = \frac{\sigma}{\sqrt{n}}$$

Hence:

$$Z = \frac{\overline{X} - \mu_{\overline{X}}}{\frac{\sigma}{\sqrt{n}}}$$

With a large sample size (n > 30):

$$Z \approx \frac{\overline{X} - \mu_{\overline{X}}}{\frac{s}{\sqrt{n}}}$$

where $s$ is the sample standard deviation.

### t-Test
* Assumption: the test statistic follows a student's t-distribution under the null hypothesis.
* Use case: used when the sample size is small and when the population variance is unknown.
* The t-test is formulated as

$$t = \frac{\overline{X} - \mu_{\overline{X}}}{\frac{s}{\sqrt{n}}} \sim t_{n-1} \text{ where } s^2 = \frac{\sum_{i=1}^{n}(x_i-\overline{x})^2}{n-1}$$

* The t-test is parametrized by the degrees of freedom, which refers to the number of independent observations in a dataset, denoted above by ${n - 1}$.
* 3 types of t-test:
    * Independent t-test: compare means of 2 groups
    * Pair-sample t-test: compare mean of 1 group before and after treatment
    * One-sample t-test: compare mean to a specific value

### Chi-squared Test

Chi-squared test is commonly used to check the independence of two categorical variables, and assess the goodness of fit of a model. The test is formulated as:

$$\chi^2 = \sum_{i}\frac{(O_i - E_i)^2}{E_i}$$

A chi-squared test is typically performed with the following steps.

* Define the null hypothesis and alternative hypothesis. The null hypothesis assumes that there is no relationship between the two variables being tested, while the alternative hypothesis assumes that there is a relationship.
* Calculate the expected frequencies for each category. This involves multiplying the total number of observations by the probability of each category, based on the null hypothesis.
* Calculate the Chi-Squared test statistic using the formula.
* Determine the degrees of freedom, which is the number of categories minus 1.
* Use a Chi-Squared distribution table or a statistical software package to determine the p-value associated with the calculated test statistic and degrees of freedom.
* Compare the p-value to the significance level (α) to determine whether to reject or fail to reject the null hypothesis.

If the p-value is less than the significance level, we reject the null hypothesis and conclude that there is a significant relationship between the two variables being tested. If the p-value is greater than the significance level, we fail to reject the null hypothesis and conclude that there is no significant relationship between the two variables.

## References
* [Sample Size Calculator](https://www.evanmiller.org/ab-testing/sample-size.html)
* [The art of A/B testing](https://medium.com/towards-data-science/the-art-of-a-b-testing-5a10c9bb70a4)
* [Understanding the Chi-Square Test: An Introduction to Its Concept and Applications](https://medium.com/@anishnama20/understanding-the-chi-square-test-an-introduction-to-its-concept-and-applications-9c9009ddb38)
* [Ace the Data Science Interview book](https://www.acethedatascienceinterview.com/)
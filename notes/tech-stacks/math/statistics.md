# Statistics

## Core statistics concepts

### Population variance vs. sample variance

* The difference between population variance and sample variance arises from the use of $n-1$ instead of $n$ in the denominator of the formula.
* [Bessel's correction](https://en.wikipedia.org/wiki/Bessel%27s_correction) is applied to address the bias in the estimation of the population variance.

### Law of Large Numbers (LLN)
The LLN states that *if you sample a random variable independently a large number of times, the measured average value should converge to the random variable's true expectation*.

$$\overline{X}_n=\frac{X_1+X_2+...+X_n}{n} \rightarrow \mu \text{, as n} \rightarrow \infty$$


### Central Limit Theorem (CLT)
The CLT states that *if you repeatedly sample a random variable a large number of times, the distribution of the sample mean will approach a normal distribution regardless of the initial distribution of the random variable*.

Note that the **sampling distribution** describes the distribution of a sample statistic (e.g. sample mean) over many samples from the same population.

The CLT holds when the sample size is sufficiently large ($n > 30$). The sample size requirement here applies to all the samples in the sampling distribution. As the sample size increases

* the sampling distribution will converge to a normal distribution.
* the mean of the samling distribution will converge to the population mean.
* the sample standard deviation ($\frac{\sigma}{\sqrt{n}}$) will become smaller.

Many statistical practices including hypothesis testing, confidence intervals are based on the normality assumption. The use of appropriate sample size and the Central Limit Theorem helps us to get around the problem of non-normality in the data.


### z-score
Under the concept of normal distribution, z-score represents *the number of standard deviation a point is from the mean*.

$$Z = \frac{X-\mu}{\sigma}$$

### p-value
* P-value represents *the probability of observing results at least as extreme as those measured when the null hypothesis is true*.
* The p-value is usually assessed relative to some pre-determined level of significance (0.05 is often chosen).

### Confidence intervals

* Confidence intervals provide a range of values, if a large sample were taken, would contain the parameter value of interest $(1 - \alpha)\%$ of the time, where $\alpha$ is the significance level, and $(1 - \alpha)\%$ is the **confidence level**.
* E.g. a 95% confidence interval would contain the true value 95% of the time.
* The general formula for all confidence intervals is

$$\text{Point Estimate } \pm \text{(Critical Value)(Standard Error)}$$

* With the population variance given, the two sided $100(1 - \alpha)\%$ CI for population mean can be calculated by

$$\overline{X} \pm Z_{\alpha / 2}\frac{\sigma}{\sqrt{n}}$$

* In the example with the A/B testing on conversion rates, since the event of conversion follows a binomial distribution, population variance is given by $\sigma^2 = np(1 - p)$. Then the confidence interval is

$$\hat{p} \pm z_{\alpha / 2}\sqrt{\frac{\hat{p}(1 - \hat{p})}{n}}$$

### Type I and II errors

* **type I error**: the probability of rejecting the null hypothesis when it is correct, also known as "false positive". Denoted as $\alpha$.
* **type II error**: the probability of failing to reject the null hypothesis when it is incorrect, also known as "false negative". Denoted as $\beta$.

## References
* [Statistical Significance Explained](https://towardsdatascience.com/statistical-significance-hypothesis-testing-the-normal-curve-and-p-values-93274fa32687)
* [7 Most Asked Questions on Central Limit Theorem](https://towardsdatascience.com/7-most-asked-questions-on-central-limit-theorem-82e95eb7d964)
* [Ace the Data Science Interview book](https://www.acethedatascienceinterview.com/)
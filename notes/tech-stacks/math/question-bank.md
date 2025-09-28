# Linear Algebra

### Why is linear algebra important in machine learning?
- Linear algebra is foundational to machine learning because many ML algorithms, including deep learning, rely on vector and matrix operations.
- Linear algebra also helps in data compression and efficient computation.

### What is an eigenvector, and why are they important?
- Eigenvectors are vectors that only scale and don't change direction during a transformation.
- Eigenvalues are the scalars associated with this transformation.
- They are important in PCA, spectral clustering, and other ML algorithms.


# Statistics

### You have two methods for assigning drivers/driving revenue. Method A has BCR of 0.5 and Method B has BCR of 0.3 / Method A generates $1 per user and Method B generates $0.8 per user. How do you ensure method A is truly better than method B?
- Knows how to set up A/B statistical tests from concrete business problems.
- Knows which statistical tests to perform based on the problem.
- Knows how to do hypothesis testing. E.g. Chi2 test for BCR / t-test or z-test for revenue.

### Explain some differences between frequentist and bayesian statistics. What are some of the practical implications of these differences in data science?
- Understands and can explain different approaches at a high level (hypothesis testing, belief distributions) and some common drawbacks (p-hacking, computational requirements)

### What is Bayes' theorem and how is it useful in machine learning?
- Bayes' theorem describes the probability of an event, based on prior knowledge of conditions that might be related to the event. It's used in ML for probabilistic models like Naive Bayes, Bayesian networks, etc.

### What is the difference between Type I and Type II error?
- Type I error is the false positive rate, where we reject a true null hypothesis.
- Type II error is a false negative, where we accept a false null hypothesis.

### What does p-values represent? If an experiment shows that p-value is 0.06, what is your recommendation? How would you ensure your experiment has sufficient statistical power?
- Understands importance of sample size and effect magnitude and can translate this to given context. Is cognizant of p-value hacking and proper intepretation of p-values within the context of decision making.
- The p-value is the probability under the null hypothesis of obtaining a result equal to or more extreme than what was actually observed. If a p-value is 0.06, it means there's a 6% chance of observing a result at least as extreme given that the null hypothesis is true.

### What statistical tests do you know and when to use them?
- T-test: compare averages between two groups
- Chi-square test: for categorical data
- ANOVA (Analysis of Variance): to determine difference in means for > 2 groups
- Mann-Whitney U test and Wilcoxon signed-rank test: non-parametric alternative to t test
- Kruskal-Wallis test: non-parametric alternative to ANOVA
- Other non parametric methods includes: bootstrapping, permutation tests...etc

### Your manager is concerned that cash bookings have much higher driver acceptance rates than go-pay bookings and asks you to dig deeper. What hypotheses would you test and how?
- Assuming the acceptance rates are normally distributed, we could use a t-test to test the hypothesis if we have two independent groups of bookings (cash vs. go-pay).
- If we have paired samples, for instance, the same drivers accepting both cash and go-pay bookings, a paired t-test would be appropriate.
- Recognises correlation does not necessarily imply causation (e.g. cities with low go-pay penetration might have higher acceptance rates).

### Describe how you would use A/B testing in an experiment design.
- An A/B test is an experiment where two versions (A and B) are compared, which are identical except for one variation that might impact a user's behavior.
- The answer should include setting up the experiment, selecting the target audience, determining the key metric, and statistical analysis of the result.
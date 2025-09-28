# ML Concepts

### Pick 1 supervised learning algorithm that you are comfortable with and explain how it works. What are the important hyperparameters to tune, and what is the expected outcome?
- Familiarity with common ML algorithms and their usage within applied data science use cases.

### What are the uses of train, validation, and test sets - and how would you recommend splitting these datasets? What is the role of these datasets when tuning model hyperparameters?
- Is mindful of overfitting and common techniques to address overfitting. Understands the rationale behind these techniques.

### If your data have a time dimension, how would you split your datasets?
- Understands that random splitting cannot be applied in this context. Must define test set based on most recent dates and train set on prior dates.

### What metrics do you use to measure performance of regression, classification, clustering?
- For regression models, common metrics include Mean Squared Error (MSE), Mean Absolute Error (MAE), and R-squared.
- For classification models, usually look at Accuracy, Precision, Recall, F1-Score, and AUC-ROC.
- For clustering, Silhouette Score, Davies-Bouldin index, and Distortion (sum of squared distances to cluster centers) are often used.

### What is the bias-variance tradeoff? What are some common ways to identify and reduce bias and variance? (Try to relate this to the algorithm that they discussed earlier)
- Understands problem of overfitting and the appropriate hyperparameters to tune in common ML algorithms.
- Overfitting happens when a model learns the detail and noise in the training data to the extent that it negatively impacts the performance of the model on new data.
- Underfitting refers to a model that can neither model the training data nor generalize to new data.

### Suppose a classification model has an AUC score of 0.99. It feels too good to be true. How would you investigate further?
- Can relate to feeling of scepticism and suggests potential pitfalls that might falsely exagerate model performance eg. target leak, imbalance datasets etc.

### Describe some common encoding techniques for categorical data. What about timestamp data?
- Suggests alternative encodings, understands that the pros and cons and how this might depend on the problem domain and model algorithm.
- Is OHE the only way? For NN, OHE is fine. If tree based algorithms, ask why OHE may not be ideal (e.g. RF, boosted trees may subsample the columns and if cardinality is huge, you are adding on to curse of dimensionality and potentially the numerical features being overwhelmed)

### How does causal inference differ from classical ML and what are some common techniques for causal inference used by data scientists?
- Classical ML is often concerned with prediction, but causal inference seeks to understand the cause-and-effect relationship between variables. It's about asking 'what if' questions.
- Common techniques for causal inference include randomized controlled trials, natural experiments, difference-in-differences, instrumental variables, regression discontinuity, and propensity score matching.

### How would you handle missing or corrupted data in a dataset?
- Approaches may include: Deleting Rows/Columns, Replacing with Mean/Median/Mode, Predicting the Missing Values, Assigning a Unique Category to Missing Values.

### What are some of the parameters that should be considered when using {any ML algorithms} and how the parameter affects the training?
- If a candidate mentions any specific algorithms, check what are the parameters that was considered when using such algorithm. E.g. learning rate, number of rounds, depth, colsubsample, rowsubsample, min child weight etc.
- Check if the candidate had given thoughts about model selection process. Things to consider should account for complexity vs simplicity when it comes to deployment.
- If a candidate chooses neural networks (esp for tabular problems) - the reasoning should be solid, else check with the candidate why no other forms of algorithms that may give better results.
- Candidate's knowledge on model interpretation methods, including model agnostic methods: SHAP, LIME...etc and if candidate mentions, have the candidate talk about how it is calculated, knows that SHAP is instance level computation.

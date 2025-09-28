# Case Study Topics

- Context: spend 5-10 minutes explaining the context.
- Keep it deliberately vague so the candidate is forced to ask questions and translate business requirements as required.
- Candidate is expected to understand the business problem and design suitable solution to improve the user experience.

## Marketplace
A PM on the matchmaking team would like to improve driver allocation.

## Cartography

- A PM on the routing team would like to improve ETA prediction. Many of ride hailing / delivery services require accurate ETA prediction as well as to prove good customer experiences. You may state any form of assumption. Try to be as technical as possible.
- As part of the user experience improvement, we want to minimise the pickup locations distance error. We ran an analysis and realised that pickup points that average PDE > 100m. You have a team of one analyst and one DS. How would you go about the problem.

# Questions

## Problem framing

### What non-ML approaches could be used to address this problem?
Ability to see that ML has to be compared to a smart-ish baseline.

### What are some reasons you may want to start with a non-ML approach first?
Understands the complexity of deploying ML systems and the virtue of deploying non-ML solutions first to verify infrastructure works as expected.

### What ML approaches could be used to address the problem? What other models might you use? What choice of objective function or other parameters (depending on the model candidate decided) needs to be used
- Ability to cast the problem as a relevant machine learning problem (e.g. classification, regression, appropriate unsupervised learning problem).
- Ability to understand trade-offs of various loss functions.

## Performance evaluation

### What business metrics would you want to track? Which would the northstar? Why?
Ability to identify suitable metrics that describe business concerns.

### How would you validate your model? What offline evaluation metrics would you measure? How would you explain the metric to business stakeholders?
- Ability to create sensible validation scheme.
- Ability to select appropriate metric that balances between closeness to loss function and interpretability.
- Ability to explain their choice of metrics (e.g. MSE, MAE, AUC...etc) to non-technical stakeholders.

### How do you deal with overfitting?
Ability to identify drawbacks associated with various modelling choices and the relevant mitigation strategies.

### How do you deal with concept drift?
Shows understanding that ML model might experience drift, and give reasonable suggestion to mitigate or suggests ways to monitor.

## Modelling intuition

### You optimise your model, and observe that offline metrics have improved. However, online metrics have not. How do you diagnose the issue?
Ability to reason about scenarios where offline evaluation metrics may not correlate with online business metrics.

### What are some features you think that could be important? How would you implement these features, what kind of data do you need?
Ability to describe the type of features (e.g. driver, temporal, spatial) they would explore given more time, and why

### For your models, would you spend more time thinking about customer or driver features?
Ability to reason effectively about other potential features and say why they did not use them here

## Stakeholder management

### Your PM is hesitant to rollout your new model because of uncertainty over the impact on UX. How do you go about convincing your PM to proceed?
Ability to emphasize with business constraints and propose suitable risk management strategies.

### Your PM is worried because the deployment of your model has resulted in increased customer complaints. How would you investigate this?
Ability to foresee other business exigencies reasonably and provide reasonable suggestions on how to proceed.

## Communication

- Ability to be understood in English (non-native fine; however, we are a primarily English-speaking team)
- Ability to communicate concisely: no beating around the bush, ideas are communicated with little excess information or distracting ideas
- Ability to communicate concepts clearly: we can understand the statistical or ML ideas that they are presenting without having to fill in any of the gaps on their behalf
- Ability to respond to questions intelligently: either proper follow up questions are asked, or the question is answered

## Reflection

### What parallels do you see between this problem and your previous projects?
Ability to break down a DS project into common workflows, e.g. data processing, model training, model evaluation, incremental model improvement, model deployment, backtesting, AB testing, etc.

### What are your learning priorities for the year?
Aware of their current skills gaps. Motivated to learn.

## Generic

### How would you design a forecasting system to predict user traffic?
- The candidate should be able to discuss the steps involved in designing a forecasting system, which might include data collection, feature extraction, model selection, model training and evaluation, as well as model deployment and monitoring.
- They should also mention the importance of accounting for seasonality and trends in the data, and the possibility of using time series models such as ARIMA or LSTM, or ensemble forecasting methods.

### How would you build a recommendation system for e-commerce website?
- Look for an understanding of recommendation system approaches like collaborative filtering, content-based filtering, or hybrid models.
- The candidate should also discuss how they would handle challenges like cold start problem, and how they would measure the success of the system.

### How would you design an anomaly detection system to detect credit card fraud?
- The candidate should talk about supervised and unsupervised approaches to anomaly detection, the importance of dealing with imbalanced datasets in fraud detection, and the use of appropriate evaluation metrics like AUC-ROC or precision-recall.
- They should also consider real-time processing needs and how to handle false positives and negatives.

### How would you design a model to predict churn for a subscription service?
- The candidate should discuss feature engineering (e.g. usage patterns, customer complaints, changes in user behavior), appropriate machine learning models (like logistic regression, decision trees, or SVM), and relevant evaluation metrics (like precision, recall, or AUC-ROC).
- They should also consider how the model's outputs would be used to design interventions to prevent churn.

### How would you develop a machine learning model to personalize user experience on a website?
- Look for a discussion of techniques like multi-armed bandits or reinforcement learning, which can adapt over time.
- The candidate should also mention the importance of balancing exploration (trying new things) with exploitation (sticking with what works), and how they would measure the success of personalization.

### How would you design a system to classify customer support tickets?
- The candidate should discuss natural language processing techniques, such as bag-of-words, TF-IDF, or word embeddings, and classification models like logistic regression, SVM, or neural networks.
- They should also mention the importance of preprocessing text data and dealing with issues like class imbalance.

### How would you build a model to predict stock prices?
- Look for a discussion of the difficulty and unpredictability of financial markets, and the use of time series analysis or LSTM models.
- The candidate should also mention the importance of feature engineering (including potentially using external data), and the need for careful evaluation to avoid overfitting.

### How would you design a machine learning system to optimize delivery routes for a logistic company?
- The candidate should discuss the use of optimization techniques or reinforcement learning, the need to handle constraints (like delivery windows and vehicle capacity), and the importance of feature engineering (like traffic, weather, or time of day).
- They should also consider how they would measure success and improve the model over time.

### We want to forecast demand in the next 30min, in precise geographical zones, say within Jakarta. How would you go with that?
- What ML model? Can the candidate explain in layman terms how the model works?
- How do you measure success of your implementation?
- How would you explain to stakeholders the effectiveness of your solution and why it works?
- Your stakeholders have a competing solution that performs better according to them, what is your response?
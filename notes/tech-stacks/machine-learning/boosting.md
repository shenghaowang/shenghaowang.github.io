#machine-learning

The general idea of boosting is to train a series of decisions in a sequential manner. Each tree is trained with the features against the residual difference from the groundtruth label.

>*Boosting uses a weighted sum of trees, each of which is constructed by fitting a tree to the residual of the current fit.*
>
>*Each new tree attempts to capture signal that is not yet accounted for by the current set of trees.*

The latter trees are trained to continually reduce the loss from the former trees. The final model aggregates all the decision tress trained along the way.

## Adaptive Boost (AdaBoost)



## Gradient Boosting Machines (GBM)

### Boosting for regression trees

- Algorithm
	- Set 0 as the initial prediction for all training samples. Hence, `residual = y_train`.
		- Repeatedly fit a number of trees
		- Fit on the features against the residual.
		- Add a shrunken version of the prediction from the new tree to the aggregated prediction.
		- Update the residual
	- Aggregate the predictions from all tress, multiplied by the shrinkage parameter.

- Hyperparameters
	- Number of trees ($B$)
		- Can be selected with cross-validation to reduce the chance of overfitting
	- Shrinkage parameter ($\lambda$) - learning rate
		- Typical value: 0.01, 0.001
		- Small $\lambda$ requires a large $B$.
	- Number of splits in each tree: $d$
		- Controls the complexity of the trees

## Bayesian Additive Regression Trees (BART)

BART takes in ideas from both bagging and boosting.

>  *Each tree is constructed in a random manner, and tries to capture signal not yet captured by the current model.*

- Algorithm
	- 
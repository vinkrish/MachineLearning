### Overfitting
The algorithm analyses the data and trains itself to create a high mathematical order model based on the data.

![Overfitting](images/overfitting.jpg)

$$y = x_1 + w_2x_2^3 + w_3x_3^8$$

These high-order terms let this equation define a precise decision boundary between the positive and negative values, but as a result, the training process has created a model that works very well on training data but poorly when asked to predict values based on data it has not trained - this is the class overfit problem and is an issue that must be handled to create machine learning models that work well not only on the training data but also on real-world data.

**Regularization**, **Cross validation**, **Ensemble learning** of which dropout is a part, are all ways to mitigate overfitting. Regularization is a technique where we penalize complex models. We add an additional parameter where if the model coefficients get too complex we add a penalty to the objective function. This is the technique that we use in regression.

### Model Parameter
A model parameter is a configuration variable that is internal to the model and whose value can be estimated from data. Often model parameters are estimated using an optimization algorithm, which is a type of efficient search through possible parameter values.

- They are required by the model when making predictions.
- They values define the skill of the model on your problem.
- They are estimated or learned from data.
- They are often not set manually by the practitioner.
- They are often saved as part of the learned model.
- Parameters are key to machine learning algorithms. They are the part of the model that is learned from historical training data.

**Statistics:** In statistics, you may assume a distribution for a variable, such as a Gaussian distribution. Two parameters of the Gaussian distribution are the mean (mu) and the standard deviation (sigma). This holds in machine learning, where these parameters may be estimated from data and used as part of a predictive model.

**Programming:** In programming, you may pass a parameter to a function. In this case, a parameter is a function argument that could have one of a range of values. In machine learning, the specific model you are using is the function and requires parameters in order to make a prediction on new data.

Some examples of model parameters include:

- The weights in an artificial neural network.
- The support vectors in a support vector machine.
- The coefficients in a linear regression or logistic regression.

### Model Hyperparameter
A model hyperparameter is a configuration that is external to the model and whose value cannot be estimated from data.

- They are often used in processes to help estimate model parameters.
- They are often specified by the practitioner.
- They can often be set using heuristics.
- They are often tuned for a given predictive modeling problem.
- We cannot know the best value for a model hyperparameter on a given problem. We may use rules of thumb, copy values used on other problems, or search for the best value by trial and error.

When a machine learning algorithm is tuned for a specific problem, such as when you are using a grid search or a random search, then you are tuning the hyperparameters of the model or order to discover the parameters of the model that result in the most skillful predictions.

Model hyperparameters are often referred to as model parameters which can make things confusing. A good rule of thumb to overcome this confusion is as follows:

> If you have to specify a model parameter manually then it is probably a model hyperparameter.

Some examples of model hyperparameters include:

- The learning rate for training a neural network.
- The C and sigma hyperparameters for support vector machines.
- The k in k-nearest neighbors.

**Grid Search** is an approach to hyperparameter tuning that will methodically build and evaluate model for each combination of algorithm parameters specified in a grid.
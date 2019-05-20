### What is Machine Learning?
**Arthur Samuel** described it as: "The field of study that gives computers the ability to learn without being explicitly programmed." This is an older, informal definition.

**Tom Mitchell** provides a more modern definition: "A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."

ML systems learn how to combine input to produce useful predictions on never-before-seen data.

_Example_: playing checkers.

**E** = the experience of playing many games of checkers

**T** = the task of playing checkers.

**P** = the probability that the program will win the next game.

In general, any machine learning problem can be assigned to one of two broad classifications:

- Supervised learning
- Unsupervised learning

### Supervised Learning
In supervised learning, we are given a data set and already know what our correct output should look like, having the idea that there is a relationship between the input and the output.

> We try to extrapolate labels for new data given labelled data we already have

Supervised learning problems are categorized into **Regression** and **Classification** problems.

- In a regression problem, we are trying to predict results within a continuous output, meaning that we are trying to map input variables to some continuous function. Commonly used algorithms:
    - Linear Regression
    - Logistics Regression
    - Polynomial Regression
    - Stepwise Regression
    - Ridge Regression
    - Lasso Regression
    - ElasticNet Regression
    - Support Vector Regression (SVR)

- In a classification problem, we are instead trying to predict results in a discrete output. In other words, we are trying to map input variables into discrete categories. Commonly used algorithms:
    - Linear Classifier (Logistic Regression & Naive Bayes)
    - Support Vector Machines
    - Decision Trees
    - Random Forest
    - Neural Networks
    - Nearest Neighbor

_Example 1_:

(a) Given data about the size of houses on the real estate market, try to predict their price. Price as a function of size is a continuous output, so this is a regression problem.

(b) We could turn this example into a classification problem by instead making our output about whether the house "sells for more or less than the asking price." Here we are classifying the houses based on price into two discrete categories.

_Example 2_:

(a) Regression - Given a picture of a person, we have to predict their age on the basis of the given picture

(b) Classification - Given a patient with a tumor, we have to predict whether the tumor is malignant or benign.

### Unsupervised Learning
Unsupervised learning allows us to approach problems with little or no idea what our results should look like. With unsupervised learning there is no feedback based on the prediction results.

> We try to classify data into groups and extract new information hidden in the data

We can derive structure:

- From data where we don't necessarily know the effect of the variables.
- By clustering the data based on relationships among the variables in the data.

_Example_:

**Clustering**: Take a collection of 1,000,000 different genes, and find a way to automatically group these genes into groups that are somehow similar or related by different variables, such as lifespan, location, roles, and so on.

**Non-clustering**: The "Cocktail Party Algorithm", allows you to find structure in a chaotic environment. (i.e. identifying individual voices and music from a mesh of sounds at a cocktail party).

Commonly used algorithms:

- K-means Clustering
- Mean-Shift Clustering
- Density-Based Spatial Clustering of Applications(DBSCAN)
- Ex-Hierarchical
- Dimensionality Reduction (Principal Component Analysis)

### Ensemble learning
In statistics and machine learning, ensemble methods use multiple learning algorithms to obtain better predictive performance than could be obtained from any of the constituent learning algorithms alone (eg: Random Forest).
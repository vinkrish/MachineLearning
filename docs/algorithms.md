### Supervised Learning

- **Linear regression** is a method for finding the straight line or hyperplane that best fits a set of points.

 - **Logistic Regression** is a powerful statistical way of modeling a binomial outcome with one or more explanatory variables. It measures the relationship between the categorical dependent variable and one or more independent variables by estimating probabilities using a logistic function, which is the cumulative logistic distribution. Examples:
    - Credit Scoring
    - Measuring the success rates of marketing campaigns
    - Predicting the revenues of a certain product
    - Is there going to be an earthquake on a particular day?

- **Naive Bayes** is based on applying Bayes’ theorem with the “naive” assumption of conditional independence between every pair of features given the value of the class variable. Examples:
    - To mark an email as spam or not spam
    - Classify a news article about technology, politics, or sports
    - Check a piece of text expressing positive emotions, or negative emotions?
    - Used for face recognition software

- **Support Vector Machine (SVM)** is a discriminative classifier formally defined by a separating hyperplane. In other words, given labeled training data (supervised learning), the algorithm outputs an optimal hyperplane which categorizes new examples. In two dimentional space this hyperplane is a line dividing a plane in two parts where in each class lay in either side. Example:
    - Finding mileage
    - Document classification
    - Image classification

- **Decision Trees** are a non-parametric supervised learning method used for classification and regression. The goal is to create a model that predicts the value of a target variable by learning simple decision rules inferred from the data features. Example:
    - Automobile price prediction (Gradient Boosting Regression - which uses several weak decision trees)

- **Random Forest** is an ensemble learning method for classification, regression and other tasks that operates by constructing a multitude of decision trees at training time and outputting the class that is the mode of the classes (classification) or mean prediction (regression) of the individual trees. Example:
    - Predicting Diabetes

### Unsupervised Learning

- **k-means clustering** aims to partition n observations into k clusters in which each observation belongs to the cluster with the nearest mean.

- **Density-based spatial clustering of applications with noise (DBSCAN)** It is a density-based clustering non-parametric algorithm; given a set of points in some space, it groups together points that are closely packed together (points with many nearby neighbors), marking as outliers points that lie alone in low-density regions (whose nearest neighbors are too far away).

- **Principal Component Analysis (PCA)** is a statistical procedure that uses an orthogonal transformation to convert a set of observations of possibly correlated variables into a set of values of linearly uncorrelated variables called principal components

![Clustering 1](https://s3-us-west-2.amazonaws.com/vinkrish-notes/img/clustering_1.png)
![Clustering 2](https://s3-us-west-2.amazonaws.com/vinkrish-notes/img/clustering_2.png)
![Clustering 3](https://s3-us-west-2.amazonaws.com/vinkrish-notes/img/clustering_3.png)

These are a versatile algorithms that can be used for any type of grouping. Some examples of use cases are:

- Behavioral segmentation:
    - Segment by purchase history
    - Segment by activities on application, website, or platform
    - Define personas based on interests
    - Create profiles based on activity monitoring
- Inventory categorization:
    - Group inventory by sales activity
    - Group inventory by manufacturing metrics
- Sorting sensor measurements:
    - Detect activity types in motion sensors
    - Group images
    - Separate audio
    - Identify groups in health monitoring
- Detecting bots or anomalies:
    - Separate valid activity groups from bots
    - Group valid activity to clean up outlier detection

### Something Else

- **Reinforcement Learning**, where we try to create a model that learns the rules of an environment to best maximize its return or reward.

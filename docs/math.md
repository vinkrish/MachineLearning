**Mean deviation** refers to how far away every data point is from the average of those data points. Squared mean deviation simply squares this result. This is the square of the distance of every data point from the mean, and now we can finally calculate the variance of these data points.

$$variance=\frac{\sum(x_i-\overline{x})^2}{n}$$

**Variance** describe the concentration of data points around the mean, It is a measure of spread/variability of data. 

It is calculated as sum of the squares of the distances of every individual data point from the mean divided by the total number of data points. The estimate of the variance can be improved by tweaking the denominator of this function. This tweak is called the **Bessel's Correction**. So instead of using N for all of the data points, we'll simply use N-1 as the denominator.

$$variance=\frac{\sum(x_i-\overline{x})^2}{n-1}$$

Mean and variance succinctly summarize a set of numbers along with **Standard deviation**, which once again measures how much the numbers jump around.

$$SD = \sqrt{variance}$$

**Mean Square Error (MSE)**  
MSE is the average squared loss per example over the whole dataset. To calculate MSE, sum up all the squared losses for individual examples and then divide by the number of examples:
$$MSE = \frac{1}{N} \sum_{(x,y)\in D} (y - prediction(x))^2$$

**Standard Error(SE)** of a statistic is the standard deviation of its sampling distribution or an estimate of that standard deviation. If the parameter or the statistic is the mean, it is called the standard error of the mean (SEM).  
$\sigma$=Standard Deviation of population, n=size of sample

$$SE = \frac{\sigma}{\sqrt{n}}$$

### Z score (Standard Score)
Given an observed value x, the Z score finds the number of Standard deviations x is away from the mean.

$$Z = \frac{x-\mu}{\sigma}$$

### T distribution
The t-Test is best to use when we do not know the population standard deviation. Instead we use the sample standard deviation.
The number of degrees of freedom(df) is the number of values that are free to vary (n-1).

$$S=\frac{\sum(x_i-\overline{x})^2}{n-1}$$

$$t = \frac{\overline{x}-\mu}{SE}$$

T-tests are also great for testing two sample means (i.e. paired t-tests), we modify the formula to become:

$$SD = \sqrt{S_1^2 + S_2^2}$$

$$SE = \sqrt{\frac{S_1^2}{n1} + \frac{S_2^2}{n2}}$$

$$t = \frac{(\overline{x}_2-\overline{x}_1)-(\mu_2-\mu_1)}{\frac{\sqrt(s_1^2+s_2^2)}{n}}$$

### Cohen's d
It measures the effect size of the strength of a phenomenon. Cohen’s d gives us the distance between means in standardized units.  
$\overline{x} = \overline{x_1} - \overline{x_2}$

$$d = \frac{\overline{x}-\mu}{S}$$

### Margin of Error (ME)
$$ME = t_{critical} * SE$$

### Confidence Interval (CI)
$$CI = \overline{x} \pm ME$$

### Evaluation Metrics

**Positive Class**
In binary classification, the two possible classes are labeled as positive and negative. The positive outcome is the thing we're testing for. (Admittedly, we're simultaneously testing for both outcomes, but play along.) For example, the positive class in a medical test might be "tumor." The positive class in an email classifier might be "spam".

**Negative Class**
In binary classification, one class is termed positive and the other is termed negative. The positive class is the thing we're looking for and the negative class is the other possibility. For example, the negative class in a medical test might be "not tumor." The negative class in an email classifier might be "not spam".

**True Positive (TP)**
An example in which the model correctly predicted the positive class. For example, the model inferred that a particular email message was spam, and that email message really was spam.

**True Negative (TN)**
An example in which the model correctly predicted the negative class. For example, the model inferred that a particular email message was not spam, and that email message really was not spam.

**true positive rate (TPR)**
Synonym for recall. That is: True positive rate is the y-axis in an ROC curve.

$$\text{True Positive Rate} = \frac{\text{True Positives}} {\text{True Positives} + \text{False Negatives}}$$

**False Negative (FN)**
An example in which the model mistakenly predicted the negative class. For example, the model inferred that a particular email message was not spam (the negative class), but that email message actually was spam.

**False Positive (FP)**
An example in which the model mistakenly predicted the positive class. For example, the model inferred that a particular email message was spam (the positive class), but that email message was actually not spam.

**false positive rate (FPR)**
The x-axis in an ROC curve. The false positive rate is defined as follows:

$$\text{False Positive Rate} = \frac{\text{False Positives}}{\text{False Positives} + \text{True Negatives}}$$

**ROC (receiver operating characteristic) Curve: **
A curve of true positive rate vs. false positive rate at different classification thresholds.

**Accuracy**
The fraction of predictions that a classification model got right. In multi-class classification, accuracy is defined as follows:

$$\text{Accuracy} = \frac{\text{Correct Predictions}} {\text{Total Number Of Examples}}$$

In binary classification, accuracy has the following definition:

$$\text{Accuracy} = \frac{\text{True Positives} + \text{True Negatives}}{\text{Total Number Of Examples}}$$

**Precision**
A metric for classification models. Precision identifies the frequency with which a model was correct when predicting the positive class. That is:

$$\text{Precision} = \frac{\text{True Positives}} {\text{True Positives} + \text{False Positives}}$$

**Recall**
A metric for classification models that answers the following question: Out of all the possible positive labels, how many did the model correctly identify? That is:

$$\text{Recall} = \frac{\text{True Positives}} {\text{True Positives} + \text{False Negatives}}$$

### Packages Overview
- **Numpy** let's you perform mathematical functions on large multi dimensional arrays and matrices efficiently.
- **Pandas** is like a more powerful and flexible version of Excel that can handle large amounts of data.
- **Matplotlib** is a plotting library that can produce great visualizations often with very few lines of code.
- **Scikit-learn** is designed to work with NumPy, SciPy and Pandas, provides toolset for training and evaluation tasks:
    - Data splitting
    - Pre-processing
    - Feature selection
    - Model training
    - Model tuning
    - and offers common interface across algorithms
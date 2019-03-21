**Mean deviation** refers to how far away every data point is from the average of those data points. Squared mean deviation simply squares this result. This is the square of the distance of every data point from the mean, and now we can finally calculate the variance of these data points.

$$variance=\frac{\sum(x_i-\overline{x})^2}{n}$$

**Variance** is the sum of the squares of the distances of every individual data point from the mean divided by the total number of data points. The estimate of the variance can be improved by tweaking the denominator of this function. This tweak is called the **Bessel's Correction**. So instead of using N for all of the data points, we'll simply use N-1 as the denominator.

$$variance=\frac{\sum(x_i-\overline{x})^2}{n-1}$$

Mean and variance succinctly summarize a set of numbers along with **Standard deviation**, which once again measures how much the numbers jump around.

$$SD = \sqrt{variance}$$

**Mean Square Error (MSE)** is nothing but the variance of the residual.

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
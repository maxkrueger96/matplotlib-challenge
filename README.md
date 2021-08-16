# matplotlib-challenge
Repo for HW #5


# HW #5 Observations

## Observation 1
The Pearson correlation coefficient measures strength of linearity between two variables. It does so best when the variables are normally distributed.
This test returns a value between -1 and +1, with 0 implying no correlation.
For our purposes, an alpha value of 0.05 will work.

Our sample coefficient is fairly close to +1, which would usually imply a strong, postive linear relationship.

In other words, as average tumor volume increases or decreases, so does average mouse weight, which heuristically makes total sense. If the tumor loses volume, then the mouse will weigh less, and the same holds for gaining volume. Furthermore, if the two variables have a linear relationship, not only to they grow and shrink together, they do so at a constant rate.
Furthermore, the p-value being so much smaller than alpha would allow the user to reject the hypothesis that these variables have no correlation.

However, due to the small sample size, our sample coefficient is not an unbiased estiamtor of the population coefficient. In other words, the expected value of our estimator is different from the true value of the parameter. The p-values can also be misleading for such a small sample, leading to Type 1 or 2 errors. In the case of a smaller sample, an adjusted correlation coefficient is used, of which there are three estimations.

Also, if the data is not normal, then this test may not be efficient, and would not perform well for a small data set like ours.

## Observation 2

The three adjusted correlation coefficients were derived to be minimum variance unbiased estimators, or approximately so, and they approach the original coefficient as the sample size increases. The unique unbiased adjusted estimator with minimum variance is calculated using the original coefficient, multiplied by an instance of the Gaussian hypergeometric function, which is defined by a power series, and is the solution of a second-order linear ODE. The other two coefficients are approximately unbiased, and approach the original coefficient as sample size increases.

We can clearly see that all three adjusted coefficients are very close to the original r-value, all with very small p-values. Therefore, the need to adjust the coefficient appears to be unnecesary in the end. Of course, this could imply that the positive linearity of this sample is indisputable, despite its size. However, we've made no attempt to test the normality of these samples. Should the samples appear to dispute normality, there would be a case for denying the Pearson coefficients and having to rely on another test or just visualization.

## Observation 3
The normality test I used compares the skewness and kurtosis statisics of a sample to those of a standard normal distribution.
Intuitevely, skewness measures the asymmetry of a sample's probability distribution. Not so intuitevely, kurtosis measures how 'heavy' the tails of a distribtuion are, or more specifically how dense the values are outside of the interquantile range, i.e. the outliers. 

If the sample is indeed normally distributed, the skew should be close to zero, as should the kurtosis, depending on how the kurtosis is calculated. (The Pearson standard of kurtosis puts a standard normal distribution at a kurtosis of 3).

The results of the test are, in one word, inconclusive. We do not have enough samples to create a particularly dense histogram. This can make the shape difficult to nail down. The number of bins can greatly impact the shape of the histograms, given our small sample size.

For this number of bins, we can see that even with 3 bins, the tumor volume data has consistent negative skewness, which would certainly suggest that it is not a standard normal distribution! It appears as though we do not have a lot of data very close to the mean, as there are valleys, and not peaks, at the red  mean line. There aren't any features of the mouse weight graph that point to normality. It looks to have a bimodal distribution, although that could be a result of the bin number.

As far as the test values go, neither have small enough p-values to reject the null hypothesis. This only means that we cannot reject them being normally distributed, so there is still a chance that they could be normal. Neither variable's test statistic is particularly close to zero, which would be the normal value. However, their statistics may appear to be much more normal compared to data that allows the null hypothesis to be rejected!

## Observation 4
Analysis of the Kernel Density Estimation certainly offers some clarity into the normality of each variable. For 6 bins, the average tumor volume density estimate appears to be a rather good fit. While the actual densities are quite different between the histogram and the mouse weight estimate, they seem to follow a similar shape. We can clearly see that the average tumor volume distribution estimation behaves like a negatively-skewed bell-shaped curve. While this may not be normal, it is certainly a clearer picture than the mouse weight density plot. 

Due to repetition of values, we essentially only have nine data points of mice weight, which produces a skeleton of a distribution. It does appear, however, that its distribution could be bimodal, in other words, have two peaks.

## Observation 5

Looking at the densities of each regimen's net tumor growth, we can see just how non-normal our data may be in its current state. Clearly, we have a few bimodal distributions, with Zoniferol, Ceftamin, Naftisol, the Placebo,  and possibly Ketapril and Propriva as well. As things stand, we can confidently say that, these distributions are not normal, at least not standard normal. After all, with small sample sizes, you may have to rely on visualization over standard tests. More likely, these data sets follow a bimodal normal distribution, or the sum of two normal distributions with each piece weighted parametrically. There seems to be more mice that had only slight tumor growth or significant tumor growth, with midrange tumor growthn being less common. We do have a few bell-curves at least, however they are all skewed at least slightly, pointing again to non-normality.

## Observation 6
Our linear model has an r-value of 0.841936342469472, so it appears that the model fits well and the relationship between tumor volume and mouse weight is a linear one.  The p-value is 1.3225722434712478e-07, far below a significance level of 0.05, so we can reject the null hypothesis that the slope of the true best-fit line is zero.
Again, the small sample size makes it difficult to confidently reject the null hypothesis, but simply by looking at the model's fit, the data seems to be positively linear. In other words, the two variables increase and decrease together, at a constant rate. If a tumor increases or decreases in volume, then it is given that the weight of the mouse will increase or decrease, respetively, so that correlation is clear. 

What's unclear is the reverse relationship: how does a change in mouse weight affect the tumor volume? Our analysis points to the relationship also being positively linear, yet we must remain skeptical as long as our data set remains small! For example, our plots above showed 'strong' linear relationships between every regimen group with the Placebo's performance AND Capomulin's! So these results, specifically the stats and the p-values, should be taken with a grain of salt.
# Day 3

Today I started with StatQuest for Normal Distribution and Maximum Likelihood. Then, I rewatched the sections on Probabilistic Interpretation and Locally Weighted Linear Regression.

## Maximum Likelihood Estimation

MLE is used to statistically estimate unknown parameters. We change the parameters and find the likelihood of the output with the parameterised inputs till we maximise this likelihood. 

Let

$$
y^{(i)} = \theta^Tx^{(i)} + \epsilon^{(i)}
$$
where $\epsilon^{(i)}$ is assumed to be the error, which is independently and identically distributed (IID). If we assume $\epsilon$ has a normal distribution with mean zero and variance as $\sigma^2$, then the probability function is

$$
p(\epsilon^{(i)}) = \frac{1}{\sigma \sqrt{2\pi}} \exp^{-\frac{(\epsilon^{(i)})^2}{2\sigma^2}}
$$

If we rearrange our previous equation, we get $\epsilon^{(i)} = y^{(i)} - \theta^Tx^{(i)}$ and substituting it back gives

$$
p(y^{(i)} | x^{(i)}; \theta) = \frac{1}{\sigma \sqrt{2\pi}} \exp^{-\frac{ (y^{(i)}-\theta^Tx^{(i)}) ^2}{2\sigma^2}}
$$

This means it is the likelihood of theta. In other words, it tells us how plausible it is that the parametrised training input gives the output as the training output.
For all training data points, it becomes

$$
L(\theta; X, \vec{y}) = \prod_{i=1}^{n}p(y^{(i)} | x^{(i)}; \theta)
$$

To maximise $L(\theta)$, we can maximise $\log{L(\theta)}$ as it is a strictly increasing function. 

$$
l(\theta) = L(\theta) = n\log{\frac{1}{\sigma \sqrt{2\pi}}} - \sum_{i=1}^{n}{\frac{ (y^{(i)}-\theta^Tx^{(i)}) ^2}{2\sigma^2}}
$$
To maximise $l(\theta)$ is the same as minimising $\sum_{i=1}^{n}{\frac{ (y^{(i)}-\theta^Tx^{(i)}) ^2}{2\sigma^2}}$ which is $J(\theta}$. So we can say that least-squares regression is the same as doing maximum likelihood estimation. However, the assumptions made for MLE are not needed for LSE. To minimise $l(\theta)$, we take its derivative with rspect to $\theta$ and equate it to 0.

$$
\frac{\partial}{\partial \theta} l(\theta) = - \sum_{i=1}^{n}{\frac{ x^{(i)}(y^{(i)}-\theta^Tx^{(i)})}{\sigma^2}}
$$

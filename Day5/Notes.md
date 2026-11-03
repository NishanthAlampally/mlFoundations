# Day 5

Logistic Regression is used for classification problems. 

The sigmoid function is defined as

$$
g(z) = \frac{1}{1 + e^{-z}}
$$

This function outputs values between 0 and 1. So, passing a value through this function would give you the probability that the output belongs to class 1.

We can use the function as 
$$
h_\theta(x) = g(\theta^Tx) = \frac{1}{1 + e^{-\theta^Tx}}
$$
So,
$$
P(y = 1| x; \theta) = h_\theta(x)
$$
Since there are only two possible values of y, $P(y = 0 x; \theta) = 1 - h_\theta(x)$. From these, we can write down the probability of observing $y$ as,
$$
P(y| x; \theta) = h_\theta(x)^y(1-h_\theta(x))^{1-y}
$$
This is because when $y$ is 1, the second term becomes 1, and when $y$ is 0, the first term becomes 1.
We can then use this to define the likeliness as
$$
L(\theta) = \prod_{i = 1}^{n}{P(y^{(i)} | x^{(i)}; \theta} = h_\theta(x^{(i)})^{y^{(i)}}(1-h_\theta(x^{(i)}))^{1-y^{(i)}}
$$
As usual, we take the log to get
$$
l(\theta) = \sum_{i = 1}^{n}{y^{(i)}\log{h_\theta(x^{(i)})}} + (1-y^{(i)})\log{1-h_\theta(x^{(i)})}
$$
If we take the derivative, we get
$$
\frac{\partial \ell(\theta)}{\partial \theta}
=
\sum_{i=1}^{n}
\left[
\frac{y^{(i)}}{h_\theta(x^{(i)})}
-
\frac{1-y^{(i)}}{1-h_\theta(x^{(i)})}
\right]
\frac{\partial h_\theta(x^{(i)})}{\partial \theta}
$$

# Day 11
## Newton's Method

Newton's method is a faster way to get to the solution of an equation $f(x) = 0$. We do this as 

$$
(x_2 - x_1) * f'(x_1) = f(x_1) \implies x_2 = x_1 + \frac{f(x_1)}{f'(x_1)}
$$

For vector $\theta$, the notation is 

$$
\theta^{(t+1)} = \theta^{(t)} + H^{-1}\delta_\theta l
$$
where $H$ is the Hessian matrix and $\delta_\theta l$ is the derivative of log-likelihood with respect to $\theta$.

### Newton's Method for Logistic Regression

Let the total log-likelihood for $m$ independent training examples be:

$$\ell(\theta) = \sum_{i=1}^m \left[ y^{(i)} \log h_\theta(x^{(i)}) + (1 - y^{(i)}) \log(1 - h_\theta(x^{(i)})) \right]$$

where the hypothesis is the sigmoid function:

$$h_\theta(x^{(i)}) = g(z^{(i)}) = \frac{1}{1 + e^{-z^{(i)}}}, \quad \text{with } z^{(i)} = \theta^T x^{(i)} = \sum_{r} \theta_r x_r^{(i)}$$

The first partial derivative with respect to parameter $\theta_k$ is:

$$\frac{\partial \ell(\theta)}{\partial \theta_k} = \sum_{i=1}^m \left( y^{(i)} - h_\theta(x^{(i)}) \right) x_k^{(i)}$$

Differentiating to Form the Hessian Entry $H_{jk}$By definition of the Hessian matrix:
  
$$H_{jk} = \frac{\partial^2 \ell(\theta)}{\partial \theta_j \partial \theta_k} = \frac{\partial}{\partial \theta_j} \left( \frac{\partial \ell(\theta)}{\partial \theta_k} \right)$$

Substitute the first derivative into the operator:

$$H_{jk} = \frac{\partial}{\partial \theta_j} \left[ \sum_{i=1}^m \left( y^{(i)} - h_\theta(x^{(i)}) \right) x_k^{(i)} \right]$$

Pass the derivative inside the summation:

$$H_{jk} = \sum_{i=1}^m \frac{\partial}{\partial \theta_j} \left[ \left( y^{(i)} - h_\theta(x^{(i)}) \right) x_k^{(i)} \right]$$

Evaluating the DerivativeBecause $x_k^{(i)}$ and $y^{(i)}$ are observed data, they are constants with respect to $\theta_j$:

$$\frac{\partial x_k^{(i)}}{\partial \theta_j} = 0, \quad \frac{\partial y^{(i)}}{\partial \theta_j} = 0$$

Factor out $x_k^{(i)}$:

$$H_{jk} = \sum_{i=1}^m x_k^{(i)} \frac{\partial}{\partial \theta_j} \left( y^{(i)} - h_\theta(x^{(i)}) \right) = \sum_{i=1}^m x_k^{(i)} \left( 0 - \frac{\partial h_\theta(x^{(i)})}{\partial \theta_j} \right)$$

Apply the chain rule to $h_\theta(x^{(i)}) = g(z^{(i)})$ where $g'(z) = g(z)(1 - g(z))$:

$$\frac{\partial h_\theta(x^{(i)})}{\partial \theta_j} = \frac{d g(z^{(i)})}{d z^{(i)}} \cdot \frac{\partial z^{(i)}}{\partial \theta_j}$$

Since $z^{(i)} = \sum_{r} \theta_r x_r^{(i)}$, we have $\frac{\partial z^{(i)}}{\partial \theta_j} = x_j^{(i)}$:$$\frac{\partial h_\theta(x^{(i)})}{\partial \theta_j} = h_\theta(x^{(i)})\left(1 - h_\theta(x^{(i)})\right) x_j^{(i)}$$

Component-Wise ResultSubstitute the derivative of $h_\theta(x^{(i)})$ back into the expression:

$$H_{jk} = -\sum_{i=1}^m h_\theta(x^{(i)})\left(1 - h_\theta(x^{(i)})\right) x_j^{(i)} x_k^{(i)}$$

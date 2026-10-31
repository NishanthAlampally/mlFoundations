# Day1

I'm starting with **Stanford CS229: Machine Learning**, taught by **Andrew Ng**. I watched the first two episodes of the course. The first episode introduces the fundamentals of ML, including its applications and different types.

### Key Takeaways

- **Purpose of ML:** Machine learning is used to make predictions from data or discover patterns and structure within it.
- **Types of ML tasks:** Two common tasks are classification, which predicts discrete categories, and regression, which predicts continuous numerical values.
- **ML training paradigms:** The three main paradigms are supervised learning (training on inputs with known outputs), unsupervised learning (finding patterns in data without labelled outputs), and reinforcement learning (learning through interactions and rewards or penalties).

### Linear Regression

One of the simplest ML models is **linear regression**, which models the relationship between input variables and a numerical output.

For example, we could use a single input, \(x\), to predict an output, \(y\). With multiple inputs, the model can use several features to make a single prediction.

Some fundamental terminology:

- **Features \(x\):** The input variables provided to the model.
- **Target \(y\):** The actual output value we want the model to predict.
- **Hypothesis $\(h_\theta(x)\)$:** The model's prediction for a given input.
- **Training examples:** The observed input-output pairs used to train the model.
- **Parameters $\theta$:** The weights and biases that the model learns during training to determine how the features influence its predictions.

For a simple linear regression model with one feature, the hypothesis is

$$
h_\theta(x) = \theta_0 + \theta_1 x
$$

Here, $\theta_0$ is the intercept (bias), and $\theta_1$ is the weight assigned to the feature $x$.
The goal of training is to find parameter values that allow the model to make predictions as close as possible to the actual target values.

So, we define $h_\theta(x)$ as,

$$
h_\theta(x) = \sum_{j=1}^{n} \theta_jx_j
$$

Here, $n$ denotes the number of features.

To do this, we use Gradient Descent.

### Gradient Descent

Gradient Descent is like "descending" from a mountain. We hope to find the minimum point on the land, which is the point at which our parameters allow the model to make accurate predictions. 

#### Batch Gradient Descent

We define the error as,
$$
J(\theta) = \frac{1}{2}\sum_{i=1}^{m}\(h\theta(x^i) - y^i\)^2
$$
where $m$ is the number of training points. So, in reality, $h_\theta(x)$ is a 2D array with $m$ rows and $n$ columns.

To perform gradient descent, we take the partial derivative of this error with respect to each feature and subtract it from Theta. We use a scaling factor called the learning rate $\alpha$. It is important to use an optimal learning rate, as we could be "descending" too fast or too slow and miss the minimum point.

$$
\frac{\partial}{\partial \theta_j}J(\theta) = 2\frac{1}{2}\sum_{i=1}^{m}\(h_\theta(x^i) - y^i\)(x_j^i)
$$

It would be easier to compute this derivative by listing the elements of $h_\theta(x)$ and then doing it.
We use this to then calculate new values of $\theta$.

$$
\theta_j := \theta_j - \alpha\frac{\partial}{\partial \theta_j}J(\theta)
$$

As you repeat the process, you will eventually converge to some value.

#### Stochastic Gradient Descent

In Batch Gradient Descent, we calculate the gradient for all training points with respect to each feature. In Stochastic Gradient Descent, we only calculate for one training example at a time before recalculating $\theta$.

We loop from $i=1$ to $m$, the following:

$$
\frac{\partial}{\partial \theta_j}J(\theta) = \(h\theta(x^i) - y^i\)(x_j^i)
$$

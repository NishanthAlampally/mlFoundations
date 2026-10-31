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
- **Hypothesis \(h_\theta(x)\):** The model's prediction for a given input.
- **Training examples:** The observed input-output pairs used to train the model.
- **Parameters $\theta$:** The weights and biases that the model learns during training to determine how the features influence its predictions.

For a simple linear regression model with one feature, the hypothesis is

$$
h_\theta(x) = \theta_0 + \theta_1 x
$$

Here, \(\theta_0\) is the intercept (bias), and \(\theta_1\) is the weight assigned to the feature \(x\).

The goal of training is to find parameter values that allow the model to make predictions as close as possible to the actual target values.

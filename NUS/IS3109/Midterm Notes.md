## Linear Algebra & Analytic Geometry

- **Dot Product**: For vectors $x, y \in \mathbb{R}^n$, the dot product is $\langle x,y \rangle = x^T y = \sum_{i=1}^n x_i y_i$.
- **Vector Norms**: The $p$-norm is $\vert{}\vert{}x\vert{}\vert{}_p = (\vert{}x_1\vert{}^p + \vert{}x_2\vert{}^p + ... + \vert{}x_n\vert{}^p)^{1/p}$. The Euclidean norm ($L_2$) is standard for length, while the Manhattan norm is $L_1$.  
- **Angle Between Vectors**: $\cos \omega = \frac{x^T y}{\vert{}\vert{}x\vert{}\vert{} \vert{}\vert{}y\vert{}\vert{}}$. If $\cos \omega = 0$, the vectors are orthogonal.
- **Convex Sets & Functions**: A set is convex if a line segment between any two points lies entirely inside the set: $\theta x + (1-\theta)y \in C$ for $0 \le \theta \le 1$. A twice-differentiable function is convex if and only if its Hessian matrix is positive semidefinite.
- **Positive Definite Matrix**: A symmetric matrix $A$ is positive definite if $x^T A x > 0$ for all non-zero vectors $x$.

**Problem-Solving Tip (Linear Independence):** To determine if a set of vectors is linearly independent, place them as columns in a matrix $A$ and solve the system $A\lambda = 0$. Use row operations to reduce the matrix. If the only unique solution is $\lambda = 0$, the vectors are independent; if you find infinitely many solutions (a free variable), they are linearly dependent.
## Matrix Calculus & Optimization

- **Gradient Vector ($\nabla f$)**: The collection of first-order partial derivatives of a scalar function $f(x)$.
- **Jacobian Matrix ($J$)**: The matrix of first-order partial derivatives for a vector-valued function $f: \mathbb{R}^n \rightarrow \mathbb{R}^m$. For a linear function $f(x) = Ax + b$, the Jacobian $\nabla_x f(x) = A$.
- **Hessian Matrix ($H$)**: The symmetric matrix containing all second-order partial derivatives of a scalar function.
- **Quadratic Functions**: For $f(x) = \frac{1}{2} x^T A x + p^T x$, the gradient is $\nabla_x f(x) = Ax + p$.
- **Least Squares Regression**: Minimizing the sum of squared errors $S(\beta) = \frac{1}{2}(Y - X\beta)^T(Y - X\beta)$. Setting the gradient $\nabla_\beta S(\beta) = -X^T(Y - X\beta) = 0$ yields the optimal weights $\beta = (X^T X)^{-1} X^T Y$
- **Chain Rule**: $(g(f(x)))' = g'(f(x))f'(x)$. For multivariate composite functions $O = K(p,q)$ where $p = g(y)$ and $q = h(z)$, apply the multivariate chain rule: $\frac{\partial O}{\partial w} = \frac{\partial O}{\partial p}\frac{\partial p}{\partial w} + \frac{\partial O}{\partial q}\frac{\partial q}{\partial w}$.
**Calculus Identities to Remember:**
- Sigmoid derivative: $f(x) = \frac{1}{1 + e^{-x}} \implies f'(x) = f(x)(1 - f(x))$.
- Tanh derivative: $f(x) = \tanh(x) \implies f'(x) = 1 - (f(x))^2$.
- Gaussian derivative: $f(x) = \exp(-\frac{1}{2\sigma^2}(x-\mu)^2) \implies f'(x) = -\frac{x-\mu}{\sigma^2} f(x)$.
## Gradient Descent Techniques
- **Standard Gradient Descent**: Updates parameters in the direction of the steepest descent (negative gradient)  $$x_{i+1} = x_i - \lambda_i \nabla f(x_i)$$
- **Exact Line Search (Optimal Step Size)**: Finds the optimal step size $\lambda_i$ by minimizing the objective function along the chosen direction $d_i$. For a quadratic function $f(x) = \frac{1}{2}x^T Ax - b^T x$, the optimal step size is:
$$\lambda_i = \frac{r_i^T r_i}{r_i^T A r_i}$$
								where $r_i = b - Ax_i = -\nabla f(x_i)$.

- **Gradient Descent with Momentum**: Adds a memory term to smooth out updates and accelerate convergence.
$$x_{i+1} = x_i - \lambda_i \nabla f(x_i) + \alpha(x_i - x_{i-1})$$
					    where $\alpha > 0$ is the momentum parameter.
- **Newton's Method**: Uses second-order derivatives (Hessian) to take more direct steps toward the minimum.$$x_{i+1} = x_i - H_k^{-1} \nabla f(x_k)$$
- **Stochastic Gradient Descent (SGD)**: Approximates the gradient using a single randomly chosen data point (or a mini-batch) to update weights, rather than the entire dataset, improving computational efficiency.

**Problem-Solving Tip (Gradient Descent & Newton's Method):**
1. _For Exact Line Search:_ If asked to find the optimal step size, define a function $g(\lambda) = f(x_i + \lambda d_i)$. Take the derivative of $g$ with respect to $\lambda$, set it to 0, and solve for $\lambda$.
2. _For Newton's Method:_ Always compute the Gradient vector $\nabla f(x)$ and the Hessian matrix $H(x)$ first. Substitute the initial point $x_0$ into both, find the inverse of the numeric Hessian matrix, and apply the update formula.
## Probability, Statistics & Data Preparation

- **Expected Value & Variance**: $\mu = E[X] = \sum x_i P[X = x_i]$. Variance is $Var(X) = E[X^2] - \mu^2$.
- **Covariance**: $Cov(X,Y) = E[(X-\mu_X)(Y-\mu_Y)] = E[XY] - E[X]E[Y]$. If $X$ and $Y$ are independent, $Cov(X,Y) = 0$.
- **Binomial Distribution**: $P(x) = \binom{n}{x} p^x (1-p)^{n-x}$. Expected value is $np$, variance is $np(1-p)$.
- **Pearson Chi-Square ($\chi^2$)**: Used to test association between categorical variables.
$$\chi^2 = \sum \frac{(f_{obs} - f_{exp})^2}{f_{exp}}$$
    _Expected Frequency_ = $\frac{(\text{Row Total}) \times (\text{Column Total})}{\text{Grand Total}}$.

**Problem-Solving Tip (Chi-Square Test):** To test for feature independence, calculate the expected cell counts under the null hypothesis (that variables are independent). Sum the squared differences divided by expected counts. If your $\chi^2$ statistic is greater than the critical value (or if $p < \alpha$), reject the null hypothesis, meaning the features _are_ associated and should be included in predictive modeling.
## Decision Trees

- **Shannon's Entropy**: Measures the amount of uncertainty or impurity in a dataset.
$$Entropy = -\sum_i p_i \log_2 p_i$$
- **Information Gain (IG)**: The reduction in entropy after splitting a dataset $S$ using a feature.
$$IG = Entropy(S) - \sum_v \frac{\vert{}S_v\vert{}}{\vert{}S\vert{}} Entropy(S_v)$$
- **Gini Index**: An alternative impurity metric used by CART.
$$Gini(t, D) = 1 - \sum_l P(t=l)^2$$
    For binary classification with proportions $p_1$ and $p_2$, this simplifies to $2p_1 p_2$.
- **Regression Trees (Variance)**: For continuous targets, impurity is measured by variance $\frac{1}{n-1} \sum (t_i - \bar{t})^2$.
- **Gradient Boosting for Regression**: Fits a sequence of models to the residuals of the previous models. The residual $r_i = y_i - F_{m-1}(x_i)$ is mathematically equivalent to the negative gradient of the square loss function.

**Problem-Solving Tip (Tree Splitting):** For continuous features (like Age or Elevation), sort the data by the feature. Evaluate candidate split boundaries located at the midpoints between values where the target class changes. Calculate the weighted impurity (Entropy or Gini) for each candidate split, and pick the boundary that yields the lowest resulting impurity.

## Neural Networks (Single Computational Layer)
- **Biological Motivation**: Artificial Neural Networks are inspired by biological neurons, where dendrites receive inputs (scaled by synaptic weights), the cell body computes a function, and the axon transmits the output.
- **The Perceptron**: Computes a linear combination of inputs and passes it through an activation function (like the sign function).$$\hat{y} = sign(W \cdot X + b) = sign\left(\sum_{j=1}^d w_j x_j + b\right)$$
- **Perceptron Weight Update**: When an error occurs ($y \neq \hat{y}$), weights are updated to push the prediction closer to the true label.
$$W \leftarrow W + \alpha (y - \hat{y}) X$$
							where $\alpha$ is the learning rate.

- **Activation Functions**: Non-linear functions allow neural networks to act as universal function approximators.
    - _Identity/Linear_: $\Phi(v) = v$ (used for standard regression).
    - _Sigmoid_: $\sigma(v) = 1 / (1 + e^{-v})$ (bounds output between 0 and 1, used for probability).
    - _Tanh_: $\tanh(v) = (e^{2v} - 1) / (e^{2v} + 1)$ (bounds output between -1 and 1, mean-centric).
    - _ReLU_: $\Phi(v) = \max\{v, 0\}$ (fast, avoids some vanishing gradient issues).
- **Loss Functions**:
    - _Least Squares_: $L = \frac{1}{2}(y - \hat{y})^2$.
    - _Hinge Loss_: $L = \max\{0, 1 - (y \cdot \hat{y})\}$ (used in maximum margin classifiers).
    - _Cross-Entropy (Categorical)_: $L = -\log(\hat{y}_r)$ where $r$ is the correct class.

**Problem-Solving Tip (Perceptron Training):** To perform a perceptron update step, compute the dot product of the current weights and the input pattern, then apply the activation function. If the prediction is correct, do nothing. If incorrect, apply the update formula $W_{new} = W_{old} + \alpha (y - \hat{y}) X$. In _batch mode_, calculate the independent errors for _all_ instances first using the initial weights, sum the gradient contributions, and perform a single aggregated weight update at the end of the epoch.
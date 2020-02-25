---


typora-copy-images-to: img
---

# Classification and Representation

## Classification

- for example, spam/not spam
- 0: negative class, 1: positive class; y: label
- regression + threshold

![image-20200223183826498](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223183826498.png)

- not good: hypothesis can be > 1 or < 0
- **logistic regression**: hypothesis is always in [0, 1]

## Hypothesis Representation

- linear regression: 
  $$
  h_\theta(x)=\theta^Tx
  $$

- logistic regression model: want 0<=h(x)<=1
  $$
  h_\theta(x)=g(\theta^Tx),\,where\space g(z)=\frac{1}{1+e^{-z}}
  $$
  ![image-20200223212348582](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223212348582.png)

  the function g is called **Sigmoid function**/**logistic function**.

- intuition of sigmoid function

  ![image-20200223212522261](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223212522261.png)

- interpretation of hypothesis output: estimated probability that y=1 on input x

## Decision Boundary

- threshold: 0.5

- $$
  g(z)\ge0.5\Leftrightarrow z\ge0\Leftrightarrow \theta^Tx\ge0
  $$

- intuition:

  ![image-20200223214301651](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223214301651.png)

- the line x1+x2=3 is called decision boundary

- non-linear decision boundary: it's obvious that the boundary is a circle in the example below

  ![image-20200223214652799](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223214652799.png)

# Logistic Regression Model

## Cost Function

$$
J(\theta)=\frac{1}{m}\sum_{i=1}^mcost(h_\theta(x^{(i)}),y^{(i)})\\
in\space linear\space regression:cost(a,b)=\frac{1}{2}(a-b)^2
$$

- if we use the cost(a,b) in linear regression, the cost function J will be non-convex, so the gradient descent method is not guaranteed to converge to the global minimum.

- we define the cost(a,b) as
  $$
  Cost(h_\theta(x),y)=\begin{cases}
  -log(h_\theta(x))&if\space y=1\\
  -log(1-h_\theta(x))&if\space y=0\\
  \end{cases}
  $$

- intuition: if y=1, the larger the hypothesis is, the smaller the cost is, if the hypothesis=1, the cost=0; if y=0, take the reverse.
- if y=1, as h(x)->0, Cost->infinity

## Simplified Cost Function and Gradient Descent

- compress the function cost(h(x),y) to one line:
  $$
  Cost(h_\theta(x),y)=-ylog(h_\theta(x))-(1-y)log(1-h_\theta(x))
  $$

- why to choose this function: the principle of maximum likelihood estimation

- gradient descent: simple calculation

  ![image-20200223222604134](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223222604134.png)

  

- vectorization

  ![image-20200223223155079](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223223155079.png)

  recall, in linear regression, the vectorization is:
  $$
  \theta:=\theta-\frac\alpha{m}X^{T}(X\theta-y)
  $$

## Advanced Optimization

- optimization algorithm: given function J(theta), want min_theta(J(theta))
- optimization algorithms: conjugate gradient, BFGS, L-BFGS (no need to manually pick alpha, often faster than gradient descent)

- no need to implement those algorithms

- in octave/MATLAB, write a function for your J like:

  ![image-20200223224428057](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223224428057.png)

- then

  ![image-20200223224535359](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223224535359.png)

  (gradient objective parameter -> on, max iteration -> 100; 'functionVal': min jVal; exitFlag: whether or not converged; fminunc: 'unc' for unconstrained)

- for logistic regression:

  ![image-20200223230610653](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223230610653.png)

# Multiclass Classification: One-vs-all

![image-20200223232331003](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223232331003.png)

- use more than one classifier

  ![image-20200223232830217](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223232830217.png)

![image-20200223233242625](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223233242625.png)

# Solving the Problem of Overfitting

## The Problem of Overfitting

- underfit/high bias

  ![image-20200223235550256](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223235550256.png)

- ![image-20200223235603396](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200223235603396.png)

- the latter one is kind of "overfitting" or "high variance"

- how to address overfitting: plotting?
- options: **reduce number of features**: manually select important features or use model selection algorithm; **regularization**: reduce magnitude/values of parameters theta_j (this works well when we have a lot of features, each of which contributes a bit to predicting y).

## Cost Function

- penalize and make some parameters really small

  ![image-20200224004043035](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200224004043035.png)

- in this way, to find the minimum, theta_3 and theta_4 end up very small
- Regularization: ![image-20200224004240873](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200224004240873.png)

![image-20200224004336334](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200224004336334.png)

​	(shrink every single parameter)

- note, if the lambda, or the **regularization parameter**, is chosen too large for the problem, it can cause underfitting.

## Regularized Linear Regression

- for gradient descent case

![image-20200224005450835](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200224005450835.png)

or

![image-20200224005602771](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200224005602771.png)

Note that the coefficient $1-\alpha\frac{\lambda}{m}$ must be less than 1 to guarantee stability. on the other hand, having lambda > 0 maintain the convexity of cost function.

- for normal equation case

  ![image-20200224010211083](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200224010211083.png)

- the underlined matrix is meant to be invertible or non-singular, even if m<n

## Regularized Logistic Regression

- new cost function

  ![image-20200224010631974](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200224010631974.png)

- gradient descent: plus additional term for j=1,2,3,...,n

- advanced optimization: edit the cost function and its gradient

  ![image-20200224011820464](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200224011820464.png)

  

  


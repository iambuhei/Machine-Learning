---
typora-copy-images-to: img
---

# Multivariate Linear Regression

## Multiple Features

### Notation

- we call the "x" in univariative linear regression a **<u>feature</u>**

![image-20200209101217579](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200209101217579.png)

### Hypothesis

- linear combination of features x1, x2, ...

- for convenience of notation, define x0 = 1, so we get:

  ![image-20200209101822101](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200209101822101.png)

## Gradient Descent for Multiple Variables

- Hypothesis: 
  $$
  h_\theta(x)=\theta^Tx\\\theta,x\in\R^{n+1}
  $$

- Parameters:
  $$
  \theta=(\theta_0,\theta_1,...,\theta_n)^T
  $$

- 
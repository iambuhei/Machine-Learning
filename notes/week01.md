---
typora-copy-images-to: img
---

# Introduction

## Definition of Machin Learning

- Arthur Samuel described it as: "the field of study that gives computers the ability to learn without being explicitly programmed." This is an older, informal definition.

- Tom Mitchell provides a more modern definition: "A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."Example: playing checkers.

  E = the experience of playing many games of checkers

  T = the task of playing checkers.

  P = the probability that the program will win the next game.

## Machine learning algorithms

- Supervised learning (Teach the machine how to complete a task)
- Unsupervised learning (Let the machine learn by itself)

Others: Reinforcement learning, recommender systems

Also talk about: Practical advice for applying learning algorithms

### Supervised Learning

- What is supervised leaning?

​	"correct answers" are given

​	In supervised learning, we are given a data set and already know what our correct output should look like, having the idea that there is a relationship between the input and the output.

- Example 1: Regression

​	<u>**regression problem**</u>: predict continuous real-valued output

- Example 2: Classification

![image-20200208070242130](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200208070242130.png)![image-20200208070654458](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200208070654458.png)

​	estimate the probability

​	<u>**classification**</u>: discrete valued output (0 or 1), or maybe more discrete data 

​	more variables:

![image-20200208070819005](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200208070819005.png)

​	the learning algorithm should find the black line, or other two-dimensional graphics

### Unsupervised Learning

- What is unsupervised learning?

​	no labels are given on the dataset

- Example 1: Clustering

​	<u>**clustering algorithm**</u>: find the structure of the data

​	Take a collection of 1,000,000 different genes, and find a way to automatically group these genes into groups that are somehow similar or related by different variables, such as lifespan, location, roles, and so on.

​	Application: organize computing clusters; social network analysis; market segmentation; astronomical data analysis

- Example 2: Non-clustering

​	The "Cocktail Party Algorithm", allows you to find structure in a chaotic environment. (i.e. identifying individual voices and music from a mesh of sounds at a [cocktail party](https://en.wikipedia.org/wiki/Cocktail_party_effect)).

![image-20200208072702818](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200208072702818.png)

​	Octave/MATLAB -> fewer codes, faster to learn, more efficient

# Model and Cost Function

## Model Representation

linear regression with one variable

learning function: h (stands for **<u>hypothesis</u>**) -> output: estimated value

![image-20200208090627463](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200208090627463.png)

![image-20200208090456370](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200208090456370.png)

rmk: univariate: one variable

## Cost Function

- definition

task: choose thetas <=> minimize the cost functions

cost function:  J(theta0, theta1), for example:

![image-20200208091305536](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200208091305536.png)

rmk: 

1.  it's also called squared error function or mean squared error
2. the mean is halved 1/2 as a convenience for the computation of the gradient descent

- Example 1: set theta0 = 0

set datasets = {(1,1),(2,2),(3,3)}

the figure of J(theta 1) is:

![image-20200208092524619](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200208092524619.png)

we can find the minimum at theta1 = 1.

- Example 2: J(theta0, theta1) figure

![image-20200208093211606](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200208093211606.png)

or contour plot/contour figure

![image-20200208093247189](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200208093247189.png)
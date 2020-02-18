---

typora-copy-images-to: img
---

# Multivariate Linear Regression

## Multiple Features

### Notation

- we call the "x" in univariate linear regression a **<u>feature</u>**

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

- define x0 = 1

- Cost function: to evaluate the hypothesis
  
  ![image-20200217171655746](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217171655746.png)

- Gradient descent:

  ![image-20200217172029863](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217172029863.png)

- Simple calculation

  ![image-20200217172417796](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217172417796.png)

## Gradient Descent in Practise

### Feature Scaling

- Idea: Make sure features are on a similar scale.

- example:

  ![image-20200217172838518](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217172838518.png)

- scaling: define the variables in a well scaled way
- as the adjecent searching paths in gradient descent are perpendicular to each other, scaling is important to make the countour more like perfect circles.

![image-20200217173251259](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217173251259.png)

![image-20200217173624168](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217173624168.png)

![image-20200217173803620](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217173803620.png)

- For example, if x_i*x**i* represents housing prices with a range of 100 to 2000 and a mean value of 1000, then, x_i := \dfrac{price-1000}{1900}*x**i*:=1900*p**r**i**c**e*−1000.

### Learning Rate

- or the "alpha"

  ![image-20200217174231407](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217174231407.png)

- convergence condition: J(theta) decreases by less than some epsilon > 0
- too large: no convergence; too small: slow convergence

## Features and Polynomial Regression

### Choice of Features

- Example: merge two features into one

  ![image-20200217181440662](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217181440662.png)

  use the area instead of the frontage and the depth.

### Polynomial Regression

![image-20200217181622044](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217181622044.png)

![image-20200217181723358](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217181723358.png)

# Computing Parameters Analytically

## Normal Equation

Solve linear equations so that the derivative of J equals to 0.

![image-20200217182411436](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217182411436.png)

![image-20200217182608024](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217182608024.png)

Normal equation:

 ![image-20200217185653927](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217185653927.png)

proof: least squre problem's normal equation.

n is large -> very slow (O(n^3))

## Normal Equation Noninvertibility

![image-20200217190149556](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217190149556.png)

Octave: pinv() and inv(); p: pseudo

When could X'*X be singular?

![image-20200217191251334](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200217191251334.png)

# Octave/MATLAB Tutorial

## Basic Operations

operators:

+,-,*,/,=,==,~=(not !=),%(not //),'(transpose)

'' stands for a string, not a char

the following are true:

- zeros(1,3) == [0 0 0] == [0, 0, 0]

- ones(3,2) == [1 1;1 1;1 1]

- rand(3,3) : give a 3x3 matrix whose elements are randomly picked from (0,1)

- 1:6 == [1 2 3 4 5 6]

- 1:0.5:3 == [1 1.5 2 2.5 3]
- matrix(?:?)

![image-20200218180638244](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218180638244.png)

![image-20200218180659523](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218180659523.png)

- randn(3,3) : give a 3x3 matrix whose elements are picked from N(0,1)

(Hint: use a+sqrt(b)*randn(m,n) to obtain an m x n matrix picked from N(a,b))

- hist: see below

![image-20200218175038923](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218175038923.png)

![image-20200218175045701](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218175045701.png)

- hist(w,100):

![image-20200218175113586](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218175113586.png)

- help:

![image-20200218175339832](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218175339832.png)

- size:

  ![image-20200218175648960](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218175648960.png)

- length:

![image-20200218175851930](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218175851930.png)

- index of a matrix:

  ![image-20200218181107378](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218181107378.png)

  ![image-20200218181143264](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218181143264.png)

  ![image-20200218181236015](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218181236015.png)

  ![image-20200218181532081](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218181532081.png)

- append a matrix to a matrix:

![image-20200218181407036](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218181407036.png)

(A = [1 10;3 11;5 12] previously)

![image-20200218181648835](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218181648835.png)

![image-20200218181704106](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218181704106.png)

## Moving Data Around

how to load data into MATLAB/Octave?

- pwd: show current path

- cd: go to a path

- load: load files

  ![image-20200218180133838](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218180133838.png)

- who: show current variables

  ![image-20200218180257581](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218180257581.png)

- whos: who in detail

  ![image-20200218180400219](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218180400219.png)

- save: save hello.mat v %save the variable v into hello.mat file

  ![image-20200218181020586](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218181020586.png)

- clear: clear every variable

  ![image-20200218180906066](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218180906066.png)

## Computing on Data

matrix multiply: 

- A*B: matrix multiply

- A.*B: elementwise multiply

  ![image-20200218182331731](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218182331731.png)

![image-20200218182343545](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218182343545.png)

![image-20200218182356534](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218182356534.png)

![image-20200218182452361](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218182452361.png)

![image-20200218182541956](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218182541956.png)

- max

![image-20200218182715939](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218182715939.png)

here ind stands for index.

- elementwise logical operation

  ![image-20200218182757145](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218182757145.png)

- find(a<3) == [1 3 4]

- magic(3):

  ![image-20200218183111880](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218183111880.png)

  ![image-20200218183204911](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218183204911.png)

- ![image-20200218183314810](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218183314810.png)

- max of column: (1 stands for the first dimension) (default case)

  ![image-20200218183552593](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218183552593.png)

- max of row: (2 stands for the second dimension)

  ![image-20200218183649629](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218183649629.png)

- max elements:

  ![image-20200218183752722](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218183752722.png)

- sum: 1 for column, 2 for row

  ![image-20200218184003413](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218184003413.png)

  (A == magic(9))

  diagonals:

![image-20200218184158021](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218184158021.png)

- flipud

  ![image-20200218184249670](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218184249670.png)

- pinv(): pseudo-inverse

## Plotting Data

- plot()

![image-20200218184618497](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218184618497.png)

![image-20200218184625475](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218184625475.png)

- hold on ('r' is for red) % hold off to cancel hold

![image-20200218184756059](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218184756059.png)

![image-20200218184828151](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218184828151.png)

- other configures

  ![image-20200218184853849](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218184853849.png)

![image-20200218184904931](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218184904931.png)

![image-20200218185327466](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218185327466.png)

![image-20200218185347258](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218185347258.png)

- print out file

  ![image-20200218185432053](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218185432053.png)

- ![image-20200218190336940](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218190336940.png)

- change range: ![image-20200218191353419](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218191353419.png)

- subplot

![image-20200218191439631](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218191439631.png)

![image-20200218191442879](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218191442879.png)

- clf: clear figure

- imagesc (comma's function is shown below)

  ![image-20200218191657279](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218191657279.png)

- comma

  ![image-20200218191813154](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218191813154.png)

## Control Statements: for, while, if statement

**example 1**

```matlab
v = zeros(10,1);
for i = 1:10
	v(i) = 2^i;
end;
```

**output 1**

![image-20200218192158707](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218192158707.png)

**example & output 2 (while)**

![image-20200218192616648](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218192616648.png)

**example 3 (if, break)**

![image-20200218192652611](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218192652611.png)

**output 3**

![image-20200218192702382](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218192702382.png)

**example & output 4 (elseif, else, disp)**

![image-20200218192829136](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218192829136.png)

**example & output 5 (user-defined function)**

![image-20200218193256793](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218193256793.png)

![image-20200218193242671](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218193242671.png)

![image-20200218193422636](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218193422636.png)

addpath: add a path to Octave's search path

**example & output 6 (multivariate function)**

![image-20200218193546379](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218193546379.png)

![image-20200218193658931](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218193658931.png)

**example 7 (cost function)**

![image-20200218193942595](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218193942595.png)

## Vectorization

Note: MATLAB's index starts at 1, not 0

**example 1.1 (MATLAB)**

![image-20200218194505617](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218194505617.png)

**example 1.2 (C++)**

![image-20200218194628445](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218194628445.png)

**example 2 (Gradient descent)**

![image-20200218194830313](E:\2019-2020 Spring\Machine Learning\notes\img\image-20200218194830313.png)

Vectorization:
$$
\theta:=(\theta_0,...,\theta_n)^T\\
x^{(i)}:=(x^{(i)}_0,...,x^{(i)}_n)\\
h_\theta(x)(=\theta^Tx)\in\R\\
vectrization:\\
\theta:=\theta-\frac\alpha{m}\sum_{i=1}^m{(h_\theta(x^{(i)})-y^{(i)})x^{(i)}}\\
more\space vectorization:\\
since\space X=({x^{(0)}}^{T},...,{x^{(m)}}^{T})^{T},we\space have:\\
\theta:=\theta-\frac\alpha{m}X^{T}(X\theta-y)
$$
note, the h(x(i))-y(i) is a real number.
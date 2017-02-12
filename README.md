# machine-learning-knowledge
knowledge memos/citations of machine-learning based on a coursera class: Machine Learning by Andrew Ng.

# What is machine learning? (Two definitions)

- Arthur Samuel's older and informal definition:  
  "the field of study that gives computers the ability to learn without being explicitly 
programmed."

- Tom Mitchell's more modern definition:  
  "A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."  
    - Example: playing checkers.  
    - E = the experience of playing many games of checkers  
    - T = the task of playing checkers.  
    - P = the probability that the program will win the next game.  

```
In general, any machine learning problem can be assigned to one of two broad classifications:
Supervised learning and Unsupervised learning.
```

<br>
***

# Supervised Learning and Unsupervised Learning<br>
## Supervised Learning
### Definition
- "right answer" is given.
- In supervised learning, we are given a data set and already know what our correct output should look like, having the idea that there is a relationship between the input and the output.

### Categories
- Regression (回帰)
    - we are trying to predict results within a continuous output, meaning that we are trying to map input variables to some continuous function.
    - ex. Given a picture of Male/Female, we have to predict his/her age on the basis of the given picture.
- Classification (分類)
    - we are instead trying to predict results in a discrete output. In other words, we are trying to map input variables into discrete categories
    - ex. Given a patient with a tumor, we have to predict whether the tumor is malignant or benign.

## Unsupervised Learning
### Definition
- Approaching problems with little or no idea what our results should look like.
- We can derive structure from data where we don't necessarily know the effect of the variables.
- We can derive this structure by clustering the data based on relationships among the variables in the data.
- With unsupervised learning there is no feedback based on the prediction results.

### Categories
- Clustering
	- ex. Take a collection of 1,000,000 different genes, and find a way to automatically group these genes into groups that are somehow similar or related by different variables, such as lifespan, location, roles, and so on.
- Non-clustering
	- ex. The "Cocktail Party Algorithm", allows you to find structure in a chaotic environment. (i.e. identifying individual voices and music from a mesh of sounds at a cocktail party).

<br>
***

# Cost Function
## Definition
- summation of the difference between the predicted value and the actual value.
- goal of machine learning to solove problem is, in other words, to minimize a cost function.  
- it is also called "Squared error function" or "Mean squared error".  

## Equasion
![alt cost function equasion](https://i.gyazo.com/f066a90d77bad0d8b2542316861df77b.png)  
- 1/m with Summation: averaging it  
- 1/2 : we rather play with smaller numbers than big numbers  
- If all data(x) are plotted on the hypothesis, cost function = 0.  

## Visual Image
- ex. h(X) = θ0 + θ1 * X  

| 3D plot | Contour plot/figure |
|---------|---------------------|
|<img src="https://i.gyazo.com/4347e6c98c024101a240e1f6e7208642.png" width="300px">|<img src="https://i.gyazo.com/e901d77d8e766e6a119afec072af6ee2.png" width="300px"> |

## Two ways to minimize cost function
- Gradient Descent (any case)  
- Normal Equation (n = # of features < 10,000)  
![](https://i.gyazo.com/b510d29de5bea0ddc79409ce45931df3.png)  

<br>
***

# Gradient Descent
## Definition
- Start with some θ(parameter)
- Keep changing θ to reduce J(θ) until we end up at a minimum
- "Batch" Gradient Descent: Each step of gradient descent uses all the training examples.
![](https://i.gyazo.com/5c6e8801861fc0ebc9b0b19d3a7a814f.png)  

## Algorithm
<img src="https://i.gyazo.com/86926b3a0244cb5db278a378148a247b.png" width="500px">

- As we approach a local minimum, gradient descent will automatically take smaller steps.  
  So, no need to decrease α over time.

## Caution
| correct | incorrect |
|---------|-----------|
|<img src="https://i.gyazo.com/a9175ce0f39c40767004962ab7ff6bd3.png" width="300px"> | <img src="https://i.gyazo.com/1762ffaf7b6ae09411e0f3157f2a6f92.png" width="300px">|

- Gradient descent could be stuck at local optima.  
<img src="https://i.gyazo.com/ac9cce2b5ce7ba1e5c8a919a4f0c93f8.png" width="400px">  

## Technics about efficiency
- make each of input values in roughly the same range to converge efficiently, speedy.  
- ideal range: −1 ≤ x(i) ≤ 1 or −0.5 ≤ x(i) ≤ 0.5  
- Feature Scailing + Mean Normalization:  
<img src="https://i.gyazo.com/56145099674c7dc3f45faedd44486ff7.png">  

### Feature Scaling
- "S" in the formula written above.
- divide the input values by the range (i.e. max - min) of the input variable.  

### Mean Normalization
- "μ" in the formula written above.
- subtract the average value from the values for that input variable.  
- the average of the processed values is 0.  

## Learning Rate
- "α" in the gradient descent formula.  
- If α is too small: slow convergence.  
- If α is too large: ￼may not decrease on every iteration and thus may not converge.  

# Normal Equation
## Definition
- minimize J by explicitly taking its derivatives with respect to the θj ’s, and setting them to zero.  
- This allows us to find the optimum theta without iteration.  
![](https://i.gyazo.com/381287142efae668858ed193372593d2.png)

## Notice
![](https://i.gyazo.com/50a55f6281d9f435e50a5586f669f0b8.png)  

<br>
***

# Linear Regression

| name | logic |
|---------------|---------------------------------------------------------------|
| Model     | <img src="https://i.gyazo.com/4d7f7f6fca419e045b0a4c14e750a6ca.png" width="200px"> |
| Cost Function | <img src="https://i.gyazo.com/5400db40bb8da23cdb0939c7bab9a103.png" width="350px"> |
| Algorithm   | <img src="https://i.gyazo.com/9775573cda8efa7bf8d4a2b6393e255b.png" width="400px"> |

# Linear Regression for Multiple variables
- Every formula is equal.

| description | formula |
|-------------|----------|
| Expanded | <img src="https://i.gyazo.com/584306a72f17284bcd0b4a574fab6b4d.png"> |
| X:column(vector) |<img src="https://i.gyazo.com/2a819590b80e3ee242d8cc06fd715f91.png"> |
| X:row | <img src="https://i.gyazo.com/a03a155d19a1eb38bde03783b59773c9.png"><br><img src="https://i.gyazo.com/86ed1cd4d048691c9f9a0202af00def7.png"> |


## Gradient Descent behind it
- simultaneously update  
<img src="https://i.gyazo.com/0c888d220e8dae92eab6e09d1a3e2bed.png">　


<br>
***

# Binary Classification Problem(0 or 1)
- Logistic Function / Sigmoid Function  

## Hypothesis
- 0 <= h(x) <= 1  
![](https://i.gyazo.com/4cf901384bc146258b9e327daa58d80e.png)  
![](https://i.gyazo.com/37210ef8cdf6f33df84e3e527fb7a734.png)  
![](https://i.gyazo.com/a9da997271fc5e0e7f500bce2983d14d.png)  
![](https://i.gyazo.com/c1c8d2c57f388fc2a3162c886ee7b7c8.png)  

## Key Concept
### Decision Boundary
- In order to get our discrete 0 or 1 classification, we can translate the output of the hypothesis function as follows:  
![](https://i.gyazo.com/5e1b02269535b7c5685f9aaa241cb829.png)

<br>
***

# Appendix
## Expression in equation
| Label         | Definition    |
|:-------------:|---------------|
| x             | input variable, feature |
| y             | output/target variable |
| m             | number of training examples |
| h             | logic(relation) between x and y |
| θ             | parameter in h |
| J             | cost function |
| α             | learning rate |
| ![](https://wikimedia.org/api/rest_v1/media/math/render/svg/786849c765da7a84dbc3cce43e96aad58a5868dc) | real number |

- [Wiki: Table of expressions in math](https://ja.wikipedia.org/wiki/%E6%95%B0%E5%AD%A6%E8%A8%98%E5%8F%B7%E3%81%AE%E8%A1%A8)


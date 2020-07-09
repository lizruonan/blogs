---
title: Difference and Similarities between Gradient Descent and Newton's Method
date: 03 Mar 2020
author: Elizabeth Zhao
tags: [Machine Learning, Mathematics, Linear Algebra]
comments: true
toc: true
---

* #table of content
{: toc}

# Introduction

As we all know, Gradient Descent method is an essential part in machine learning (deep learning) that is used to optimize the distance between predictions and true values. Newton's Method is one of the most well-know root finding algorithms in numerical analysis. Though both methods involve computing the first order derivative, they are independent ideas and cannot be confused. Hence, I'd like to make simple comparisons between Gradient Descent method and Newton's Method.    

*Note:  The first two sections are for the recap of definitions. If you're already familiar with them, please feel free to jump to the [last section](#why-not-newtons-method-in-ml-problems).*



# Newton's Method

Newton's Method is derived from Taylor series approximation of a twice differentiable function $$f$$. 

## Definition (for single variable)

Suppose that $$ f: D\in C^2[a, b] $$, let $$p_0$$ be an approximation of $$p$$ such that $$ f'(p_0) \neq 0$$ and $$abs(p_0 - p)$$ is small.  To find a solution p of $$f(x) = 0$$, the Newton's Method is given by 


$$
g(p_{n-1}) = p_{n-1}  - \frac{f(p_{n-1} )}{f'(p_{n-1} )}, \quad \textrm{for } n \geq 1,
$$
 with $$g(p_{n-1}) = p_n$$ .



* The convergence depends on the initial point $$p_0$$. Since Taylor series converges if $$abs(p-p_0) < \sigma$$, Newton's Method is guaranteed to converge for small $$abs(p - p_0)$$ .
* The bound of the error approximation is also from Taylor's approximation. 



## Definition (for Nonlinear Systems of Equations)



## Newton's Method for Optimization Problems

TBD



# Gradient Descent

Given the *cost function* 
$$
J(\theta) = \frac{1}{2}\sum_{i=1}^m\left(h_{\theta}(x)^{(i)} - y^{(i)}\right)^2
$$
We want to choose $$\theta$$ that minimizes $$J(\theta)$$. 

**Algorithm ($$n\geq 1$$) :**

we pick an initial value of $$\theta$$,

repeat until convergence: {
$$
\theta_j := \theta_j -\alpha \frac{1}{m}\sum_{i=1}^m (h_{\theta}(x^{(i)}) - y^{(i)})\cdot x_j^{(i)} \quad \textrm{for } j:= 0,...,n
$$
}

where $$\alpha$$ is the learning rate.




## Stochastic Gradient Descent (SGD)

TBD



# Why Not Newton's Method in ML problems? 



* Major issues of Newton's Method
* Major issues of Gradient Descent and SGD





# References:

[Introduction to Gradient Descent and Backpropagation Algorithm](https://atcold.github.io/pytorch-Deep-Learning/chapters/02-1/)
---


layout: post
title: Who Is The Winner? Gradient Descent v.s. Newton's Method
date: 03 Mar 2020
author: Elizabeth Zhao
tags: [Machine Learning, Mathematics, Numerical Analysis, Linear Algebra, Convex Optimization]
comments: true
toc: true
---

<!--abstract to make Jekyll stable-->

As we all know, Gradient Descent method is an essential part in machine learning that is used to optimize the distance between predictions and true values. Newton's Method is one of the most well-known root-finding algorithms in numerical analysis. Though both methods involve computing the first order derivative, they are independent ideas and cannot be confused. What are the differences between Gradient Descent and Newton's Method? When to use which of them?

Block math test 
$$
\begin{align*}
y = y(x,t) &= A e^{i\theta} \\
&= A (\cos \theta + i \sin \theta) \\
&= A (\cos(kx - \omega t) + i \sin(kx - \omega t)) \\
&= A\cos(kx - \omega t) + i A\sin(kx - \omega t)  \\
&= A\cos \Big(\frac{2\pi}{\lambda}x - \frac{2\pi v}{\lambda} t \Big) + i A\sin \Big(\frac{2\pi}{\lambda}x - \frac{2\pi v}{\lambda} t \Big)  \\
&= A\cos \frac{2\pi}{\lambda} (x - v t) + i A\sin \frac{2\pi}{\lambda} (x - v t)
\end{align*}
$$

# Difference 1: Rate of Convergence 

Suppose we are given a function $f$ is convex, twice differntiable in $\mathbb{R}^n$, and we want to find the local minimum 

$\min_{x\in \mathbb{R}^n} f(x).$
$$
\min_{x\in \mathbb{R}^n} f(x).
$$

The Gradient Method:

$x_{k+1} = x_k - h_k f'(x_k),\quad h_k > 0$
$$
x_{k+1} = x_k - h_k f'(x_k),\quad h_k > 0
$$

Newton's Method:



$x_{k+1} = x_k - [f''(x_k)]^{-1}f'(x_k)$


$$
x_{k+1} = x_k - [f''(x_k)]^{-1}f'(x_k)
$$
Where $k = 0, 1, 2, 3,...$

We can immediately observe that the rate convergence of gradient method is linear, while the Newton's method is quadratic. 

# Difference 2: Directions

The direction of updating step of Gradient Method follows along the direction of the gradient, while Newton's Method follows along the inverse of second order derivative (or Hessian for a linear system). We'll see from the derivations below. 

Let us approximate $f(x)$ with the following:

$\phi_G(x) = f(\bar x) + \left<	\nabla f(\bar{x}), x-\bar{x}\right> + \frac{1}{2h}\left\Vert x-\bar x \right\Vert^2,$
$$
\phi_G(x) = f(\bar x) + \left<	\nabla f(\bar{x}), x-\bar{x}\right> + \frac{1}{2h}\left\Vert x-\bar x \right\Vert^2,
$$
where $h >0$. 
$$
\implies \phi_G'(x_G^*) = \nabla f(\bar x) + \frac{1}{h}(x_G^*-\bar x) = 0
$$
Then, the minimum of the function is
$$
x^*_G = \bar x - h \nabla f(\bar x)
$$
Thus, this is the iterate of Gradient Method. 

---

Newton's Method is derived from Taylor Series Approximation of a twice differentiable function $$f$$. Let us approximate $f(x)$:
$$
\phi_N(x) = f(\bar{x}) + \left<	\nabla f(\bar{x}), x-\bar{x}\right> + \frac{1}{2}\left<	\nabla^2 f(\bar{x})(x-\bar{x}), x-\bar{x}\right>
$$

$$
\implies \phi_N'(x_N^*) = \nabla f(\bar x) +  \nabla f(\bar x)(x_N^*-\bar x) = 0
$$

The minimum of the function is
$$
x_N^* = \bar x - \left[	\nabla^2f(\bar x)\right]^{-1} \nabla f(\bar x)
$$
Therefore, we got the iterate of Newton's Method.

---

Recall the inner product between $x$ and $y$, 
$$
\left< x, y \right> = \sum_{i=1}^n x^{(i)}y^{(i)}, \quad \textrm{where} \quad x, y \in \mathbb{R}^n\\
\left\Vert x \right\Vert = \sqrt{\left< x, x \right>}
$$
The gradient by definiton is 
$$
f(x+h) = f(x) + \left< \nabla f(x), h \right> + o(\Vert h\Vert)
$$


The coordinate representation of the gradient is
$$
\nabla f(x) = \left(\frac{\part f(x)}{\part x^{(1)}}, \frac{\part f(x)}{\part x^{(2)}}, ..., \frac{\part f(x)}{\part x^{(n)}}\right)^T.
$$

> The root gradient comes from the Latin word gradi, meaning “to walk”. In this sense, the gradient of a surface is the rate at which it “walks uphill” [3].

---

The figure below is an example of the convergence of the Gradient Method (black curve) and Newton's Method (blue curve. However, Newton's Method converges much faster than Gradient Method by taking a different direction. 

<img src="https://i.loli.net/2020/09/10/3yn7vBqNaGzD8kU.png" alt="Screen Shot 2020-09-09 at 4.48.43 PM.png" style="zoom:50%;" />

The figure above uses the function $f(x)= (10x_1^2 + x_2^2)/2 + 5\log(1 + e^{-x_1-x_2})$ [[2]] [2].

# Difference 3: Operation Time 

At each step of iteration of Newton's Method, we want to compute the Hessian of a $n \times n$ matrix of $f$, this will cost $O(n^2)$ time to compute. The operation time of Gradient Method, however, is $O(n)$ time. If n is a very large number, e.g. n = 1 million, then Newton's Method is computationally expensive. 

Moreover, Newton's Method converges by one step for a quadratic function.

Consider a quadratic function
$$
f(x) = \alpha + \left<a, x\right> + \frac{1}{2}\left<Ax, x\right>
$$
where $A$ is a symmetric positive definite $n \times n$ matrix.

So
$$
\nabla f(x) = a + Ax\\
	\nabla^2 f(x) = A
$$
Then, the minimum of the function is 
$$
x^* =-A^{-1}a
$$
We can then see that the direction of Newton's Method at some $x \in \mathbb{R}^n$ is
$$
d_N(x)= \left[	\nabla^2 f(x)\right]^{-1}	\nabla f(x)= A^{-1}(a+ Ax) = x + A^{-1}a
$$
At some $x \in \mathbb{R}^n$, 
$$
x - d_N(x) = -A^{-1}a = x^*
$$
Therefore, we can close the conclusion by above.

# Gradient Descent

## Batch Gradient Descent 

The scheme of batch GD  is to compute the loss for every element in a dataset, then update the parameter by the mean of loss until the loss function converges to the minimum.

Given the lost function
$$
J(\theta) = \frac{1}{2}\sum_{i=1}^m\left(h_{\theta}(x)^{(i)} - y^{(i)}\right)^2
$$



We want to choose $\theta$ that minimizes $$J(\theta)$$. 

**Algorithm ($n\geq 1$) :**

We pick an initial value of $\theta$,

repeat until convergence: {


$$
\theta_j := \theta_j -\alpha \frac{1}{m} \sum_{i=1}^m \frac{\partial J(\theta)}{\partial \theta_j} \quad \textrm{for } j= 0,...,n\\
\implies \theta_j := \theta_j -\alpha \frac{1}{m}\sum_{i=1}^m (h_{\theta}(x^{(i)}) - y^{(i)})\cdot x_j^{(i)} \quad \textrm{for } j:= 0,...,n
$$


}

where $\alpha$ is the learning rate.

# References

[1]: https://see.stanford.edu/materials/aimlcs229/cs229-notes1.pdf)	"Lecture Notes of CS229 - Learning Regression, Classification and Logistic Regression, Generalized Linear Models"
[2]: http://www.stat.cmu.edu/~ryantibs/convexopt-S15/lectures/14-newton.pdf	"Lecture Notes of Convex Optimization 10-725: Newton's Method"
[3]: 	"Burden, R. L., &amp; Faires, J. D. (2011). *numerical analysis*."
[4]: 	"Nesterov, Yurii. (2004). *Introductory Lectures on Convex Optimization, A Basic Course*."


---
layout: post
title: Orthogonal Complement of Column Space - The Big Picture Of Linear Algebra
date: 2020-02-15
author: Elizabeth Zhao
tags: [Mathematics, Linear Algebra]
comments: true
toc: true
---


# Introduction

I came across a theorem when struggling with one of the problems from my linear algebra written exam [link](https://math.nyu.edu/student_resources/wwiki/index.php?title=Linear_Algebra:_2011_September:_Problem_4 "problem link").  Besides from the determinant of block matrix, which I will talk later in another post, the theorem plays an essential role in the linked problem. Here is the theorem below: 


# Fundamental Theorem of Orthogonality:
Let $$A$$ be a $$m \times n$$ matrix. Then, 

$$Nul(A^T) = Col(A)^{\perp}$$

In other words, the column space contains every vector that is orthogonal to left nullspace (in $$\mathbb{R}^m$$);

Equivalently, 

$$Nul(A)^{\perp} = Col(A^T)$$

I.e., the row space contains every vector that is orthogonal to the nullspace (in $$\mathbb{R}^n$$). 

Before we see the mathematical proof of the theorem, we shall think about the theorem in an intuitive sense:
$$Ax = b$$ then $$b$$ is in the column space, which then implies b is perpendicular to the left nullspace. 

The above theorem also leads us to the following fundamental theorem:

## Rank-Nullity Theorem:
$$dim(Col(A)) + dim(Nul(A)) = n$$

![big_pic_LA.png](https://i.loli.net/2020/02/17/dIbniEk6NwHVf7h.png) "Strang, G. "Linear Algebra And Its Applications 4th Ed". Chapter 3.1. New York, Academic Press. 2006."

## Examples:
The figures below are generated in MATLAB: 

The orthogonal complement of a 2-d plane spanned by two vectors is a line of a vector in 3-d space.

![orthog.png](https://i.loli.net/2020/03/04/rVwohXjJvAzLPcs.png)

Likewise, the orthogonal complement of a single vector is a 2-d plane in 3-d space. 

![orthog2.png](https://i.loli.net/2020/03/04/j7aGdwlhtPLZros.png)

Now, let us see the proof (it is very straightforward, and you can do on your own and compare):


# Proof of the theorem

$$(\subseteq)$$ let $$x\in Col(A)$$, then $$x = a_1v_1+a_2v_2+...+a_nv_n, $$ where $$a_1, a_2, ..., a_n$$ are columns of $$A$$, and $$v_1, v_2,..., v_n$$ are the entries of some vector $$v$$.  

WTS:  $$x\perp w$$,  where $$w\in Nul(A^T)$$. 

$$
x\cdot w = x^T w \\
= (a_1v_1+...+a_nv_n)^T w\\
=(a_1v_1)^T w+...+(a_nv_n)^T w \\
= v_1(a_1^Tw) +...+v_n(a_n^Tw)\\
= v_1(0)+...+v_n(0)\\
= 0 \\
$$

$$\implies x \perp w, \forall w \in Nul(A^T)$$
$$\implies x\in Nul(A^T)^{\perp}$$

$$(\supseteq)$$ let $$w\in Nul(A^T)$$. Then

$$a_j^Tw = a_j\cdot w = 0, \forall j = 1,2,...,n$$.

By the definition of orthogonal complement, $$w \in Col(A)^{\perp}$$. 

We're done！$$\Box$$

To Be Continued...

# References

Margalit, D., Rabinoff, J. "Interactive Linear Algebra". Web. Chapter 6.2. <https://textbooks.math.gatech.edu/ila/orthogonal-complements.html> 

Strang, G. "Linear Algebra And Its Applications 4th Ed". New York, Academic Press. 2006.

---
layout: post
title: What is the expected number of coin flips until you get two heads in a row?
---

## Example

Suppose we toss a fair coin, what is the expected number of tosses until we get two heads in a row?

I'll show three ways of solving this problem.

## Method I: Recursive expectation in two steps

Let \\(X\\) be the number of tosses until we get two heads in a row, then 

$$ \begin{align}
& \mathbb{E}\left[X\right] & = \frac{1}{2}\mathbb{E}\left[X\vert T\right]+\frac{1}{4}\mathbb{E}\left[X\vert HT\right]+\frac{1}{4}\mathbb{E}\left[X\vert HH\right] \\
& & = \frac{1}{2}\left(1+\mathbb{E}\left[X\right]\right)+\frac{1}{4}\left(2+\mathbb{E}\left[X\right]\right)+\frac{1}{4}\cdot 2 \\
\Rightarrow & \mathbb{E}\left[X\right]=6.
\end{align} $$

\\( a \ne 0 \\)

![](/images/two_steps_tree.png?raw=true)

![](/images/two_steps_transition.png?raw=true)
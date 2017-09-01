---
layout: post
title: Expected Number of Coin Flips until Two Heads in a Row
---

## Example

Suppose we toss a fair coin, what is the expected number of tosses until we get two heads in a row?

I'll show three ways of solving this problem.

## Method I: Recursive Expectation in Two Steps

Let \\(X\\) be the number of tosses until we get two heads in a row, then we can solve \\( \mathbb{E}\left[X\right] \\) as follows:

$$ \begin{align}
& \mathbb{E}\left[X\right] = \frac{1}{2}\cdot \mathbb{E}\left[X\vert T\right]+\frac{1}{4}\cdot \mathbb{E}\left[X\vert HT\right]+\frac{1}{4}\cdot \mathbb{E}\left[X\vert HH\right] \\
\Rightarrow & \mathbb{E}\left[X\right] = \frac{1}{2}\cdot \left(1+\mathbb{E}\left[X\right]\right)+\frac{1}{4}\cdot \left(2+\mathbb{E}\left[X\right]\right)+\frac{1}{4}\cdot 2 \\
\Rightarrow & \mathbb{E}\left[X\right]=6.
\end{align} $$

This recursive relation can be better explained by the probabilistic tree below:
![](/images/two_steps_tree.png?raw=true)

For those who know [Markov chains](https://en.wikipedia.org/wiki/Markov_chain), we can also draw a state transition diagram as follows:
![](/images/two_steps_transition.png?raw=true)

## Method II: Recursive Expectation in One Step

$$ \begin{align}
& \left\{
\begin{array}
[c]{l}
\mathbb{E}\left[X\right] = \frac{1}{2} \cdot \mathbb{E}\left[X\vert H\right] + \frac{1}{2}\cdot \left(1+\mathbb{E}\left[X\right]\right) \\
\mathbb{E}\left[X\vert H\right] = \frac{1}{2}\cdot 2 + \frac{1}{2}\cdot \left(2+\mathbb{E}\left[X\right]\right)
\end{array}
\right. \\
\Rightarrow & \begin{array}
[c]{l}
\mathbb{E}\left[X\right] = 6 \\
\mathbb{E}\left[X\vert H\right] = 4
\end{array}
\right.
\end{align} $$

![](/images/one_step_tree.png?raw=true)

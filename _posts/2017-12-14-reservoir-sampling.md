---
layout: post
title: Reservoir Sampling
---

How to randomly and uniformly smaple k items out of a population (of an unknow size)?

Imagine a scenario: a gate keeper of a part stands at the entrance of the park, and this keeper will give away k free tickets to customers during this day. The keeper wants each customer coming today have an equal chance of getting a free ticket, yet this keeper doesn't know how many customer would come this day. This is exactly the practical sampling problem we are trying to solve. 

Indeed, it is not easy to come up with such a [randomized algorithm](https://en.wikipedia.org/wiki/Randomized_algorithm). Let's go to see the algorithm first and then try to figure out how it works.

``` python
import random
def sample(iterable, n)
"""
Returns n random items from iterable (of unknown size)
"""
reservoir = []
for t, item in enumerate(iterable):
  if t<n:
    reservoir.append(item)
  else:
    m = random.randint(0,t)
    if m<n:
      reservoir[m] = item
return reservoir
```

## Proof Idea:

Suppose there are \\(N\\) items in total (Remember we don't know \\(N\\) a priori).

If \\(k\leq N\\), each of k items will be selected in the reservoir for sure. The more interesting case is when \\(k\geq N\\).

The **key observation** is that: at the \\(i\\)th iteration (\\(i=n+1,n+2,\cdots,N\\)) of the algorithm, each item has probability \\(n/i\\) of being in the reservoir.

Then, we can use **induction** to prove that in the end, each item has probability \\(n/N\\) of being in the reservoir. The details of the inductive proof are left to the readers.

---
layout: post
title: Reservoir Sampling
---

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

Suppose there are \\(N\\) items in total.

The key observation is that at the \\(i\\)th iteration (\\(i=n+1,n+2,\cdots,N\\)), each item has probability \\(n/i\\) of being in the reservoir.

Then, we can use **induction** to prove that in the end, each item has probability \\(n/N\\) of being in the reservoir.

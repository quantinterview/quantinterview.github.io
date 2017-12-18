---
layout: post
title: Reservoir Sampling
---

some random code, to be replaced

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

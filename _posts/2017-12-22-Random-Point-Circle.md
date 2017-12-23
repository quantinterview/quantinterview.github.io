---
layout: post
title: How to generate random points uniformly on a circle?
---

![](/images/random_point_on_circle.png?raw=true)

{% highlight python linenos %}
  import numpy as np
  import matplotlib.pyplot as plt

  plt.close("all")

  # setup
  Nmax = 1000
  R = 5

  # wrong method
  r1 = R * np.random.rand(Nmax, 1)
  theta1 = 2 * np.pi * np.random.rand(Nmax, 1)
  x1 = r1 * np.cos(theta1)
  y1 = r1 * np.sin(theta1)

  # right method
  # pdf_r(r)=(2/R^2) * r
  # cumulative pdf_r is F_r = (2/R^2)* (r^2)/2
  # inverse cumulative pdf is r = R*sqrt(F_r)
  r2 = R * np.sqrt(np.random.rand(Nmax, 1))
  theta2 = 2 * np.pi * np.random.rand(Nmax, 1)
  x2 = r2 * np.cos(theta2)
  y2 = r2 * np.sin(theta2)

  # plot
  plt.subplot(121)
  plt.plot(x1,y1,'r.')
  plt.xlim((-1.1*R,1.1*R))
  plt.ylim((-1.1*R,1.1*R))
  plt.title('Wrong')
  plt.axis('square')

  plt.subplot(122)
  plt.plot(x2,y2,'g.')
  plt.xlim((-1.1*R,1.1*R))
  plt.ylim((-1.1*R,1.1*R))
  plt.title('Right')
  plt.axis('square')

  plt.show()

  plt.savefig("random_point_on_circle", bbox_inches='tight')
{% endhighlight %}

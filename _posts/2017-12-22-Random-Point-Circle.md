---
layout: post
title: How to generate random points uniformly on a circle of radius R?
---

## Method I: Polar Coordinates

![](/images/polar_coordinates.png?raw=true)

[Source](https://www.khanacademy.org/computing/computer-programming/programming-natural-simulations/programming-angular-movement/a/polar-coordinates)

**A naive first thought:** Oh, we might just generate a uniform random radius \\(r\in [0,R]\\) and a uniform random angle \\(\theta\in [0,2\pi]\\), and we are basically done?

However, if we simulate using this naive method, we will see that points clustered around the center of the circle, as shown in the left picture below:

![](/images/random_point_on_circle.png?raw=true)

Something must be wrong.

**Key intuition**: for a certain angle interval \\([\theta, \theta+d\theta]\\), there needs to be more points generated further out (at large \\(r\\)) than close to zero.

Recall that, in polar coordinates, the infinitesimal area is \\(rdrd\theta\\).

Then, the pdf of \\(r\\) should be proportional to \\(r\\). Actually, it is \\(f(r)=\frac{2}{R^2}r\\) due to normailization.

Now, we can use the inverse cdf to generate \\(r\\):

$$ \begin{equation}
r = R * \text{sqrt}( \text{rand()} )
\end{equation} $$

where \\(\text{rand()}\\) is a uniformly distributed random number in \\([0,1]\\).

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

## Method II: Limit Of Shrinking Triangles

![](/images/limiting_triangles.png?raw=true)

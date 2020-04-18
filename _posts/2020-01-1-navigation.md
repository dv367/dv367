---
layout: post
title: "4. Navigation Potential Functions"
mathjax: true
comments: true
description: "Turtlebot3"
keywords: "Turtlebot3"
---  

### 4.1 Escape Local Minimas?  
We saw in the previous post that the overall potential function consists of multiple local minimas. One way to avoid is by using **Radnomized Path Planner (RPP)**. In this, series of random walks are initiated when the robot is stuck in the local minima. Another way can be using **Navigation Potential Function** which consists of only one minima which is at $q_{goal}$. This post will be focussed on Navigation Potential Function. More info about **RRP** can be found [here](https://www.cs.rice.edu/CS/Robotics/papers/barraquand1997rand-sample-scheme-journal.pdf)
  
    
Before moving on further, lets discuss about _Hessian_ matrix. Suppose a potential function $\nabla U(q)$ has a critical point at $q^{\dagger}$ i.e $\nabla U(q^{\dagger}) = 0$. The point $q^{\dagger}$ is either maximum, minimum or saddle point(**Figure 4.1**).One can look at the second derivative to determine the type of critical point. For real-valued functions, this second derivative is the _Hessian_ matrix.   

<p align="center">
$$\left[
    \begin{matrix}
    \frac{\partial^{2}U}{dq^{2}_{1}} & \cdots  & \frac{\partial^{2}U}{\partial q_{1} \partial q_{n}} \\
    \vdots & \ddots & \vdots \\
    \frac{\partial^{2}U}{\partial q_{n} \partial q_{1}} & \cdots & \frac{\partial^{2}U}{dq^{2}_{n}} \\
    \end{matrix}
\right]$$
</p> 
When the Hessian matrix is   
 * non-singular, then $q^{\dagger}$ is non-degenerate(isolated).  
 * positive-definite, then $q^{\dagger}$ is local minimum.           
 * negative-definite, then $q^{\dagger}$ is local maximum.  
  
![minmaxsad]({{ site.url }}/assets/images/minmaxsaddle.png)   
<p align="center">
Figure 4.1 Minimum, Maximum, Saddle
</p> 

### 4.2 Navigation Potential Function  
As stated above, navigation potential function have one local minima. The formal definition is as follows:  
A function $\varphi$ : $Q_{free} \to [0,1]$ is called navigation potential if it  
* is smooth (or atleast $C^{k}$ for $k \geqslant 2$ [continous dervatives](https://en.wikipedia.org/wiki/Smoothness))
* has unique minimum at $q_{goal}$ in the connected component of free space that contains $q_{goal}$
* is uniform maximal on the boundary of the free space
* is [Morse](http://web.cse.ohio-state.edu/~wang.1016/courses/788/Lecs/lec10-brian.pdf)  
A morse function is one whose critical point($\frac{d}{dx}f(x) = 0$) are all non-degenrate i.e they are isolated.

### 4.3 Sphere Space
This approach intially assumes that the configuration space is bounded by a sphere centered at $q_{0}$ and has _n_ $dim(Q_{free})$-dimensional spherical obstacles centered at $q_{1},q_{2},....q_{n}$. The repulsive function is defined as  
<p align="center">
$\beta_{0}(q) = -d^{2}(q,q_{0}) + r^{2}_{0} \tag{1}$
<br>
$\beta_{i}(q) = d^{2}(q,q_{i}) - r^{2}_{i} \tag{2}$
<br>
where $r_{i}$ is the radius of $i^{th}$ sphere.
</p>



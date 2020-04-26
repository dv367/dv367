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
 One can refer this [wiki](https://en.wikipedia.org/wiki/Definiteness_of_a_matrix) for matrix properties. 
  
![minmaxsad]({{ site.url }}/assets/images/minmaxsaddle.png)   
<p align="center">
Figure 4.1 Minimum, Maximum, Saddle
</p> 

### 4.2 Navigation Potential Function  
As stated above, navigation potential function have one local minima. The formal definition is as follows:  
A function $\varphi$ : $Q_{free} \to [0,1]$ is called navigation potential if it  
* is smooth (or atleast $C^{k}$ for $k \geqslant 2$ [continous derivatives](https://en.wikipedia.org/wiki/Smoothness))
* has unique minimum at $q_{goal}$ in the connected component of free space that contains $q_{goal}$
* is uniform maximal on the boundary of the free space
* is [Morse](http://web.cse.ohio-state.edu/~wang.1016/courses/788/Lecs/lec10-brian.pdf)  
A morse function is one whose critical point($\frac{d}{dx}f(x) = 0$) are all non-degenrate i.e they are isolated.

### 4.3 Sphere Space
This approach intially assumes that the configuration space is bounded by a sphere centered at $q_{0}$ and has _n_ $dim(Q_{free})$-dimensional spherical obstacles centered at $q_{1},q_{2},....q_{n}$. The spheres are assumed to be disjoint. The repulsive function is defined as  
<p align="center">
$\beta_{0}(q) = -d^{2}(q,q_{0}) + r^{2}_{0} \tag{1}$
<br>
$\beta_{i}(q) = d^{2}(q,q_{i}) - r^{2}_{i} \tag{2}$
<br>
where $r_{i}$ is the radius of $i^{th}$ sphere.
</p>  
The overall repulsive function is written as the multiplication of every sphere, 
<p align="center">  
${\displaystyle \prod_{i=0}^{n} \beta_{i}(q)} \tag{3}$
</p>  
The repulsive function of $i^{th}$ sphere at the boundary is **zero**, **positive** inside the boundary and **negative** outside the boundary. However, for the $0^{th}$ it is **positive** outside the boundary and **negative** inside the boundary. We can think of a disc of some thickness removed from a solid block. Now, imagine a robot is kept in that empty space or impression indicating the configuration space the robot has to work in. Next, the attractive function is defined as
<p align="center">  
$\gamma_{k} = (d(q,q_{goal}))^{2k} \tag{4}$
  <br>
where $k$ is a positive number.
</p>  
<div class="divider"></div>
**Key Points:**
* the value of $\gamma_{k}$ is zero at goal.
  
* $\frac{\gamma_{k}}{\beta}$ tends to $\infty$ as $q$ approaches boundary of an obstacle.
  
* For large value of $k$, $\frac{\gamma_{k}}{\beta}$ has a unique minimum. As gradient $\frac{\partial \gamma_{k}}{\partial q}$ dominates  $\frac{\partial \beta}{\partial q}$.
  
* increasing the value of $k$ causes other minimas to gravitate towards boundary of the obstacle and the range of repulsive influence of obstacle becomes small relative to attractive fucntion.
  
* only the nearby obstacle will have significant effect on value of $\frac{\gamma_{k}}{\beta}$.
  
* therefore, only opportunity of local minima appear on the radial line of obstacle and goal.(One may refer to **Figure 3.7** in previous post)
  
* for a **very** large value of $k$, Hessian matrix can be positive definite. Therefore, only one minima can be at goal which is infact the global minima. 
<div class="divider"></div>
Now, we need to do some scaling as $\frac{\gamma_{k}}{\beta}$ can have any arbitary values. The following equation is called an analytical switch. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![switch]({{ site.url }}/assets/images/switch.PNG) 
<p align="center">
Figure 4.2 Analytical Switch  
</p>
<br>
<p align="center">
$\sigma_{\lambda}(x) = \frac{x}{\lambda + x} \tag{5}$ 
</p>

Lets see how this switch limits a given function. Take an example of $y = x^{2} $ and observe the **Figure 4.3**. _Note: It is not scaled to graph._  

![example]({{ site.url }}/assets/images/example.PNG)  
<p align="center">
Figure 4.3 Analytical switch limiting the function  
</p>  

We can now apply the same on the function $\frac{\gamma_{k}}{\beta}$. The function $s(q,\lambda)$ has a zero value at goal, unitary at boundary of an obstacle, and varies continuously in free space. 
<p align="center">
$s(q,\lambda) = (\sigma_{\lambda} \circ \frac{\gamma_{k}}{\beta})(q) = \frac{\gamma_{k}}{\lambda \beta + \gamma_{k}}(q) \tag{6}$
</p>
It has a unique minimum at for a large enough value of $k$. However, this is still not necessarily a Morse function. So, we introduce another function to sharpen $s(q,\lambda)$. This sharpening function is 
<p align="center">
$\xi_{k} = x^\frac{1}{k} \tag{7}$
<br>  
$\varphi(q) = (\xi_{k} \circ \sigma_{\lambda} \circ \frac{\gamma_{k}}{\beta})(q) = \frac{d^2(q,q_{goal})}{[(d(q,q_{goal}))^{2k} + \lambda \beta(q)]^\frac{1}{k}} \tag{8}$  
</p>

![navi]({{ site.url }}/assets/images/navi.jpg)  
<p align="center">
Figure 4.4 Visualization of navigation function with five obstacles for $k=3,4,5,6,7,8,10$  
</p>
The effect of increasing $k$ can be seen in the **Figure 4.4**. For $k=10$, $\varphi$ has one minima which is at goal.

### 4.4 Implementation  
Similar to our previous post, the velocity can be considered as gradient of this function. Before that, we need to determine the value of $\lambda$. The value of $\lambda$ should be such that,
<p center="align">
$\frac{\lambda \beta}{\gamma_{k}} << 1 \tag{9}$ 
</p>
The value of $\gamma_{k}$ will be maximum on the boundary with its line segment to goal passing through the center of $0^{th}$ obstacle. With the same boundary point, we can further calculate the value of $\beta(q)$. Finally, the value of $\lambda$ can be calculated as,
<p center="align">
$ \lambda = |\gfrac{\beta^{\dagger}}{\gamma^{\dagger}_{k}}| \epsilon \tag{10}$   
$where, \epsilon = 1e-25$
</p> 
The value of $\epsilon$ was obtained by experimental analysis. 

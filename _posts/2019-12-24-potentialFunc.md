---
layout: post
title: "3. Potenial Functions"
mathjax: true
comments: true
description: "Turtlebot3"
keywords: "Turtlebot3"
---  

## 3.1 Basic Idea  
Potential function approach directs a robot as if it were a particle moving in a gradient vector field. Gradients can be viewed as forces acting on a positively charged particle robot attracted by negatively charged goal. Obstacles are also positively charged which forms a repulsive force directing the robot away from it.   

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![obstacle]({{ site.url }}/assets/images/charged.png)  

<p align="center">
Figure 1. -ve goal attarcts +ve robot
</p>  
A potential function can be constructed as the sum of attractive and repulsive potenials.  
<p align="center">
$U(q) = U_{att}(q) + U_{rep}(q) \tag{1}$
</p>  
We will consider the gradient of the potential function as a velocity vector($\vec{v}$).
<p align="center">
$v = -\nabla U(q) \tag{2}$
</p> 
_Note: The function must be continuously differentiable._ 

### 3.2 Attractive Potential  
The simplest attractive potential function is one that grows quadratically with the distance to goal. $\zeta$ is a parameter used to scale the effect of the attractive potential function and $d^{2}(q,q_{goal})$ is the distance from current configuration $q$ to goal goal configuration $q_{goal}$.   
<p align="center">
$U_{att}(q) = \frac{1}{2}\zeta d^{2}(q,q_{goal}) \tag{3}$
</p>  
In Figure 2, we can observe that as we move closer towards the goal the energy decreases and becomes zero at the goal. The velocity vector can be found from the equation(2).  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![att]({{ site.url }}/assets/images/attractive.png)   
<p align="center">
Figure 2. Attractive Potential Function $goal: (500,500)$
</p> 
As discussed in the earlier post that our robot can move only in plane. From eqn(2), we can write
<p align="center">
$\vec{v} = \zeta (x_{g}-x) \hat{i} + \zeta (y_{g}-y) \hat{j}
</p> 


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
The simplest attractive potential function is one that grows quadratically with the distance to goal. Let $\zeta$ be a parameter used to scale the effect of the attractive potential function and $d^{2}(q,q_{goal})$ is the distance from current configuration $q$ to goal configuration $q_{goal}$.   
<p align="center">
$U_{att}(q) = \frac{1}{2}\zeta d^{2}(q,q_{goal}) \tag{3}$
</p>  
In Figure 2, we can observe that as we move closer towards the goal the energy decreases and becomes zero at the goal. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![att]({{ site.url }}/assets/images/attractive.png)   
<p align="center">
Figure 2. Attractive Potential Function $goal: (500,500)$
</p> 
As discussed in the earlier post that our robot can move only in plane. From eqn(2), we can write
<p align="center">
$\vec{v} = \zeta (x_{g}-x) \hat{i} + \zeta (y_{g}-y) \hat{j}. \tag{4}$  
</p> 
The agrument $\theta$ of the vector can be given by
<p align="center">
$\theta = atan2(y_{g}-y,x_{g}-x). \tag{5}$
</p>
The magnitude of the vector can be given by
<p align="center">
$|v| = \zeta \sqrt{(x_{g}-x)^{2} + (y_{g}-y)^{2}} \tag{6}$  
$or$
$|v| = \zeta d^{2}(q,q_{goal}). \tag{7}$  
</p>
We can find the value of $\zeta$ by subsituting the $|v|$ as maximum linear velocity of robot and $d^{2}(q,q_{goal})$ as the distance from start configuration $q_{start}$ to the goal configuration $q_{goal}$. Therefore,
<p align="center">
$\zeta = \frac{|v_{max}|}{d^{2}(q,q_{goal})}. \tag{8}$  
</p>  
  
### 3.3 Repulsive Potential    
The repulsive potential keeps the robot away from the obstacles. It is usually defined in terms of how close the robot is to the obstacle. Here, we will only consider the effect of the nearest obstacle. Let $D(q)$ be the distance from the robot's current position  to the nearest obstacle and $Q^{\dagger}$ be tolerance which allows the robot to ignore the obstacle. The function is defined as    
<p align="center">
 $U_{rep}(q)$ =
\begin{cases}
\frac{\eta}{2} (\frac{1}{D(q)} - \frac{1}{Q^{\dagger}})^{2},  & \text{$D(q) \leqslant Q^{\dagger}$} \\  
0, & \text{$D(q) > Q^{\dagger}$} $\tag{9}$ 
\end{cases} 
</p>


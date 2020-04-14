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
The repulsive potential keeps the robot away from the obstacles. It is usually defined in terms of how close the robot is to the obstacle. Here, we will only consider the effect of the nearest obstacle. Let $D(q)$ be the distance from the robot's current position $(x,y)$  to the nearest point $(x_{o},y_{o})$ on obstacle and $Q^{\dagger}$ be tolerance which allows the robot to ignore the obstacle. The function is defined as    
<p align="center">
 $U_{rep}(q) =
\begin{cases}
\frac{\eta}{2} (\frac{1}{D(q)} - \frac{1}{Q^{\dagger}})^{2},  & \text{$D(q) \leqslant Q^{\dagger}$} \\  
0, & \text{$D(q) > Q^{\dagger}$} \tag{9}
\end{cases} $
</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![att]({{ site.url }}/assets/images/repulsive.png) 
<p align="center">
Figure 3. Repulsive Potential Function - two cylindrical obstacles
</p> 
Also,
<p align="center">
 $\vec{v} = - \nabla U_{rep}(q) =
\begin{cases}
- \eta (\frac{1}{D(q)} - \frac{1}{Q^{\dagger}}) \frac{1}{D^{2}(q)} \nabla D(q),  & \text{$D(q) \leqslant Q^{\dagger}$} \\  
0, & \text{$D(q) > Q^{\dagger}$} \tag{10}
\end{cases} $
<br>  
$where, \nabla D(q) = \frac{(x_{o}-x)^{2}}{D(q)} \hat{i} + \frac{(y_{o}-y)^{2}}{D(q)} \hat{j} \tag{11} $
</p>
Similar to eqn(5) the argument $\phi$ is given by
<p align="center">
$\phi = atan2(y - y_{o},x - x_{o}). \tag{12}$
</p>
One should be very careful while calculating the argument of the vector as we require an angle from point $D(x_{o},y_{o})$ to point $P(x,y)$. Figure 4 should make this more clear. _Note: atan2 gives quadrant specific angles_ 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![example]({{ site.url }}/assets/images/example.png)
<p align="center">
Figure 4. Only nearest obstacle is considered
</p>
Similar to eqn(6) the magnitude is given by  
<p align="center">
$|v| = |\eta (\frac{1}{Q^\dagger} - \frac{1}{D(q)}) \frac{1}{D^{2}(q)} \nabla D(q)|. \tag{13}$
<br>
$\because |\nabla D(q)| = 1 \tag{14}$
<br>  
$|v| = |\eta (\frac{1}{Q^\dagger} - \frac{1}{D(q)}) \frac{1}{D^{2}(q)}| \tag{15}$  
</p>
Now, the value of $\eta$ can be calculated when $D(q)$ is minimum. One may think $D(q)$ to be zero which is not practically possible as the $360^{\circ}$ LIDAR or any other sensor has some minimum and maximum value. For our case, the minimum distance the laser can sense is $0.12m$. Plugging the value of $D(q)$ as $0.12m$ and $|v|$ as $|v_{max}|$, we can calculate the value of $\eta$.  
From Figure 5, we can now observe the overall potential function $U(q)$.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![att]({{ site.url }}/assets/images/overall.png) 
<p align="center">
Figure 5. Potential Function (Att + Rep)
</p>  

### 3.4 Results
Figure 6 is the simulation result with following environment configuration:  

* Start = $S(0,0)$  
* Goal = $G(500,500)$  
* Cylindrical obstacle at $(100,130)$ and $(330,270)$ with raidus of $20cm$  
* Radius of robot = $20cm$  
* $Q\dagger = 30cm$  

_Note: The robot can reach the goal with any orientation_
![test]({{ site.url }}/assets/images/test.png) 
<p align="center">
Figure 6. Results
</p>  
**Video:**  

<iframe width="610" height="344" src="https://www.youtube.com/embed/a_e5wqz2nfw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

One might have observed in the video that the robot struggled to move when it was near the second obstacle.

### 3.5 The Local Minima Problem



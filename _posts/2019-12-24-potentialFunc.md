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

### 3.2 Attractive Potential  
The simplest attractive potential function is one that grows quadratically with the distance to goal.  
<p align="center">
$U_{att}(q) = \frac{1}{2}\zeta d^{2}(q,q_{goal}) \tag{2}$
</p>



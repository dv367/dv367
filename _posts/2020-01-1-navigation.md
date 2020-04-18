---
layout: post
title: "4. Navigation Potential Functions"
mathjax: true
comments: true
description: "Turtlebot3"
keywords: "Turtlebot3"
---  

## Espace Local Minimas?  
We saw in the previous post that the overall potential function consists of multiple local minimas. One way to avoid is by using **Radnomized Path Planner (RPP)**. In this, series of random walks are initiated when the robot is stuck in the local minima. Another way can be using **Navigation Potential Function** which consists of only one minima which is at $q_{goal}$. This post will be focussed on Navigation Potential Function. More info about **RRP** can be found here[[^1]].  

### References  
[^1] [1]. _A Random Sampling Scheme for Path Planning -_ [link](https://www.cs.rice.edu/CS/Robotics/papers/barraquand1997rand-sample-scheme-journal.pdf)

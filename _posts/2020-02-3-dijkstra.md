---
layout: post
title: "6. Greedy Search and Dijkstra"
mathjax: true
comments: true
description: "graph based planning"
keywords: "greedy, dijkstra, graph based planning"
---  

### 6.1 Again, some terminologies!
* **$Star(n)$** - represents set of nodes which are adjacent to n.
* **$c(n_1,n_2)$** - is the length of edge connecting $n_1$ and $n_2$.
* **$O$** - open set(priority queue)
* **$C$** - closed set(all processed nodes)
* **$h(n)$** - heuristic cost function, which returns the estimated cost of the shortest path from $n$ to $q_goal$.
* **$g(n)$** - is the total length of **backpointer** path from $n$ to $q_{start}$
* **$f(n)$** - is the estimated cost of shortest path from $q_{start}$ to $q_{goal}$ via $n$.

### 6.2 Greedy!
As we saw in the previous post, the wave-front planner doesn't take any advantage of the prior information about the start/goal position. Let us make the search a bit greedy by expanding/exploring nodes based on distance to goal i.e. node which is closer to goal are given more priority. This makes the search greedy and is only considering what it **believes**. In the following example, dark-blue : obstacles, purple : free space, dark-green : start-goal, yellow : closed nodes, light-green : open nodes. Assume, eight-point connectivity. 
<p align="center">
$$f(n) = h(n) \tag{1}$$
</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![greed]({{ site.url }}/assets/gifs/greedyy.gif)
<p align="center">
Figure 6.1 Greedy search
</p>
For now, just assume closed and open nodes as explored nodes. In the **next post**, we will discuss these terminologies with much depth and also the **implementation part of these algorithms**.     

### 6.3 Dijkstra's algorithm
Similar to how the nodes were prioritized on the basis of distance to goal, in Dijsktra's algorithm the nodes are prioritized on the basis of distance to the start i.e. the nodes which are closer to start. Same as above, dark-blue : obstacles, purple : free space, dark-green : start-goal, yellow : closed nodes, light-green : open nodes. Assume, eight-point connectivity.  

<p align="center">
$$f(n) = g(n) \tag{2}$$
</p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![dij]({{ site.url }}/assets/gifs/dijjj.gif)
<p align="center">
Figure 6.2 Dijkstra 
</p>

**</>** [GitHub](https://github.com/dv367/planning-cmu/tree/master/my_robot/src/scripts)

### 6.4 References
[1]. Choset H., Lynch  K. M., Hutchinson S. Kantor G., Burgard W., Kavraki L. E., Thrun Sebastian. Principles of Robot Motion. MIT Press 

<hr>
### Bonus!
* In the example of greedy search, which is in 2-dimension. What would be the function $h(n)$?
<hr>

[Previous](https://dv367.github.io/thinkspace/2020/graph/) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
[Next](https://dv367.github.io/thinkspace/2020/astar/)

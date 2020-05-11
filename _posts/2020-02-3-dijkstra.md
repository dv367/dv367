---
layout: post
title: "6. Greedy Search and Dijkstra"
mathjax: true
comments: true
description: "graph based planning"
keywords: "greedy, dijkstra, graph based planning"
---  

### 6.1 Greedy!
As we saw in the previous post, the wave-front planner doesn't take any advantage of the prior information about the start/goal position. Let us make the search a bit greedy by expanding/exploring nodes based on distance to goal i.e. node which are closer to goal are given more priority. This makes the search greedy and is only considering what it **believes**. In the following example, dark-blue : obstacles, purple : free space, dark-green : start-goal, yellow : closed nodes, light-green : open nodes. For now, just assume closed and open nodes as explored nodes. In the next post, we will discuss these terminologies with much depth and also the implementation part.     

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![greed]({{ site.url }}/assets/gifs/greedyy.gif)
<p align="center">
Figure 6.1 Greedy search
</p>

### 6.2 Dijkstra's algorithm
Similar to how the nodes were prioritized on the basis of distance to goal, in Dijsktra's algorithm the nodes are prioritized on the basis of distance to the start i.e. the nodes which are closer to start. Same as above, dark-blue : obstacles, purple : free space, dark-green : start-goal, yellow : closed nodes, light-green : open nodes.  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![dij]({{ site.url }}/assets/gifs/dijjj.gif)
<p align="center">
Figure 6.2 Dijkstra
</p>

### 6.3 Again, some terminologies!
* **Star(n)** - represents set of nodes which are adjacent to n.
* **$c(n_1,n_2)$** - is the length of edge connecting $n_1$ and $n_2$.
* **O** - open set(priority queue)
* **C** - closed set(all processed nodes)
* **h(n)** - heuristic cost function, which returns the estimated cost of the shortest path from $n$ to $q_goal$.
* **g(n)** - is the total length of **backpointer** path from $n$ to $q_start$
* **f(n)** - is the estimated cost of shortest path from $q_start$ to $q_goal$ via $n$.


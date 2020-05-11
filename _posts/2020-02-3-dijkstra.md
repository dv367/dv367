---
layout: post
title: "6. Greedy Search"
mathjax: true
comments: true
description: "graph based planning"
keywords: "greedy, dijkstra, graph based planning"
---  

## 6.1 Greedy!
As we saw in the previous post, the wave-front planner doesn't take any advantage of the prior information about the start/goal position. Let us make the search a bit greedy by expanding nodes based on distance to goal i.e. node which are closer to goal are given more priority. This makes the search greedy and is only considering what it **believes**. In the following example,    
---|---|---  
dark-blue| obstacle   
purple|free space  
yellow|closed state  
green|open states  
 

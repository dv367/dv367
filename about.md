---
layout: page
title: About
permalink: /about/
---
<img src="{{ site.url }}/assets/images/me.png" alt="alternatetext"  align="right" style="width:22%;height:22%;">     
<p align="justify">
  <br>
  I am an incoming graduate student at <a href="https://www.utias.utoronto.ca/">UTIAS</a> Fall 2021. I completed my Bachelors in ECE at Sardar Vallabhbhai National Institute of Technology. Currently, I work as an undergraduate researcher under <a href="https://scholar.google.co.in/citations?user=0zgDoIEAAAAJ&hl=en">Prof. Arun Kumar Singh</a>, <a href="https://sisu.ut.ee/collabrobotics/home-0">IMS Robotics</a>, University of Tartu. In the past, I've worked under <a href="https://faculty.iiit.ac.in/~mkrishna/">Prof. K Madhava Krishna</a>, <a href="https://robotics.iiit.ac.in/">Robotics Research Center</a>, IIIT Hyderabad. In my sophomore and junior year, I was an active member of my institute's technical club <a href="https://drishti-svnit.github.io/drishti/">Drishti</a>, participating in Asia-Pacific Robot Contest. <br>  
<br>  
My research interests is in motion planning and control for UAVs, UGVs.<br>
<br>
  <strong>Updates:</strong><br>  
<ol>
  <li><strong>2021/06/30</strong> Paper titled "Embedded Hardware Appropriate Fast 3D Trajectory Optimization for Fixed Wing Aerial Vehicles by Leveraging Hidden Convex Structures," accepted to <strong>IEEE/RSJ IROS 2021</strong></li>
  <li><strong>2021/06/09</strong> Paper titled "Real-Time Multi-Convex Model Predictive Control for Occlusion-Free Target Tracking with Quadrotors" submitted to <strong>IEEE Access</strong>.</li>
  <li><strong>2021/05/27</strong> Incoming graduate student at <a href="https://www.utias.utoronto.ca/">UTIAS</a></li>
  <li><strong>2021/05/11</strong> Capstone project on multi-robot cooperation: <a href="https://bit.ly/3eTurpt">Youtube </a></li>
  <li><strong>2020/12/15</strong> Technical Blogs on <strong>Motion Planning Techniques</strong><a href="https://dv367.github.io">&#128279;</a></li>
</ol>
<br>
Feel free to contact me <a href="mailto:vivekadajania@gmail.com">vivekadajania@gmail.com</a> <br>

</p>	
<p align="center">
  [<a href="https://www.linkedin.com/in/vivekadajania/">Linkedin </a>|<a href="https://github.com/dv367"> Github</a>]
</p><br>

<h6>Click on images to watch it on Youtube</h6>
### Projects
<ol>
  <li><h4> Multi-Modal MPC for autonomous driving</h4></li>
  Developed a multi-modal MPC that consists </i>
<p align="center">
<!--   [<a href="https://www.linkedin.com/in/vivekadajania/">Linkedin </a>|<a href="https://github.com/dv367"> Github</a>] -->
<iframe width="450" height="253" src="https://www.youtube.com/embed/z2cDWWb_oS0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>
  <!--   <p align="center"><a href="https://youtu.be/uDG9M1NHW_c">
<img src="{{ site.url }}/assets/images/acado_thread.png" alt="Watch on Youtube" width="75%" height="75%">
</a></p> -->
<li><h4>Fixed-Wing-Aerial Vehicle Trajectory Optimization in Urban Settings</h4></li>
  <p align="justify">
Research accepted to IROS'21: Developed a novel optimizer which exploits the computational structure of the non-linear trajectory optimization problem. Our optimizers builds an insight that the seemingly non-linear trajectory optimization has an implicit multi-convex structure. It outperforms the state-of-the-art implementation of SQP ACADO Toolkit in terms of computation time and solution quality.</p>
<p align="center">
<iframe width="450" height="253" src="https://www.youtube.com/embed/Qk7wdQ39Onk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>
<li><h4>Occlusion-Free Target Tracking with Quadrotors</h4></li>
Research submitted to IEEE Access: Developed a fast MPC algorithm that can run reali-time laptops and devices such as Jetson TX2 for the problem of quadrotor tracking a target. Our approach relies on novel reformulations for the tracking, collision, and occlusion constraints that induce a multi-convex structure in the resulting trajectory optimization. We exploit these mathematical structures using the split Bregman Iteration technique, eventually reducing our MPC to a series of convex Quadratic Programs solvable in a few milliseconds.
 <p align="center">
<iframe width="450" height="253" src="https://www.youtube.com/embed/D97A7I7qUts" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  </p>
  
  <li><h4>Multi-Robot System for Warehouse application</h4></li>
  <p align="justify">
  Final Year Project: Developed a multi-robot navigation system by incorporating diverse concepts and algorithms such as distributed model predictive control, A* search algorithm, On-demand Collision Avoidane, and Leader-Follower formation scheme. The problem statement was divided into three parts: single-robot navigation, multi-robot navigation, multi-robot cooperation to transport a deformable object. We validated and tested algorithms in Gazebo environment.</p><br>
 <a href="https://youtu.be/ncNinuzSq00">
   <img src="{{ site.url }}/assets/gifs/fyp_1.gif" alt="fyp1" style="width:45%;height:45%;"> <a href="https://youtu.be/ncNinuzSq00"><img src="{{ site.url }}/assets/gifs/fyp_2.gif" alt="fyp2" align="right" style="width:45%;height:45%;"></a>
  <p align="center">
  <iframe width="450" height="253" src="https://www.youtube.com/embed/ncNinuzSq00" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
   </p>
   
   
  <li><h4>Asia-Pacific Robot Contest</h4></li>  
  <p align="justify">Developed an autonomous navigation system for Omni-directional robots from its embedded system to motion planning and control.</p>
  <p align="center">
  <iframe width="450" height="253" src="https://www.youtube.com/embed/bhk94eT4mUk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  </p>  
  <li><h4>Non-Linear Model Predictive Control with Gradient Descent Variant</h4></li>
  <p align="justify">Developed deep learning inspired gradient descent variant RMSPprop using Autograd and incorporated it in a NMPC setup for non-holonomic robots.</p><br>
  <p align="center"><img src="{{ site.url }}/assets/gifs/rmsprop.gif" alt="rmsprop" align="center" style="width:75%;height:75%;"></p>
  
  <li><h4>Planning Techniques</h4></li>
  Followed RI16-730 Planning techniques in Robotics and implemented planners such as A*, ARA*, D*, Wave front planner, navigation potential functions, etc. Moreover, wrote blogs<a href="https://dv367.github.io">&#128279;</a> on implementation and results. <br> 
   <p align="center"><img src="{{ site.url }}/assets/gifs/intro5.gif" alt="robocon" align="center" style="width:75%;height:75%;"><br>
     Robot Chasing a Target</p> 



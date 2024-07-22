---
title: "Simulation and optimal control of a bouncing ball by a movable platform"
type: projects
layout: post
---
![A gif showing a simulated ball bouncing on a movable platform, and the platform moving at each step to guide the ball to the target destination](/images/bouncing_ball_fast.gif)

For the final project of my first-year fall semester class "Modeling and Simulation of the Physical World", my partner Ian Eykamp and I first created a simulation for a ball bouncing off of an arbitrary controlled surface, akin to a [Stewart Platform](https://en.wikipedia.org/wiki/Stewart_platform) robot. Then, we implemented an optimal-control policy that orients the surface to bounce the ball to a target destination.

### Simulation
The contact simulation was implemented via Matlab's ODE45 event checker, and we used a simple reflection with a coefficient of restitution. Notably, because our simulation is in 3D, and we don't care about the "yaw" of the surface, the orientation of the surface is encoded as as its normal vector - a 3-vector. To render the simulation, this normal vector is converted to a quaternion, so that the animation frames between two "keyframe" orientations can be interpolated using SLERP.

### Control
To control the ball, we solved a hybrid trajectory optimization problem with a fixed-mode sequence. We make the assumption that at each point along the trajectory, the optimal bounce is the one that gets the ball's next landing position closest to the desired location. As the ball bounces off of the surface, we can compute the location of the next bounce as a function of the surface's orientation. Finding the orientaiton that minimizes the distance of the next bounce to the target point is easily solved as an unconstrained minimization problem, which we solve using Matlab's `fmincon` solver.

### More results
For more details on the project, you can check out our report [here](/pdfs/Bouncing_ball_computational_essay.pdf)
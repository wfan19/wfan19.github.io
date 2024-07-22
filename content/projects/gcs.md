---
title: "Path planning around obstacles as convex optimization"
type: projects
layout: post
---

![Results plot of the graph of convex sets algorithm for a 2D path planning problem](/images/gcs_success.png)

For the final project of my robotics system integration class during my third year, I implemented the state of the art Graphs of Convex Sets (GCS) algorithm for reformulating motion planning around obstacles as a convex problem as described in the breaktrhough 2023 paper by Tobia Marcucci, Mark Peterson, David von Wrangel, and Russ Tedrake. We first implemented the alogrithm for path-planning of a single agent. Then, we extended the algorithm to multi-agent path planning. 

The project was implemented in Python using the cvxpy Python convex optimization library. Perspective functions are crucial to the GCS convex reformulation of the traditionally non-convex (mixed-integer) path-planning problem, but it requires the usage of perspective functions in a way that the cvxpy library did not support. To complete the project, I extended the cvxpy library to support these features, and merged my extensions into the main library via a [pull-requiest](https://github.com/cvxpy/cvxpy/pull/2157).

For more information on the GCS algorithm, check-out this incredible talk by Russ Tedrake at RI:
{{< youtube KSCC7mVJzaw >}}
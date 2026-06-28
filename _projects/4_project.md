---
layout: page
title: Trochoidal Paths for a Multi-Robot Swarm
description: Distributed consensus-based generation of constrained trochoidal swarm trajectories
img: assets/img/trochoids.gif
importance: 4
---

<div class="row justify-content-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    <img src="{{ '/assets/img/trochoids.gif' | relative_url }}" alt="Trochoidal paths executed by a multi-robot swarm" class="img-fluid rounded z-depth-1">
  </div>
</div>

<div class="caption">
  Trochoidal trajectories executed by a 3-robot indoor swarm.
</div>

This project studies the generation of collision-free trochoidal trajectories for a swarm of non-holonomic mobile robots. Starting from a distributed consensus protocol that enables connected agents to generate periodic patterns in two-dimensional space, we design the controller parameters and initial robot positions so that the resulting trajectories satisfy geometric and speed constraints.

The imposed constraints eliminate inter-robot collisions, maintain minimum and maximum separation from fixed reference points, and ensure that the generated trajectories remain physically trackable by the robots. The resulting motion patterns are relevant to persistent surveillance, coverage, guarding regions of interest, and target detection.

We also study how additional robots can be injected into the trajectories at specific locations to improve refresh rate without violating the geometric constraints. The proposed designs are validated in simulation and implemented on an indoor mobile robot platform.

## Links

- **Paper:** [European Journal of Control](https://www.sciencedirect.com/science/article/pii/S0947358024002036)
- **PDF:** [arXiv PDF](https://arxiv.org/pdf/2311.11720.pdf)

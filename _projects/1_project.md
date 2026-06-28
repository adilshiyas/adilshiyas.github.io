---
layout: page
title: CoAd
description: Constant-Time Planning for Continuous Goal Regions
img: assets/img/coad.gif
importance: 1
category: work
related_publications: true
---

<div class="row justify-content-center mt-3">

  <div class="col-md-6 text-center">
    <img src="{{ '/assets/img/coad.gif' | relative_url }}"
         alt="CoAd real robot demonstration"
         class="img-fluid rounded z-depth-1"
         style="width:90%;">
  </div>

  <div class="col-md-6 text-center">
    <img src="{{ '/assets/img/li_sim.gif' | relative_url }}"
         alt="CoAd simulation"
         class="img-fluid rounded z-depth-1"
         style="width:90%;">
  </div>

</div>

<div class="caption">
  <b>Left:</b> Real-world execution on a UR10 manipulator.
  <b>Right:</b> Simulation on a Franka Emika Panda.
</div>

In many robotic manipulation tasks, the robot repeatedly solves motion-planning problems that differ mainly in the location of the goal object and its associated obstacle, while the surrounding workspace remains fixed. Prior works have shown that leveraging experience and offline computation can accelerate repeated planning queries, but they lack guarantees of covering the continuous task space and require storing large libraries of solutions.

CoAd provides constant-time planning over a continuous goal-parameterized task space. It discretizes the continuous task space into finitely many Task Coverage Regions and constructs a compressed library by solving only representative root problems offline. Other problems are handled through fast adaptation from these root solutions.

At query time, the system retrieves a root motion in constant time and adapts it to the desired goal using lightweight adaptation modules such as linear interpolation, Dynamic Movement Primitives, or simple trajectory optimization. We evaluate the framework on various manipulators and environments in simulation and the real world, showing that CoAd achieves substantial compression of the motion library while maintaining high success rates and sub-millisecond-level queries.

## Links

- [GitHub](https://github.com/elpis-lab/CoAd)
- [arXiv](https://arxiv.org/abs/2603.12488)
- [PDF](https://arxiv.org/pdf/2603.12488.pdf)

---
layout: page
title: MotionBenchMaker - Pinocchio
description: Simulator-agnostic benchmarking framework for planners in robot manipulation problems
img: assets/img/pin_tallshelffetch.gif
importance: 2
category: work
giscus_comments: false

technologies:
  - name: Python
    color: "#d32f2f"
  - name: OMPL
    color: "#1976d2"
  - name: Pinocchio
    color: "#7b1fa2"
  - name: Coal
    color: "#7b1fa2"

---

MotionBenchMaker-Pinocchio is a Python reimplementation of MotionBenchMaker built on Pinocchio, Coal, MeshCat, and OMPL.

The project provides:

- A library of motion-planning benchmark environments
- Problem generation through inverse kinematics
- Collision-aware OMPL planning
- Benchmarking utilities compatible with PlannerArena
- Visualization through MeshCat

<div class="row justify-content-center">

  <div class="col-md-6 mt-3">
    <img src="{{ '/assets/img/pin_boxpanda.gif' | relative_url }}" class="img-fluid rounded z-depth-1">
  </div>

  <div class="col-md-6 mt-3">
    <img src="{{ '/assets/img/pin_tablepanda.gif' | relative_url }}" class="img-fluid rounded z-depth-1">
  </div>

  <div class="col-md-6 mt-3">
    <img src="{{ '/assets/img/pin_kitchenfetch.gif' | relative_url }}" class="img-fluid rounded z-depth-1">
  </div>

  <div class="col-md-6 mt-3">
    <img src="{{ '/assets/img/pin_tallshelffetch.gif' | relative_url }}" class="img-fluid rounded z-depth-1">
  </div>

</div>

<div class="caption">
Representative benchmark environments included in MotionBenchMaker-Pinocchio.
</div>

## Links

- **GitHub:** [MotionBenchMaker-Pinocchio](https://github.com/adilshiyas/MotionBenchMaker-Pinocchio)

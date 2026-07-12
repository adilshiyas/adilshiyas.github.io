---
layout: page
title: Constrained Motion Planning for Active 3D Reconstruction
description: Continuous constrained motion planning for active viewpoint selection using Expansion-GRR on a UR10 manipulator.
img: assets/img/constrained_ur10.gif
importance: 2
category: work
selected: false

technologies:
  - name: Python
    color: "#d32f2f"
  - name: PyBullet
    color: "#00897B"
  - name: MoveIt 2
    color: "#1976D2"
  - name: Intel RealSense
    color: "#E91E63"
---

<div class="row justify-content-center">
  <div class="col-sm-10 mt-3 mt-md-0 text-center">
    <img src="{{ '/assets/img/constrained_pybullet.gif' | relative_url }}"
         alt="Expansion-GRR trajectory execution in PyBullet"
         class="img-fluid rounded z-depth-1"
         style="width:80%;">
  </div>
</div>

<div class="caption">
The UR10 follows a continuous semi-circular trajectory around an object while maintaining camera orientation for multi-view 3D reconstruction.
</div>

This project explores **constrained motion planning for active viewpoint selection**, enabling a robot manipulator to capture multiple views of an object for 3D reconstruction. Rather than planning independent camera poses, the robot generates a continuous trajectory that keeps the camera oriented toward the object throughout execution, producing smooth motion while satisfying kinematic constraints.

To generate these trajectories, I implemented **Expansion-GRR (Global Redundancy Resolution)**, which computes smooth, continuous configuration-space paths corresponding to a desired workspace trajectory. Compared to MoveIt's `computeCartesianPath`, Expansion-GRR produced significantly more reliable joint-space trajectories without discontinuities, making it well suited for constrained visual inspection tasks.

The resulting trajectories were first validated in **PyBullet** before being executed on a **real UR10 manipulator** equipped with an **Intel RealSense D435 RGB-D camera**. Images collected along the trajectory were converted into point clouds and registered using the **Iterative Closest Point (ICP)** algorithm to reconstruct a complete 3D model of the object from multiple viewpoints.

<div class="row justify-content-center">
  <div class="col-sm-10 mt-3 mt-md-0 text-center">
    <img src="{{ '/assets/img/constrained_ur10.gif' | relative_url }}"
         alt="Expansion-GRR trajectory execution on a UR10"
         class="img-fluid rounded z-depth-1"
         style="width:80%;">
  </div>
</div>

### Highlights

- Implemented constrained motion planning for active viewpoint selection using **Expansion-GRR**
- Generated continuous joint-space trajectories while maintaining camera orientation toward the target object
- Compared Expansion-GRR against MoveIt's Cartesian path planner for constrained trajectory generation
- Executed planned trajectories in both **PyBullet** simulation and on a **real UR10 manipulator**
- Collected RGB-D observations using an **Intel RealSense D435** camera
- Reconstructed a complete 3D model by registering multiple point clouds using **ICP**

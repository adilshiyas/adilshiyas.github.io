---
layout: page
title: TAMP Framework with MoveIt
description: ROS 2 task and motion planning package using PDDL, Fast Downward, and MoveIt
img: assets/img/hanoi3_gif.gif
importance: 3
category: work
---

<div class="row justify-content-center">
  <div class="col-sm-10 mt-3 mt-md-0 text-center">
    <img src="{{ '/assets/img/hanoi3_gif.gif' | relative_url }}"
         alt="Tower of Hanoi demonstration"
         class="img-fluid rounded z-depth-1"
         style="width:80%;">
  </div>
</div>

<div class="caption">
The robot solves the Tower of Hanoi puzzle by combining symbolic task planning with geometric motion planning.
</div>

A ROS 2 package demonstrating task and motion planning (TAMP) on a Franka Emika Panda manipulator. The robot solves the Tower of Hanoi puzzle by combining symbolic task planning with geometric motion planning.

The symbolic planning problem is modeled in PDDL and solved using Fast Downward. Each action is then executed using MoveIt 2 and the MoveIt Task Constructor (MTC), which computes inverse kinematics, collision-free motion plans, and gripper actions.

## Package Components

- **hanoi_planner** – Generates a symbolic task plan by invoking the Fast Downward PDDL planner.
- **hanoi_mtc_executor** – Converts each symbolic action into a MoveIt Task Constructor task, computes inverse kinematics, collision-free motion plans, and executes the resulting trajectory.

## Links

- **GitHub:** [MoveIt-PDDL](https://github.com/adilshiyas/MoveIt-PDDL)

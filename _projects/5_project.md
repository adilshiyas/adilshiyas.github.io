---
layout: page
title: Reinforcement Learning for Robotic Object Picking
description: Deep reinforcement learning for vision-based object picking with a KUKA manipulator using DDPG and A3C.
img: assets/img/kuka_ddpg.gif
importance: 5
category: work
selected: false

technologies:
  - name: Python
    color: "#d32f2f"
  - name: PyTorch
    color: "#EF6C00"
  - name: PyBullet
    color: "#00897B"
---

<div class="row justify-content-center">
  <div class="col-sm-10 mt-3 mt-md-0 text-center">
    <img src="{{ '/assets/img/kuka_ddpg.gif' | relative_url }}"
         alt="DDPG training for object picking with a KUKA manipulator"
         class="img-fluid rounded z-depth-1"
         style="width:80%;">
  </div>
</div>

<div class="caption">
A KUKA manipulator learns to grasp objects through trial-and-error using deep reinforcement learning.
</div>

This project investigates **deep reinforcement learning for robotic manipulation**, where a simulated **KUKA manipulator** learns to grasp objects through interaction with its environment. The objective is to train policies capable of reliably reaching, grasping, and lifting objects without manually designing the control strategy.

### Deep Deterministic Policy Gradient (DDPG)

The initial implementation uses **Deep Deterministic Policy Gradient (DDPG)**, an off-policy actor-critic algorithm designed for continuous control. The actor network learns a deterministic control policy while the critic estimates the expected return of state-action pairs. Training is stabilized using replay buffers, target networks, and exploration noise, allowing the robot to gradually improve its manipulation strategy through experience.

<!-- Add A3C section here -->

<!-- Add comparison/results section here -->

### Highlights

- Implemented a complete DDPG training pipeline in **PyTorch**
- Trained a KUKA manipulator to perform object picking in simulation
- Implemented actor and critic neural networks with target network updates
- Used experience replay and exploration noise for stable continuous-control learning
- Evaluated training through reward, episode length, and loss metrics

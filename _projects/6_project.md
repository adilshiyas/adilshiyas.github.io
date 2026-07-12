---
layout: page
title: Action Chunking Transformer for Robotic Peg Insertion
description: Learning vision-based peg insertion policies from scripted demonstrations using the Action Chunking Transformer (ACT).
img: assets/img/act.gif
importance: 5
category: work
selected: false

technologies:
  - name: Python
    color: "#d32f2f"
  - name: PyTorch
    color: "#EF6C00"
  - name: MuJoCo
    color: "#00897B"
---

<div class="row justify-content-center">
  <div class="col-sm-10 mt-3 mt-md-0 text-center">
    <img src="{{ '/assets/img/act.gif' | relative_url }}"
         alt="Scripted demonstrations in MuJoCo"
         class="img-fluid rounded z-depth-1"
         style="width:80%;">
  </div>
</div>

<div class="caption">
Scripted expert demonstration used to generate training data for ACT
</div>

This project investigates **imitation learning for robotic manipulation** using the **Action Chunking Transformer (ACT)**. Rather than learning through reinforcement learning, the robot learns by observing expert demonstrations generated from scripted control policies in simulation. The objective is to predict continuous robot actions directly from visual observations and reproduce successful peg insertion trajectories.

### Demonstration Generation

Training demonstrations were generated in **MuJoCo** using scripted YAML policies describing the complete peg insertion sequence. To improve generalization, peg positions were randomized across multiple workspace locations with additional positional perturbations. The resulting demonstrations were stored as synchronized observations and robot actions for supervised learning.

### Action Chunking Transformer (ACT)

The collected demonstrations were used to train the **Action Chunking Transformer (ACT)**, a transformer-based imitation learning architecture for robotic manipulation. ACT combines a transformer policy with a variational autoencoder (VAE) latent representation to model complex manipulation behaviors while learning temporally consistent action sequences through behavior cloning.

The project included the complete data generation and training pipeline, including demonstration collection, dataset preparation, transformer training, and policy rollout within the MuJoCo simulation environment.

### Training Results

Training and validation losses decreased rapidly during the first few hundred epochs before converging, indicating that the transformer successfully learned the demonstrated behaviors without significant overfitting. Similar convergence trends were observed for both square and triangular peg insertion tasks, suggesting that the learned policy generalized well across both insertion geometries.

### Highlights

- Generated expert demonstrations using scripted policies in **MuJoCo**
- Randomized object placement to improve policy robustness
- Trained an **Action Chunking Transformer (ACT)** for vision-based manipulation
- Learned robot actions through supervised imitation learning with behavior cloning
- Evaluated training using training and validation loss curves

---
layout: page
title: Linear MPC with Dynamic Obstacle Avoidance
description: Linear MPC for trajectory tracking and dynamic obstacle avoidance on a UR10 manipulator using quadratic programming. 
img: assets/img/MPC_V1.gif
importance: 3
category: work

technologies:
  - name: C++
    color: "#d32f2f"
  - name: MuJoCo
    color: "#00897B"
  - name: OSQP
    color: "#388e3c"
  - name: OMPL
    color: "#1976d2"
  
---

Implementation of a linear Model Predictive Controller (MPC) for trajectory tracking and dynamic obstacle avoidance on a UR10 manipulator.

<p align="center">
  <img src="/assets/img/MPC_V1.gif" width="400"/>
  <img src="/assets/img/MPC_H.gif" width="400"/>
</p>

## Features

- Linear MPC formulated as a quadratic program (QP)
- Joint acceleration as the optimization variable
- Receding horizon trajectory tracking
- Soft dynamic obstacle avoidance constraints using slack variables
- Inverse dynamics for torque computation
- MuJoCo simulation of a UR10 manipulator

## MPC Formulation

The controller performs trajectory tracking using a linear Model Predictive Controller (MPC). The manipulator is modeled as a discrete-time double integrator, where the system state consists of joint positions and joint velocities,

$$
x =
\begin{bmatrix}
q \\
\dot{q}
\end{bmatrix},
$$

and the control input is the joint acceleration,

$$
u = \ddot{q}.
$$

The system is propagated over a finite prediction horizon according to the discrete-time dynamics

$$
x_{k+1} = A x_k + B u_k.
$$

At each control step, the MPC solves a quadratic program (QP) that minimizes trajectory tracking error while penalizing large joint accelerations,

$$
\min_U
\sum_{k=0}^{N}
(x_k - x_k^{\mathrm{ref}})^T
Q
(x_k - x_k^{\mathrm{ref}})
+
\sum_{k=0}^{N-1}
u_k^T
R
u_k,
$$

subject to the system dynamics and actuator constraints. The optimization returns an optimal sequence of joint accelerations over the prediction horizon, of which only the first control input is applied before the optimization is repeated at the next control step (receding horizon control).

Finally, the optimized joint accelerations are converted into joint torques using inverse dynamics,

$$
\tau = M(q)\ddot{q} + C(q,\dot{q}) + g(q),
$$

which are then applied to the MuJoCo simulation.

<table align="center">
  <tr>
    <td align="center">
      <img src="/assets/img/PD.gif" width="400"/><br/>
      <em>PD Controller Trajectory Tracking</em>
    </td>
    <td align="center">
      <img src="/assets/img/pd_qpos_err.png" width="400"/><br/>
      <em>Joint Position Tracking Error</em>
    </td>
  </tr>
</table>

<table align="center">
  <tr>
    <td align="center">
      <img src="/assets/img/MPC.gif" width="400"/><br/>
      <em>MPC Trajectory Tracking</em>
    </td>
    <td align="center">
      <img src="/assets/img/mpc_qpos_err.png" width="400"/><br/>
      <em>Joint Position Tracking Error</em>
    </td>
  </tr>
</table>

## Dynamic Obstacle Avoidance

Dynamic obstacle avoidance is incorporated directly into the MPC as optimization constraints. The future obstacle trajectory is predicted over the MPC horizon, and end-effector clearance constraints are enforced at each prediction step.

For each prediction step, the end-effector is constrained to remain above a minimum clearance height over the obstacle,

$$
z_{ee,k} + s_k \ge z_{\mathrm{clear},k},
$$

where $z_{ee,k}$ is the predicted end-effector height, $z_{\mathrm{clear},k}$ is the required obstacle clearance, and $s_k \ge 0$ is a slack variable that relaxes the constraint when necessary.

The optimization problem is modified to penalize the use of slack variables,

$$
\min_U
\sum_{k=0}^{N}
(x_k - x_k^{\mathrm{ref}})^T
Q
(x_k - x_k^{\mathrm{ref}})
+
\sum_{k=0}^{N-1}
u_k^T
R
u_k
+
w_s
\sum_{k=0}^{N-1}
s_k^2,
$$

subject to

$$
x_{k+1}=Ax_k+Bu_k,
$$

$$
\ddot{q}_{\min}\le u_k\le\ddot{q}_{\max},
$$

$$
\dot{q}_{\min}\le\dot{q}_k\le\dot{q}_{\max},
$$

$$
z_{ee,k}+s_k\ge z_{\mathrm{clear},k},
$$

$$
s_k\ge0.
$$

The slack variables ensure the optimization remains feasible when the obstacle avoidance constraints cannot be satisfied exactly. Their associated penalty weight, \(w_s\), encourages the controller to satisfy the obstacle constraints whenever possible while allowing graceful degradation when strict feasibility is impossible.

## Results


<table align="center">
  <tr>
    <td align="center">
      <img src="/assets/img/MPC_V1.gif" width="300"/><br/>
      <em>Scenario 1: Vertical Patrol</em>
    </td>
    <td align="center">
      <img src="/assets/img/MPC_H.gif" width="300"/><br/>
      <em>Scenario 2: Horizontal Patrol</em>
    </td>
    <td align="center">
      <img src="/assets/img/MPC_C.gif" width="300"/><br/>
      <em>Scenario 3: Circular Patrol</em>
    </td>
  </tr>
</table>

The controller successfully tracks a reference trajectory while avoiding a dynamic obstacle following vertical, horizontal, and circular trajectories. 

## Dependencies

- MuJoCo
- Eigen
- OsqpEigen

## Future Work

- Multiple dynamic obstacles
- Link-level collision avoidance
- Nonlinear MPC

## Links

- **GitHub:** [Dynamic-Obstacle-MPC](https://github.com/adilshiyas/Dynamic-Obstacle-MPC)

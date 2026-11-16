---
title: "Humanoid Walking Control"
excerpt: "This is an ongoing work, where I test and compare different walking control approaches"
collection: portfolio
---

This is an ongoing project, where I compare different approaches to walking control. Currently I have implemented one model-based walking controller and one learning-based walking controller. The goal of this project is to learn more about humanoid robotics, ROS2, simulation and control of robots with high DoF. The robot has 12 degrees of freedem: hip roll, hip yaw, hip pitch, knee pitch, ankle pitch and ankle roll in each leg. I started with Gazebo for Simulation, but switched to MuJoCo/ MuJoCo XLA (MJX) for Reinforcement Learning.


## Walking demonstrations
Below you can see demonstrations of the current walking controllers. The screencasts of the simulation are stuttering because of the high CPU load during the simulations.

### Model-based walking

<video controls preload="metadata" width="100%" src="/images/modelbased_walk_cut.mp4">
  Your browser cannot play this video.
  <a href="/images/modelbased_walk_cut.mp4">Watch the model-based walking demo</a>.
</video>

The model-based controller plans alternating footsteps and uses a linear inverted pendulum model (LIPM) to generate center-of-mass and zero-moment point references. The divergent component of motion (DCM) provides a preview signal for balance. Swing-foot trajectories describe foot lift and placement between supports.
Inverse kinematics to turn those targets into joint commands. A closed-loop
balance controller adjusts the references using the estimated robot state.

### Reinforcement-learning walking

<video controls preload="metadata" width="100%" src="/images/rl_walk_cut2.webm">
  Your browser cannot play this video.
  <a href="/images/rl_walk_cut2.webm">Watch the RL walking demo</a>.
</video>

The second demonstration uses a trained policy deployed in the MuJoCo simulator. Unlike
the model-based controller, the policy maps its observation and a forward-speed command
directly to joint-position offsets. Brax PPO was used for training on a Nvidia Tesla T4 using Google Colab.

## Scope and next steps

This is a simulation and research project, not a safety-certified or hardware-ready
controller. The estimator currently uses simulator ground-truth rather than
fused hardware sensors. Turning, step adjustment, and push recovery are not implemented. 

The next steps are to improve robustness, validating controller and model changes against both simulation backends, and extend the gait
toward push recovery. 

## Code

*[https://github.com/Bjarne33/3D-Bipedal-Walking](https://github.com/Bjarne33/3D-Bipedal-Walking)*

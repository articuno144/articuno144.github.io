---
title:  "Learning Coordinated Badminton Skills"
header:
  image: /assets/badminton/badminton_diverse_env_clips_compressed-ezgif.com-optimize.gif
---

## A robot that plays badminton.


**Authors**: Yuntao Ma, Andrei Cramariuc, Farbod Farshidian, Marco Hutter

**Video**: [Watch the full demonstration](https://youtu.be/zYuxOVQXVt8) 

**Paper**: [Read the paper](https://www.science.org/doi/10.1126/scirobotics.adu3922)

We've taught a quadrupedal robot that can autonomously play badminton with human opponents using only onboard perception. This work shows a method to coordinate complex whole-body movements that integrate locomotion, manipulation, and active perception in dynamic environments.

Our ANYmal-D robot equipped with a DynaArm manipulator successfully maintained long rallies with human players, achieving up to 10 consecutive shots in a single rally. The robot executed fast and precise swings with velocities up to 12.06 m/s while demonstrating sophisticated active perception behaviors that balance visual tracking with agile motion. Perhaps most impressively, it adapted its gait patterns dynamically based on distance and time constraints, operating effectively in diverse environments including outdoor conditions with wind.

A key contribution is our perception-aware training that incorporates real-world camera noise models directly into the RL training loop. This approach bridges the sim-to-real gap for perception while encouraging emergent active perception behaviors without requiring hard-coded field-of-view constraints. The robot learns when to prioritize visual tracking versus agile motion, resulting in sophisticated behaviors like pitching up to maintain shuttlecock visibility before pitching down for the swing.

We employed an asymmetric actor-critic training approach where the deployed policy only observes information available on the robot, while the critic receives additional privileged information to improve value function estimation. This setup enables better learning while maintaining deployability, solving a key challenge in privileged learning where teacher and student policies often develop different behaviors.

The robot demonstrated interesting emergent behaviors including distance-based gait adaptation ranging from minimal movement for close targets to galloping motions for distant ones. It showed time-constrained responses by adjusting movement vigor based on available time, automatic post-swing recovery by returning to center court position, and active perception behaviors like strategic pitching to maintain shuttlecock visibility.

This work shows that legged mobile manipulators can achieve human-like coordination in dynamic sports scenarios, opening new possibilities for dynamic manipulation tasks requiring whole-body coordination, human-robot interaction in competitive scenarios, agile robotics in unstructured environments, and sports robotics applications.

Future research directions include developing strategic gameplay with high-level policies that adapt tactics based on opponent behavior, enhanced perception through multi-modal sensing including sound and additional cameras, training for diverse motions and court coverage, and extension to other morphologies including humanoid robots where preliminary simulation results show promise.

This research was published in *Science Robotics* as a collaboration between ETH Zurich's Robotic Systems Lab and the Robotics and AI Institute, with support from Intel Labs, the Max Planck ETH Center for Learning Systems, and the National Centre of Competence in Research Robotics. The work showcases the potential of unified learning approaches for complex robotic tasks, demonstrating that with the right training methodology, robots can achieve sophisticated coordination between perception, locomotion, and manipulation in dynamic environments.

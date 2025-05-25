---
title:  "Combining MPC-controlled arm and RL-controlled legs"
header:
  image: /assets/marb/real_2021_compressed.gif
---

Bringing legged manipulators to rough terrain.

[arXiv link](https://arxiv.org/pdf/2201.03871.pdf)
[Video](https://www.youtube.com/watch?v=ZCv8W_NzhVo)

Optimization-based control methods for legged mobile manipulators typically require model simplifications to allow for real-time computation. With these assumptions, their motion can be very precise. However, common simplifications such as flat terrain, predefined contact schedules, and ZMP criterion often do not perform well on challenging terrains. On the other hand, RL-based methods have proven effective in these environments. In this project, we sought to maintain the model-based control for the arm due to its precision, while delegating control of the robot's legs to an RL policy.

A simplistic method would involve separating the two components completely. We could train an RL policy that is robust against random disturbances and treat whatever arises from the arm as a disturbance. Alternatively, we could utilize the optimization results (e.g. MPC) from the arm controller so that the leg anticipates incoming 'disturbances' and learns to compensate for them.

However, running MPC during the training is not feasible due to the prohibitive computational cost. Our RL simulation in RaiSim operates at around 10k fps, whereas MPC only runs at approximately 200 fps even after disabling all computationally intensive constraints. Instead of executing MPC, we trained the policy using a wrench that changes smoothly over time, akin to what actually occurs during deployment. The RL policy observes a prediction of the wrench sequence, which will also be available during deployment. In this scenario, the policy learns to compensate for the predicted external wrench.

![recovery]({{ site.url }}/assets/marb/pull_comparison.gif)

Deploying the policy on the robot is then a relatively straightforward process. At each timestep, we plan the MPC and perform inverse dynamics to compute the wrench that will be applied to the robot base. This prediction is fed in the same format as the external wrench used during training.

![recovery]({{ site.url }}/assets/marb/real_2021.gif)
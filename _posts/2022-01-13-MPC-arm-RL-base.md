---
title:  "Combining MPC-controlled arm and RL-controlled legs"
header:
  image: /assets/marb/real_2021.gif
---

Bringing ALMA to rough terrain.

[arXiv link](https://arxiv.org/pdf/2201.03871.pdf)
[Video](https://www.youtube.com/watch?v=ZCv8W_NzhVo)

(TODO: update. Currently this is just the abstract.)

Deep reinforcement learning produces robust locomotion policies for legged robots over challenging terrains. To date, few studies have leveraged model-based methods to combine these locomotion skills with the precise control of manipulators. Here, we incorporate external dynamics plans into learning-based locomotion policies for mobile manipulation. We train the base policy by applying a random wrench sequence on the robot base in simulation and add the noisified wrench sequence prediction to the policy observations. The policy then learns to counteract the partially-known future disturbance. The random wrench sequences are replaced with the wrench prediction generated with the dynamics plans from model predictive control to enable deployment. We show zero-shot adaptation for manipulators unseen during training. On the hardware, we demonstrate stable locomotion of legged robots with the prediction of the external wrench.

![recovery]({{ site.url }}/assets/marb/real_2021.gif)
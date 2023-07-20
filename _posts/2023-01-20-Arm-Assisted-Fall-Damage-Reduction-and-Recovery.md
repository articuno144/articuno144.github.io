---
title:  "Learning Arm-Assisted Fall Damage Reduction and Recovery for Legged Mobile Manipulators"
---

We've trained ALMA to adaptively recover using its arm.

[arXiv link](https://arxiv.org/abs/2303.05486)
[Video](https://www.youtube.com/watch?v=avwg2HqGi8s)

Previously, to make the ANYmal robots (including ALMA) rest, we typically ran the [free_gait](https://github.com/leggedrobotics/free_gait) control with scripted motions. This method worked well on flat terrain. However, when we went into wild terrains or attached payloads, the motions would sometimes deviate from the planned course. To address this, I trained a learning-based resting controller using [time-based rewards](https://sites.google.com/leggedrobotics.com/end-to-end-loco-navigation/home), which worked immediately. Given the ease of training state transition policies with this type of reward, it raises the question: how far can we push this?

![resting]({{ site.url }}/assets/recovery/resting.gif)

We attempted to train a single policy for fall damage reduction, fall recovery, and standing up. Once again, things mostly worked straight away. With randomized initialization and time-based rewards, the robot exhibited this behavior: it would rest on the ground and not stand up until the last minute.

![symmetric_recovery]({{ site.url }}/assets/recovery/symmetric_recovery.gif)

While this is beneficial as it is torque-efficient for the given task, it's not the behavior we ultimately want. When deploying the robot, we typically desire a more time-invariant behavior.

To achieve this, we utilized the concept of [asymmetric actor-critic](https://arxiv.org/abs/1710.06542). We intentionally hid the episode progress observation from the actor network, forcing it to maintain time-invariant behavior while still accomplishing the task. The critic still needed to observe the episode progress, because, for the time-based reward environments, the value function that the critic tries to estimate is time-dependent. We further added more privileged information from the simulator to the critic network, which accelerated the training process. As a result, we developed a time-invariant policy that typically enables recovery and standing up within our specified timeframe.

![recovery]({{ site.url }}/assets/recovery/experiment_weekend.gif)
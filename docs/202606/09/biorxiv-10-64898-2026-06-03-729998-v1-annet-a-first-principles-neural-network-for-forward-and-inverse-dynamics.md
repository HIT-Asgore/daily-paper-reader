---
title: "ANNet: A first-principles neural network for forward and inverse dynamics"
title_zh: ANNet：一种用于正动力学和逆动力学的第一性原理神经网络
authors: "Bahdasariants, S., Parola, L., Kacker, K., Feldman, A. K., Zdobinski, Z., Kang, I., Weber, D. J."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.729998v1.full.pdf"
tags: ["query:diff-physics"]
score: 7.0
evidence: 物理信息神经网络用于正逆动力学，可能可微
tldr: 现有正向和逆向动力学通常被分别建模，忽视了它们共享的物理结构。ANNet通过神经网络学习Appell加速度能这一标量函数，实现统一表示。逆动力学通过对加速度能的梯度求导获得关节力矩，正动力学则通过优化同一能量函数的最小值求解加速度，无需重新训练。在双摆仿真中，该方法在未见过的轨迹上达到了实时精度，为机器人的预测和控制提供了物理一致的统一框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 逆向和正向动力学通常被分开估计或实现，忽略了它们共享的物理方程，导致结构冗余和泛化性差。
method: ANNet学习Appell加速度能这一标量函数，逆动力学通过对其求加速度梯度得到，正动力学则通过最小化同一能量函数满足Gibbs-Appell方程求解。
result: 在双摆未见过轨迹上，逆动力学和基于优化的正向仿真均达到实时准确。
conclusion: 首次证明单一学习表示可同时支持预测和控制，为机器人运动控制提供了第一性原理的新范式。
---

## 摘要
生物和机器人系统必须解决两个相关的运动计算：逆动力学（确定产生期望运动所需的力或扭矩）和正动力学（将施加的力映射到运动）。尽管这些计算由相同的运动方程耦合，但在基于模型和基于数据的公式中，它们通常被估计或实现为不同的逆映射和正映射。这种分离可能掩盖了约束这两个问题的共享结构。在这里，我们提出了ANNet，一种物理信息神经网络，通过从经典力学中学习一个标量量——阿佩尔加速度能量，将两个计算置于一个共同的学习表示上。该网络将运动学状态和候选加速度映射到这个标量函数，通过将学习到的能量函数对加速度求导来恢复关节扭矩，从而获得逆动力学。然后，在不重新训练的情况下，通过将相同的学习能量景观嵌入到优化目标中，其无约束最小值满足Gibbs-Appell方程，从而计算正动力学。得到的加速度在时间上向前积分。我们在双摆范例上评估ANNet。在训练期间网络未见过的试验中，基于逆动力学和优化的正动力学模拟是实时的且准确的。我们的结果为使用单一学习表示同时支持预测和控制提供了一条第一性原理路径。

## Abstract
Biological and robotic systems must solve two related computations to move: inverse dynamics, which determines the forces or torques needed to produce a desired movement, and forward dynamics, which maps applied forces to motion. Although these computations are coupled by the same equations of motion, they are usually estimated or implemented as distinct inverse and forward mappings, in both model-based and data-driven formulations. This separation can obscure the shared structure that constrains both problems. Here, we present ANNet, a physics-informed neural network that places both computations on a common learned representation by learning a single scalar quantity from classical mechanics--Appell acceleration energy. The network maps kinematic state and candidate accelerations to this scalar function, and inverse dynamics is obtained by differentiating the learned energy function with respect to acceleration to recover joint torques. Forward dynamics is then calculated without retraining by embedding the same learned energy landscape in an optimization objective whose unconstrained minimum satisfies the Gibbs-Appell equation. The resulting accelerations are integrated forward in time. We evaluate ANNet on a double pendulum paradigm. In trials unseen by the network during training, inverse and optimization-based forward simulations are real-time accurate. Our results provide a first-principles route for using a single learned representation to support both prediction and control.
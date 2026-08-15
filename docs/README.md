<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-15
- 运行时间：2026-08-15 19:32:38 UTC
- 运行状态：成功
- 本次总论文数：19
- 精读区：7
- 速读区：12

### 今日简报（AI）
今日筛选19篇论文，精读7篇，重点聚焦机器人操控与预测控制的前沿方法。

最值得精读的是两篇9.0分工作：集中训练与评论解耦的在线强化学习，以及可微预测控制的拓扑可行性保证。

若想快速扩展视野，可速读JEPA世界模型系列与SLIM-0.5B等动作预测方案。
- 详情：[/202608/15/README](/202608/15/README)

### 精读区论文标签
1. [Efficient Real-World Online Reinforcement Learning for Robot Manipulation via Centralized Training and Critic Decomposition](/202608/15/2608.09762v1-efficient-real-world-online-reinforcement-learning-for-robot-manipulation-via-centralized-training-and-critic-decomposition)  
   标签：评分：9.0/10、query:mbrl-manip
   evidence：面向机器人操作的真实世界在线强化学习，结合集中训练与评论员分解提升样本效率
2. [Topological Feasibility Guarantees for Differentiable Predictive Control](/202608/15/2608.10332v1-topological-feasibility-guarantees-for-differentiable-predictive-control)  
   标签：评分：9.0/10、query:diff-physics
   evidence：嵌入可微动力学的可微预测控制
3. [SoRoMoX: Fast, Differentiable, and Parallelizable Soft Robot Models](/202608/15/2608.06650v1-soromox-fast-differentiable-and-parallelizable-soft-robot-models)  
   标签：评分：8.0/10、query:diff-physics
   evidence：基于JAX的可微软体机器人模型，支持控制相关导数计算
4. [TEMPO: Semantic-Action Decoupled RL Post-Training for Vision-Language-Action Models](/202608/15/2608.07314v1-tempo-semantic-action-decoupled-rl-post-training-for-vision-language-action-models)  
   标签：评分：8.0/10、query:mbrl-manip
   evidence：对视觉-语言-动作操作模型进行强化学习后训练
5. [Hölder Signed Distance: A Differentiable, Signed, Parallelizable Metric for Robotics](/202608/15/2608.07707v1-hlder-signed-distance-a-differentiable-signed-parallelizable-metric-for-robotics)  
   标签：评分：8.0/10、query:diff-physics
   evidence：提出一种可微、带符号、可并行的距离度量，用于机器人梯度优化
6. [LUCID: Latent-Skill Unified Control via Imagined Dynamics for Long-Horizon Humanoid Loco-Manipulation](/202608/15/2608.07746v1-lucid-latent-skill-unified-control-via-imagined-dynamics-for-long-horizon-humanoid-loco-manipulation)  
   标签：评分：8.0/10、query:mbrl-manip
   evidence：基于学习动力学模型想象展开的分层模型强化学习用于移动操作
7. [Differentiate the Solver, Not the Equation: Reverse-Sweep Adjoints for Block Implicit Simulation](/202608/15/2608.08559v1-differentiate-the-solver-not-the-equation-reverse-sweep-adjoints-for-block-implicit-simulation)  
   标签：评分：8.0/10、query:diff-physics
   evidence：提出离散求解器级微分方法，为块隐式物理仿真提供高效梯度传播

### 速读区论文标签
1. [JEPA-WAM: Learning Vision-Language-Action Policies with Joint-Embedding World Modeling](/202608/15/2608.09381v1-jepa-wam-learning-vision-language-action-policies-with-joint-embedding-world-modeling)  
   标签：评分：8.0/10、query:mbrl-manip
   evidence：面向动作生成与机器人控制的潜空间世界模型
2. [SLIM-0.5B: Learning Action-Grounded Predictive Latents for Robot Manipulation](/202608/15/2608.09771v1-slim-05b-learning-action-grounded-predictive-latents-for-robot-manipulation)  
   标签：评分：8.0/10、query:mbrl-manip
   evidence：为机器人操作学习动作条件转移的动力学模型
3. [JEPA-WAM: Stage-Level Joint-Embedding Prediction for World-Action Models in Robot Manipulation](/202608/15/2608.10780v1-jepa-wam-stage-level-joint-embedding-prediction-for-world-action-models-in-robot-manipulation)  
   标签：评分：8.0/10、query:mbrl-manip
   evidence：通过联合嵌入预测学习机器人操作的世界-动作模型
4. [Learning Loco-Manipulation From SMPC Demonstrations With Sparse Offline-to-Online RL](/202608/15/2608.12063v1-learning-loco-manipulation-from-smpc-demonstrations-with-sparse-offline-to-online-rl)  
   标签：评分：8.0/10、query:mbrl-manip
   evidence：利用SMPC专家生成演示，以稀疏奖励训练离线-在线强化学习，提升操作样本效率
5. [Is Forward Prediction Enough? Physical State Grounding for JEPA World Models](/202608/15/2608.06799v1-is-forward-prediction-enough-physical-state-grounding-for-jepa-world-models)  
   标签：评分：7.0/10、query:mbrl-manip
   evidence：面向控制相关潜在动力学的物理锚定JEPA世界模型
6. [GWM-VLA: Geometry-Aware Latent World Modeling for Vision-Language-Action Learning](/202608/15/2608.07619v1-gwm-vla-geometry-aware-latent-world-modeling-for-vision-language-action-learning)  
   标签：评分：7.0/10、query:mbrl-manip
   evidence：面向VLA操作学习的几何感知潜在世界模型，预测场景动态
7. [Vid2WAM: Distilling Video Diffusion Priors into World Action Models](/202608/15/2608.08558v1-vid2wam-distilling-video-diffusion-priors-into-world-action-models)  
   标签：评分：7.0/10、query:mbrl-manip
   evidence：将视频扩散先验蒸馏为世界动作模型，用于机器人控制，属于学习动力学模型
8. [SpeedTuning: Speeding Up Policy Execution with Lightweight Reinforcement Learning](/202608/15/2608.09138v1-speedtuning-speeding-up-policy-execution-with-lightweight-reinforcement-learning)  
   标签：评分：7.0/10、query:mbrl-manip
   evidence：用于操作策略执行速度的强化学习
9. [SG-WAM: Text-Grounded and Spatial-aware Semantic Guidance for World-Action Models](/202608/15/2608.08839v1-sg-wam-text-grounded-and-spatial-aware-semantic-guidance-for-world-action-models)  
   标签：评分：6.0/10、query:mbrl-manip
   evidence：面向机械臂操作的世界-动作模型与语义引导
10. [SpeedTuning: Speeding Up Policy Execution with Lightweight Reinforcement Learning](/202608/15/2608.09138v2-speedtuning-speeding-up-policy-execution-with-lightweight-reinforcement-learning)  
   标签：评分：6.0/10、query:mbrl-manip
   evidence：用强化学习预测最优执行速度以加速操作策略
11. [WorldSimProbe: Diagnosing Simulator Faithfulness in Action-Conditioned World Models for Embodied Manipulation](/202608/15/2608.09298v1-worldsimprobe-diagnosing-simulator-faithfulness-in-action-conditioned-world-models-for-embodied-manipulation)  
   标签：评分：6.0/10、query:mbrl-manip
   evidence：评估动作条件世界模型作为物理模拟器的忠实性，对基于模型的机器人控制相关
12. [Variational Parameter Calibration with Physics-Aware Latent-Space Surrogates](/202608/15/2608.11435v1-variational-parameter-calibration-with-physics-aware-latent-space-surrogates)  
   标签：评分：6.0/10、query:diff-physics
   evidence：通过自编码器构建可微动力学代理模型，实现变分参数估计


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>

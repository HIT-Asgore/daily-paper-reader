---
title: Neural networks learn forward dynamics when freed from numerical integration
title_zh: 神经网络在脱离数值积分时学习前向动力学
authors: "Bahdasariants, S., Yakovenko, S."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.27.728310v1.full.pdf"
tags: ["query:mbrl-manip"]
score: 8.0
evidence: 使用神经网络学习前向动力学，可应用于机器人控制
tldr: 人机界面需鲁棒地预测肢体动力学，但传统神经网络直接学习前向动力学映射时数值不稳定。将运动方程近似与时间数值积分分离，提出人工物理引擎（APE）模型。在未见外部扰动下，APE预测误差低且稳定，而直接映射RNN产生大误差。通过施加因果物理结构，APE显著提升了前向动力学预测的鲁棒性。
source: biorxiv
selection_source: fresh_fetch
motivation: 直接映射神经网络求解前向动力学时存在数值不稳定性，需更稳健的动力学预测方法。
method: 将运动方程近似与数值积分解耦，设计两阶段人工物理引擎（APE）模型。
result: APE在未见扰动下预测精度高且稳定，优于直接映射循环神经网络。
conclusion: 分离运动方程近似与积分可显著提升前向动力学预测的鲁棒性。
---

## 摘要
无缝的人机交互需要接口对生物信号和物理环境中固有的变异性保持鲁棒。先进的人机界面越来越依赖机器学习来预测或控制肢体动力学。这些系统必须学习控制变量与肢体状态之间的输入-输出映射，例如作用在分段手臂关节上的肌肉力或关节扭矩随时间变化到肢体姿态的映射。这种统计的输入-输出变换可能会导致预测的肌肉骨骼运动学和动力学数值不稳定。实现生物运动控制的鲁棒性需要同时解决前向和逆向动力学问题；然而，这些问题在计算上是不对称的，因为它们涉及相反的操作——积分和微分。由于我们之前已经证明，当训练神经网络在到达过程中将运动学信号映射到动力学信号时，它们能够解决逆向动力学问题，因此我们假设，分别表示运动方程的近似及其时间数值积分可能捕获前向动力学问题的相关计算结构。我们通过比较传统的直接映射循环神经网络和一个两阶段模型（人工物理引擎，APE）来测试这一假设。当预测一个两段系统在训练中未遇到的外部扰动下的状态时，直接映射的整体模型产生了与预期交互扭矩不一致的大预测误差，而APE在新初始条件和扰动下保持低误差并保持稳定。以运动方程的形式映射系统动力学，通过在人机界面设计中施加基于因果关系的物理结构，提高了对内在和外在变异性源的鲁棒性。

## Abstract
Seamless interaction between humans and machines requires interfaces that remain robust to the variability inherent in biological signals and physical environments. Advanced human-machine interfaces (HMIs) increasingly rely on machine learning to predict or control limb dynamics. These systems must learn input-to-output mappings between control variables and limb state, such as the mapping from muscle forces or joint torques acting about segmented arm joints to limb posture over time. Such statistical input-to-output transformations can result in numerical instability of predicted musculoskeletal kinematics and dynamics. Achieving the robustness of biological motor control requires solving both forward and inverse dynamics problems; however, these problems are computationally asymmetric because they entail opposing operations-integration and differentiation. Since we have previously shown that neural networks solve the inverse dynamics problem when trained to map kinematic to dynamic signals during reaching, we hypothesized that representing separately the approximation of equations of motion (EOM) and their temporal numerical integration may capture the relevant computational structure of the forward dynamics problem. We tested this hypothesis by comparing a conventional direct-mapping recurrent neural network (RNN) with a two-stage model, the artificial physics engine (APE). When predicting the state of a two-segment system under external perturbations not encountered during training, the direct-mapping, monolithic model produced large prediction errors inconsistent with the expected interaction torque, whereas the APE maintained low error and remained stable under novel initial conditions and perturbations. Mapping system dynamics in the terms of the EOM improves robustness against intrinsic and extrinsic sources of variability by imposing a causal, physics-based structure on HMI design.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：无缝的人机交互需要接口对生物信号和物理环境中的变异性保持鲁棒。人机界面（HMI）常依赖机器学习预测或控制肢体动力学，需要学习控制变量（如肌肉力、关节扭矩）到肢体状态（如姿态）的映射。然而，直接学习这种输入-输出映射可能导致数值不稳定，因为前向动力学（从力/扭矩到运动）和逆向动力学（从运动到力/扭矩）计算不对称——前者涉及积分，后者涉及微分。
- **背景**：作者之前证明神经网络能通过训练从运动学信号映射到动力学信号（逆向动力学）。本文假设：分别表示运动方程（EOM）的近似及其时间数值积分，可能捕获前向动力学问题的计算结构，从而提高鲁棒性。
- **核心问题**：如何设计神经网络结构，使其在预测前向动力学时避免数值不稳定性，尤其对训练中未出现的外部扰动保持稳健。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将运动方程（EOM）的近似与时间数值积分解耦，提出**人工物理引擎（Artificial Physics Engine, APE）**模型。APE 是一个两阶段模型，先由神经网络近似当前状态下的动力学导数（如角加速度），再通过数值积分更新下一时刻状态。
- **关键技术细节**：
  - **第一阶段**：使用神经网络（如全连接或循环网络）逼近运动方程，即根据当前状态和控制输入预测状态导数（例如关节角加速度）。
  - **第二阶段**：采用确定性数值积分器（如欧拉法或龙格-库塔法）对导数进行时间积分，得到下一时刻的完整状态（位置、速度等）。
  - **对比基线**：传统的**直接映射循环神经网络（direct-mapping RNN）**，这是一个整体模型（monolithic model），直接学习从当前状态和控制输入到下一时刻状态的映射，不显式拆分积分过程。
- **公式抽象**（文字说明）：  
  设状态向量为 \(x_t\)，控制输入为 \(u_t\)。直接映射模型学习 \(x_{t+1} = f(x_t, u_t)\)。APE 则分解为：
  - 神经网络学习导数 \( \dot{x}_t = g(x_t, u_t) \)
  - 数值积分 \( x_{t+1} = x_t + \int_{t}^{t+\Delta t} \dot{x}(\tau) d\tau \)，实际操作中用一个积分步近似。
- **设计意图**：通过分离物理定律（EOM）与积分过程，强制模型学习符合物理因果关系的动力学，从而提升泛化能力和稳定性。

## 3. 实验设计：数据集 / 场景、基准、对比方法

- **数据集 / 场景**：使用一个**两段系统（two-segment system）**的模拟数据，模拟手臂或机械臂的关节运动。系统受外部扰动（如外力、扭矩）影响，这些扰动在训练中未出现。
- **基准方法**：
  - **直接映射循环神经网络（direct-mapping RNN）**：作为传统整体模型对比。
  - **人工物理引擎（APE）**：两阶段模型。
- **测试条件**：
  - 在**未见的外部扰动**下预测系统状态（例如新的初始条件或施加的外力/扭矩）。
  - 评估预测误差（如关节角度、角速度的误差）和长期稳定性（是否发散）。
- **评估指标**：预测误差（数值比较）、与预期交互扭矩的一致性（物理合理性）。

## 4. 资源与算力

- **未明确说明**：论文中未提及使用的 GPU 型号、数量、训练时长、显存等具体算力信息。也未提及是否使用分布式训练或具体硬件平台。因此无法总结算力消耗。

## 5. 实验数量与充分性

- **实验数量**：论文仅报告了一个主要实验：在两段系统模拟中对比 APE 与直接映射 RNN 在未见扰动下的预测性能。未提及更多数据集（如不同自由度、不同动力学模型）或消融实验（如积分器类型、网络结构变化）。
- **充分性与公平性**：
  - **优点**：对比了直接映射整体模型，验证了分离积分的思想。实验场景明确，扰动条件具有挑战性。
  - **不足**：实验覆盖范围有限。仅用单一模拟系统，缺乏真实机器人或生物数据验证。未进行统计性多轮重复实验或交叉验证。未测试其他架构（如物理信息神经网络 PINN 或基于模型的强化学习）。因此，实验充分性较低，结论的泛化能力和统计可靠性有待加强。

## 6. 论文的主要结论与发现

- APE 在未见外部扰动下**预测误差低**且**长期稳定**，而直接映射 RNN 产生**大预测误差**，且误差与预期交互扭矩不一致（即违反物理规律）。
- 分离运动方程近似与数值积分，通过**施加基于因果关系的物理结构**，显著提高了前向动力学预测对内在和外在变异性（如新初始条件、外部扰动）的鲁棒性。
- 结论支持：神经网络在解决前向动力学问题时，显式嵌入物理约束（EOM+积分器）优于端到端直接学习映射。

## 7. 优点：方法或实验设计上的亮点

- **方法新颖性**：将控制领域常见的“模型预测控制”思想简化为“近似 EOM+数值积分”，并以神经网络实现，结构简洁且可解释性强。
- **物理约束嵌入**：通过强制模型学习动力学导数而非直接跳过积分，自然引入了物理因果性，避免产生非物理的预测（如能量不守恒、违反扭矩关系）。
- **实验验证清晰**：针对直接映射模型的典型失败案例（未见扰动下发散），展示了 APE 的稳定性，直观说明了分离积分的必要性。

## 8. 不足与局限

- **实验覆盖不足**：仅使用模拟的两段系统，未在真实机器人、多自由度系统或人体运动数据上验证。泛化到高维、非线性、含噪声的真实系统不可知。
- **未对比其他方法**：未与物理信息神经网络（PINN）、符号回归、或者基于物理的仿真器（如 MuJoCo）结合学习等方法比较。
- **未讨论积分误差累积**：数值积分自身会引入误差，长期预测时误差如何积累未分析。
- **未涉及计算效率**：未比较两种模型在训练和推理时的计算成本。
- **资源信息缺失**：未提供实验复现所需的训练超参数、数据生成细节、网络规模等，可复现性不足。
- **统计可靠性低**：未报告多次随机实验的均值和方差，无法判断结果是否统计显著。

（完）

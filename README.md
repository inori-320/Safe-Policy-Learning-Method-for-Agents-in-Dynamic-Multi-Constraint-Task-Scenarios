# 面向动态多约束场景的智能体安全策略学习方法



**Source Code for the Thesis "Safe Policy Learning Method for Agents in Dynamic Multi-Constraint Task Scenarios".**

论文《面向动态多约束场景的智能体安全策略学习方法》的核心源码，包括风险感知奖励机制、安全层投影优化和自适应原对偶优化方法。用于支持论文结果复现，并为后续研究提供思路。

---

## 仓库结构（Repository Structure）

```
.
├── algorithms/                  # 安全强化学习核心算法（SRSAC、SACLag 基线等）
│   ├── srsac/                   # 论文提出的 SRSAC 方法实现
│   ├── sac_lagrangian/          # 基线方法 SAC-Lag
│   ├── cvar_module/             # CVaR 估计与安全 critic 实现
│   └── utils/                   # Replay Buffer、网络结构、工具函数
│
├── envs/                        # 仿真环境接口
│   ├── unity_wrapper/           # Unity3D 环境 Python 接口（基于 ML-Agents）
│   └── gym_like/                # 其他对比实验环境（如 Safety-Gym）
│
├── configs/                     # 实验超参数配置（YAML/JSON）
│
├── scripts/                     # 训练、评估、绘图脚本
│   ├── train.py                 # 主训练入口
│   ├── evaluate.py              # 评估脚本
│   └── plot_results.py          # 绘制 Reward/Cost/ESI 曲线
│
├── results/                     # 实验结果（日志、曲线、模型参数）
│
└── README.md                    # 当前说明文档
```

---

## 快速开始（Quick Start）

例如需要在 `Safety-Gymnasium` 中的`SafetyPointGoal1-v0`环境对智能体进行训练，可以使用命令：

```shell
python main.py env=PointGoal1_v0 seed=1
```

这样会生成`data`文件夹，所有输出的数据都会存储。可以通过运行以下命令查看`tensorboard`面板：

```shell
tensorboard --logdir /data/tb_{timestamp}
```

另外，可以查看 `config/agent/sac_cost.yaml` 查看超参数的完整列表。

---

## 主要模块说明（Key Components）

### **风险感知奖励机制**

- 针对风险值动态调整智能体获得的奖励
- 与 Safety-Critic 输出联动

### **多网络联合优化结构**

- Policy Actor
- 双 Q-Critic
- 双 Safety-Critic
- 支持动态更新熵系数 / 风险系数

### **基于 CVaR 的安全价值评估**

- 累积成本分布估计
- 分位点回归
- α-CVaR 计算与优势加权更新

### **安全层投影优化机制**

- 预训练收集离线数据
- 在线训练中进行重训练，以优化安全层

### **基于原对偶优化的约束处理机制**

- 自适应拉格朗日乘子 λ
- 针对悲观域随机化的快速适应

---

## 论文引用（Citation）

如果你觉得该代码或本篇论文的思路对你有帮助，请引用以下论文：

```
待补充
```


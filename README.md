# Safe Risk-Sensitive Actor-Critic(SRSAC)

This is the source code of `Risk-Aware Safe Reinforcement Learning with CVaR-Based Constraints`

## Instructions

To train a SRSAC agent on the `SafetyPointGoal1-v0` environment from Safety-Gymnasium run:

```shell
python main.py env=PointGoal1_v0 seed=1
```

This will produce `data` folder, where all the outputs are going to be stored including `train/eval` logs, tensorboard blobs, and evaluation episode videos. One can attach tensorboard to monitor training by running:

```shell
tensorboard --logdir /data/tb_{timestamp}
```

Also, see `config/agent/sac_cost.yaml` for full list of hyperparameters.

## Acknowledgement

If you use this code in your research project please cite us.


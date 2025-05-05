

# Setup
```Shell
conda create -n ASAP --clone isaacgym
conda activate ASAP

pip install -e .

pip install -e isaac_utils
```

## Training for a basic humanoid locomotion task
```Shell
HYDRA_FULL_ERROR=1 python humanoidverse/train_agent.py \
+simulator=isaacgym \
+exp=locomotion \
+domain_rand=domain_rand_loco \
+rewards=loco/reward_g1_locomotion \
+robot=g1/g1_29dof_anneal_23dof \
+terrain=terrain_locomotion_plane \
+obs=loco/leggedloco_obs_history_wolinvel \
opt=wandb.yaml \
+opt=eval_analysis_plot_locomotion.yaml \
num_envs=4096 \
project_name=Basic_Loco \
experiment_name=Basic_Loco_May4_09PM_SRC01 \
wandb.wandb_id=run_20250504_9PM_low_pd
```

## Eval the ckpt
> `
python humanoidverse/eval_agent.py \
+checkpoint=logs/MotionTracking/xxxxxxxx_xxxxxxx-MotionTracking_CR7-motion_tracking-g1_29dof_anneal_23dof/model_5800.pt`

```Shell
# E.g. 
python humanoidverse/eval_agent.py \
+checkpoint=logs/Basic_Loco/20250504_193328-Basic_Loco_May4_0730PM_SRC01-locomotion-g1_29dof_anneal_23dof/model_39100.pt
```
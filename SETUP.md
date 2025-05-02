

```Shell
conda create -n ASAP --clone isaacgym
conda activate ASAP

cd /home/ziang/code/humanoid_codebase/ASAP
pip install -e .

pip install -e isaac_utils
```



```Shell
python humanoidverse/train_agent.py \
+simulator=isaacgym \
+exp=motion_tracking \
+domain_rand=NO_domain_rand \
+rewards=motion_tracking/reward_motion_tracking_dm_2real \
+robot=g1/g1_29dof_anneal_23dof \
+terrain=terrain_locomotion_plane \
+obs=motion_tracking/deepmimic_a2c_nolinvel_LARGEnoise_history \
num_envs=4096 \
project_name=MotionTracking \
experiment_name=MotionTracking_CR7 \
robot.motion.motion_file="humanoidverse/data/motions/g1_29dof_anneal_23dof/TairanTestbed/singles/0-TairanTestbed_TairanTestbed_CR7_video_CR7_level1_filter_amass.pkl" \
rewards.reward_penalty_curriculum=True \
rewards.reward_penalty_degree=0.00001 \
env.config.resample_motion_when_training=False \
env.config.termination.terminate_when_motion_far=True \
env.config.termination_curriculum.terminate_when_motion_far_curriculum=True \
env.config.termination_curriculum.terminate_when_motion_far_threshold_min=0.3 \
env.config.termination_curriculum.terminate_when_motion_far_curriculum_degree=0.000025 \
robot.asset.self_collisions=0
```


```Shell
python humanoidverse/eval_agent.py \
+checkpoint=logs/MotionTracking/xxxxxxxx_xxxxxxx-MotionTracking_CR7-motion_tracking-g1_29dof_anneal_23dof/model_5800.pt


python humanoidverse/eval_agent.py \
+checkpoint=logs/MotionTracking/20250502_011516-MotionTracking_CR7-motion_tracking-g1_29dof_anneal_23dof/model_5800.pt

python humanoidverse/eval_agent.py \
+checkpoint=logs/MotionTracking/20250502_011516-MotionTracking_CR7-motion_tracking-g1_29dof_anneal_23dof/model_13800.pt

```
# Reinforcement-Learning-Atari_MuJoCo_Project

Course project on reinforcement learning with Atari and MuJoCo environments.

## Contents

- **Task 1a – Atari Freeway (Discrete DQN)**
  - Environment: `FreewayNoFrameskip-v4`
  - Algorithm: DQN with CnnPolicy (Stable-Baselines3)
  - Training: 300k timesteps with TensorBoard logging
  - Result: mean episodic reward ≈ 18.9, validation episode reward ≈ 20–23

Planned additions:
- Task 1a – MuJoCo continuous control (HalfCheetah-style)
- Task 2 – Frequent reward Atari (Riverraid)
- Task 3 – Sparse reward Atari (Breakout)
- Task 4 – New MuJoCo continuous environment
- 
## Task 3 – Atari Breakout with DQN 

**Environment:** Atari Breakout (`ALE/Breakout-v5`)   
**Algorithm:** Deep Q-Network (DQN) with convolutional policy and frame stacking.

**Training setup**
- Input: 4 stacked grayscale frames (84×84)
- Total training steps: ~1,000,000
- Replay buffer size: 100,000
- Learning rate: 1e-4
- Discount factor (γ): 0.99
- Exploration ε: decayed from 1.0 → 0.01

**Training performance**
- Final training mean episode reward (`ep_rew_mean`): **~21.6**
- Final mean episode length (`ep_len_mean`): **~785** steps

**Evaluation**
- Ran **20 evaluation episodes**, each capped at 1,000 steps.
- **Best evaluation reward:** **10.0** (episode 15/20).
- Final episode used for the report had reward **4.0**.

**Artifacts in this repository**
- Notebook: `E_Dada_Task3_Atari_RL_Breakout.ipynb`
- Best episode video (reward = 10.0): `Task3_Breakout_DQN_BestEpisode.mp4`
- Last training episode video: `Task3_Breakout_DQN_LastEpisode.mp4`
- Raw evaluation episode 15 video: `Task3_Breakout_DQN_ep15-step-0-to-step-1000.mp4`
- All evaluation videos zipped: `videos_task3_breakout.zip`

## Task 4 – MuJoCo Hopper with PPO (Continuous Control)

**Environment:** `Hopper-v4` (MuJoCo continuous-control benchmark).  
**Algorithm:** Proximal Policy Optimization (PPO) with `MlpPolicy` (Stable-Baselines3).

**Training setup**
- Total training steps: **1,000,000**
- Vectorized environments: **4**
- Discount factor (γ): **0.99**
- Learning rate: **3e-4** (linear schedule)
- Rollout length: **2,048**, batch size: **64**, PPO epochs: **10**
- GAE(λ = 0.95) and advantage normalization enabled

**Training performance**
- Final training mean episode reward (`rollout/ep_rew_mean`): **≈ 2,070**
- Final mean episode length (`rollout/ep_len_mean`): **≈ 554** steps
- Value function explained variance: **≈ 0.99** (critic is well-fitted)

**Evaluation**
- Evaluated the final policy over **10 episodes** (no rendering, headless mode).
- **Mean evaluation reward:** **3480.30 ± 5.30**.

**Artifacts in this repository**
- Trained model: `model_Hopper_PPO.zip`
- TensorBoard logs: folder `Hopper_tensorboard/` (also zipped as `Hopper_tensorboard.zip`)

*Note:* Due to OpenGL limitations on Colab’s headless GPU backend (gladLoadGL error), MuJoCo rendering with `VecVideoRecorder` was not reliable, so Task-4 Hopper rollouts are documented via numerical evaluation and TensorBoard logs rather than videos.





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

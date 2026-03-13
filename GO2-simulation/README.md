# Unitree Go2 ProtoTwin Simulation

This project provides a **Unitree Go2 robot simulation environment** using **ProtoTwin** and **Reinforcement Learning (PPO)**.

The goal is to train a locomotion policy for the quadruped robot and evaluate it inside the ProtoTwin simulation environment.

---

# Project Overview

This repository includes:

- Reinforcement learning training code
- ProtoTwin simulation environment
- PPO locomotion policy
- Simulation execution scripts

The robot learns to **walk forward while maintaining stability**.

---

# System Architecture

```
ProtoTwin Simulation (.ptm)
        ↓
Environment Interface
        ↓
Reinforcement Learning (PPO)
        ↓
Trained Policy Model
        ↓
Simulation Execution
```

---

# Project Structure

```
go2-simulation
│
├── walking.ptm
│   ProtoTwin simulation model
│
├── train_walking.py
│   Reinforcement learning training script
│
├── run_walking.py
│   Runs trained model in simulation
│
├── logs
│   training checkpoints
│
├── tensorboard
│   training logs
│
└── README.md
```

---

# Requirements

Install the following software before running the project.

Python version:

```
Python 3.10+
```

Required libraries:

```
stable-baselines3
prototwin
prototwin-gymnasium
tensorboard
gymnasium
torch
numpy
```

Install dependencies:

```
pip install stable-baselines3
pip install prototwin
pip install prototwin-gymnasium
pip install tensorboard
pip install gymnasium
pip install torch
```

---

# Training the Walking Model

Run the training script:

```
python train_walking.py
```

The training script will:

- Start ProtoTwin simulation
- Create multiple simulation environments
- Train PPO locomotion policy
- Save checkpoints
- Save the final trained model

Training settings:

- Algorithm: PPO
- Timesteps: 1,000,000
- Parallel environments: 8
- Neural network size:  
  256 → 256 → 128

---

# Training Outputs

During training the following files will be generated.

Checkpoint models:

```
logs/checkpoints/
```

TensorBoard logs:

```
tensorboard/
```

Final trained model:

```
walking_final_model.zip
```

---

# Monitoring Training

To monitor the training process:

```
tensorboard --logdir tensorboard
```

Open browser:

```
http://localhost:6006
```

---

# Running the Simulation

After training finishes, run the simulation with the trained model.

```
python run_walking.py
```

This script will:

1. Start ProtoTwin
2. Load simulation model
3. Load trained PPO policy
4. Run robot locomotion

Console output will show:

- robot velocity
- reward
- actions
- reset events

---

# Robot Control

The robot has **12 controllable joints**.

Leg structure:

```
4 legs
3 joints per leg

hip
thigh
calf
```

Total actions:

```
12 joint position targets
```

Actions control the **target joint positions**.

---

# Observation Space

The policy observes:

- base position
- base orientation
- angular velocity
- linear velocity
- joint positions
- joint velocities
- foot positions
- previous action
- target speed

This allows the policy to maintain **balance and forward motion**.

---

# Reward Function

The reward encourages:

Positive rewards:

- forward velocity
- upright orientation
- correct body height
- stable heading
- low lateral movement

Penalties:

- sudden action changes
- high torque
- high joint velocity

This helps produce **stable walking behavior**.

---

# Episode Termination

Episode ends if:

- robot falls
- robot tilts too much
- robot drifts sideways
- episode time limit reached

---

# Future Work

Possible improvements:

- turning control
- navigation tasks
- terrain randomization
- sim-to-real transfer
- real Unitree Go2 deployment

---

# References

ProtoTwin

https://prototwin.com

Stable Baselines3

https://github.com/DLR-RM/stable-baselines3

Prototwin RLExamples

https://github.com/prototwin/RLExamples/

---

# License

MIT License

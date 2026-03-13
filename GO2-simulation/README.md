# Unitree Go2 Simulation with ProtoTwin

This project provides a simulation environment for the **Unitree Go2 quadruped robot** using **ProtoTwin** and **Reinforcement Learning (PPO)**.

The goal is to train a locomotion policy in simulation and test the behavior inside a ProtoTwin digital twin environment.

---

# Project Goal

This repository focuses on:

- Simulating the Unitree Go2 robot
- Training locomotion policies using reinforcement learning
- Running trained models inside ProtoTwin simulation

The workflow follows a **simulation-first robotics development approach**.

---

# System Workflow

Typical workflow of the project:

```
Robot Simulation (ProtoTwin)
        ↓
Environment Interface
        ↓
Reinforcement Learning Training
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
├── train_walking.py
│   Reinforcement learning training script
│
├── run_walking.py
│   Runs trained model in ProtoTwin simulation
│
├── logs
│   Training logs and checkpoints
│
├── models
│   Saved trained models
│
└── README.md
```

---

# Requirements

Before running the project install the following:

- Python 3.10+
- ProtoTwin Connect
- Stable-Baselines3
- Gymnasium
- TensorBoard

---

# Installation

Clone the repository.

```bash
git clone https://github.com/YOUR_USERNAME/go2-simulation.git
cd go2-simulation
```

Install required libraries.

```bash
pip install stable-baselines3
pip install tensorboard
pip install prototwin-gymnasium
```

---

# Training the Model

To train the locomotion model run:

```bash
python train_walking.py
```

During training:

Model checkpoints will be saved in:

```
logs/checkpoint
```

TensorBoard logs will be saved in:

```
tensorboard/PPO
```

---

# Monitoring Training

To monitor training progress run:

```bash
tensorboard --logdir logs/tensorboard
```

Open in browser:

```
http://localhost:6006
```

---

# Running the Simulation

After training the model run the simulation:

```bash
python run_walking.py
```

This script will:

- Load the trained model
- Connect to ProtoTwin
- Execute the locomotion policy in simulation

---

# Example Development Workflow

Typical development process:

1. Build simulation environment in ProtoTwin  
2. Train locomotion policy using reinforcement learning  
3. Monitor training with TensorBoard  
4. Run simulation with trained model  
5. Evaluate robot behavior  

---

# Future Improvements

Possible improvements for this project:

- Improved walking stability
- Turning and navigation behaviors
- Sim-to-real transfer
- Domain randomization
- Hardware deployment on Unitree Go2

---

# References

ProtoTwin

https://prototwin.com

Stable-Baselines3

https://github.com/DLR-RM/stable-baselines3'

Prototwin RLExamples

https://github.com/prototwin/RLExamples/

---

# License

MIT License

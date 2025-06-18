<div align="center">

# Dynamic Pricing System using Deep Reinforcement Learning

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white) ![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white) ![Keras](https://img.shields.io/badge/Keras-%23D00000.svg?style=for-the-badge&logo=Keras&logoColor=white) ![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)

</div>

## 📝 Overview

This project presents a Dynamic Pricing System for the Fast-Moving Consumer Goods (FMCG) retail sector using Deep Reinforcement Learning (DRL). Traditional pricing models, which rely on static adjustments, often fail to adapt to real-time market fluctuations in demand, inventory, and competitor actions. This project addresses these limitations by developing an intelligent agent that can autonomously adjust product prices to maximize profitability and maintain a competitive edge.

## 🎯 Problem Statement

The core challenge in the FMCG sector is setting optimal product prices in a highly dynamic environment. Overpricing can reduce sales volume, while underpricing harms profit margins. This project aims to solve this optimization problem by creating a DRL-based system that continuously learns from market interactions to find the most effective pricing strategies, balancing sales volume, revenue, and inventory management.

## 🤖 Architecture & Methodology

The system is built around a Deep Q-Learning (DQN) agent interacting with a custom-simulated retail market environment.

1.  **Simulated Environment (`Environment.py`):** A custom environment was built to mimic real-world market dynamics for 5 different FMCG products. It models key factors such as:
    * **Demand & Supply Dynamics:** Fluctuating demand based on customer behavior and price elasticity.
    * **Inventory Levels:** Stock levels that influence pricing decisions.
    * **Seasonality:** Four distinct seasons that impact product demand.
    * **Competitor Actions:** Prices of 3 simulated competitors are tracked and adjusted.

2.  **DQN Agent (`Agent.py`):** A Deep Q-Learning agent was designed to learn the optimal pricing policy.
    * **State Space:** The agent observes a state vector of 27 features, including demand, inventory, competitor prices, season, and day.
    * **Action Space:** The agent chooses from **59,049 possible actions**, representing discrete price level combinations for the five products.
    * **Neural Network:** The Q-network is a sequential model built with Keras, using two dense layers (64 neurons each with ReLU activation) and a linear output layer.
    * **Learning Mechanism:** The agent uses an epsilon-greedy policy for exploration and an experience replay buffer to stabilize learning. A separate target network is used to improve the stability of Q-value updates.

3.  **Training & Evaluation (`Train.py`, `Evaluation.py`):** The agent is trained over a series of episodes, where each episode represents a sales period. The `Train.py` script manages the training loop, while `Evaluation.py` is used to assess the performance of the trained agent and visualize the results.

## 📊 Results

The DRL-based system successfully demonstrated its ability to adapt and optimize pricing strategies over time. The agent learned to make effective decisions by balancing demand, competition, and inventory, resulting in a clear upward trend in total rewards. The final learned policy delivered superior revenue and profitability compared to what would be expected from traditional static pricing models.

## 🚀 How to Run

This project is structured as a set of Python scripts that define the agent, environment, training, and evaluation loops.

### Prerequisites

* Python 3.x
* TensorFlow (which includes Keras)
* NumPy
* Matplotlib

### Installation

1.  Clone the repository:
    ```bash
    git clone [your-repo-link]
    ```

2.  Install the required dependencies:
    ```bash
    pip install tensorflow numpy matplotlib
    ```

### Execution

1.  **Train the Agent:** Run the `Train.py` script to start the training process. This will train the DQN agent and save the model weights as `trained_model.weights.h5`.
    ```bash
    python Train.py
    ```

2.  **Evaluate the Agent:** Once the model is trained, run the `Evaluation.py` script. This will load the saved weights and run the agent in the environment to visualize its performance in terms of rewards and pricing decisions.
    ```bash
    python Evaluation.py
    ```

## 💻 Project Structure
``
.
├── Agent.py          # Defines the DQN Agent architecture<br>
├── Environment.py    # Defines the simulated FMCG Market Environment<br>
├── Train.py          # Main script to train the agent<br>
└── Evaluation.py     # Script to evaluate and visualize the trained agent's performance
``

## 📜 License

This project is released under the MIT License. It was developed as part of an academic requirement and is shared for educational and research purposes. See the `LICENSE` file for more details.

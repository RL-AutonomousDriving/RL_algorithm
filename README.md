# Tactical Decision Making Strategy for Autonomous Driving using Deep Reinforcement Learning Techniques

## Course: CMPE 297 sec 47 Reinforcement Learning

## Team Members

Team Members | Contributions | 
--- | --- |
Sivaranjani Kumar |  Setting up the highway environment for autonomous driving, Creating configuration files for driving environment, Running simulations for highway driving, Ablation study, Model training - Deep-Q Network algorithm, Optimizing and testing the DQN agent to make optimal decisions.    |
Vigneshkumar Thangarajan |  Requirement and dependency identification for DDQN based RL agent, Model Training - DDQN with Dueling architecture algorithm, Hyperparameter Tuning, Creating comparisons for two models, Optimizing and testing the DDQN agent with dueling architecture to make optimal decisions.    |

## Project Summary

The high-level decision-making strategies for autonomous driving have seen less progress compared to other areas. It’s because only few use cases are addressed and most of them cannot scale to more complex scenes, when decision-making involves interacting with other human drivers, whose behaviors are uncertain and difficult to model explicitly.  The cost involved in collecting human driving data is very expensive and not possible to record all the possible driving scenarios. The promising approach to achieve this without much hassle is to train a decision-making policy using reinforcement learning. RL leverages driving agent to automatically learn a complex driving policy to imitate the human driving decisions. The goal of our project is to train an autonomous driving agent to drive efficiently by following the safe maneuvers to overtake other driving vehicles in a simulated highway environment. To achieve this, we have implemented two DRL techniques, DQN and DDQN with Dueling Network Architecture which will increase the efficiency of driving agent in a highway environment. 

## Highway Environment








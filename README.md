# Tactical Decision Making Strategy for Autonomous Driving using Deep Reinforcement Learning Techniques

## Course: CMPE 297 sec 47 Reinforcement Learning

## Team Members

Team Members | Contributions | 
--- | --- |
Sivaranjani Kumar |  Setting up the highway environment for autonomous driving, Creating configuration files for driving environment, Running simulations for highway driving, Ablation study, Model training - Deep-Q Network algorithm, Optimizing and testing the DQN agent to make optimal decisions.    |
Vigneshkumar Thangarajan |  Requirement and dependency identification for DDQN based RL agent, Model Training - DDQN with Dueling architecture algorithm, Hyperparameter Tuning, Creating comparisons for two models, Optimizing and testing the DDQN agent with dueling architecture to make optimal decisions.    |

## Project Summary

The high-level decision-making strategies for autonomous driving have seen less progress compared to other areas. It’s because only few use cases are addressed and most of them cannot scale to more complex scenes, when decision-making involves interacting with other human drivers, whose behaviors are uncertain and difficult to model explicitly.  The cost involved in collecting human driving data is very expensive and not possible to record all the possible driving scenarios. The promising approach to achieve this without much hassle is to train a decision-making policy using reinforcement learning. RL leverages driving agent to automatically learn a complex driving policy to imitate the human driving decisions. The goal of our project is to train an autonomous driving agent to drive efficiently by following the safe maneuvers to overtake other driving vehicles in a simulated highway environment. To achieve this, we have implemented two DRL techniques, DQN and DDQN with Dueling Network Architecture which will increase the efficiency of driving agent in a highway environment. 

## Links

- [Project_Presentation](https://github.com/RL-AutonomousDriving/RL_algorithm/tree/main/Presentation_slides)
- [Project_Report](https://github.com/RL-AutonomousDriving/RL_algorithm/tree/main/Project_Report)
- [DQN and Dueling DQN code](https://github.com/RL-AutonomousDriving/RLAgent)

## Highway Environment

Environment Link: [Code for Highway Environment Implementation](https://github.com/RL-AutonomousDriving/Autonomous_Driving)

The highway environment consists of multiple lanes where the ego vehicle which is a driving agent and other surrounding vehicles can drive.  The agent is driving on a straight highway with several lanes, and is rewarded for reaching a high speed, staying on the rightmost lanes and avoiding collisions. The reward points for the agent are specified in the config file. 

RIGHT_LANE_REWARD: float= 0.1 
HIGH_SPEED_REWARD: float= 0.4 
LANE_CHANGE_REWARD: float= 0 
COLLISION_REWARD: -1 
CONTROLLED_VEHICLE: 1 

![alt text](https://github.com/RL-AutonomousDriving/RL_algorithm/blob/main/Images/Highway.png)

Source for image: https://highway-env.readthedocs.io/en/latest/environments/highway.html

## Hierarchical Motion Controller:

To manage the lateral and longitudinal movements of the ego and surrounding vehicles. It consists of two parts. The upper level contains two models, which are Intelligent driver model (IDM) and Minimize overall braking induced by lane changes (MOBIL). The lower level focuses on regulating vehicle velocity and acceleration. The original speed of the ego vehicle is chosen from [23, 25] m/s and the maximum speed of vehicle is 40 m/s. The length and width of all vehicles are 5m and 2m. The initial velocity of the surrounding vehicles is randomly chosen from [20, 23] m/s, and their behaviors are manipulated by IDM and MOBIL. Car-following and collision free is handled by IDM and it is implemented for Adaptive Cruise Controller (ACC). 

![alt text](https://github.com/RL-AutonomousDriving/RL_algorithm/blob/main/Images/env.png)

Source for image: https://arxiv.org/pdf/2007.08691.pdf

## Deep Q-Network

Execution file: [Code for DQN Training](https://github.com/RL-AutonomousDriving/RL_algorithm/blob/main/Deep_Q_Network.ipynb)

The traditional Deep reinforcement learning are the powerful to deal with the long sequential problems and it is independent of the historical data. But DRL was unable to address highway overtaking problems because of the continuous action space and large state space. To overcome this, we use deep neural network which is a non-linear function approximator to map the state and action into a value. When it is used in context of Q-learning, it refers to the Deep Q-Network (DQN). It is the first DRL methods proposed by the DeepMind. Deep neural networks empower RL to directly deal with high dimensional states like images. Motivation for Deep Q Network to solve this problem is – huge number of states causing numerous combinations of possible state-action combinations. Highway environment is ever changing and requires lot of time to explore all the state. The following equation explains the update value of Q-function: 

![alt text](https://github.com/RL-AutonomousDriving/RL_algorithm/blob/main/Images/DQN.png)

Source: https://www.analyticsvidhya.com/blog/2019/04/introduction-deep-q-learning-python/

## Dueling DQN. 

Execution file: [Code for Dueling DQN Training](https://github.com/RL-AutonomousDriving/RL_algorithm/blob/main/Dueling_DQN.ipynb)

Dueling DQN has two separate network one to estimate the state-value and the other one to estimate the advantages for each action in that state. This solves one of the specific problems to this domain. In environments like Atari single agent games and highway environment like this, at most of the states the agent action is not relevant. For example, when there are no chance of collision in any lane, the agent action is of least important. Dueling architecture addresses the problem of Q value overshooting and prevents model to learn from high Q values. 

![alt text](https://github.com/RL-AutonomousDriving/RL_algorithm/blob/main/Images/DDQN.png)

Source: https://arxiv.org/pdf/2007.08691.pdf

## Results


Techniques | Episodes | Training Time | Testing Time | Reward point for 3 episodes in testing | Results
--- | --- | --- | --- | --- | --- | 
DQN | 2000 | 9hr | 28s | [35.8, 11.1, 37.4] | High variance, takes longer time to train |
Dueling DQN | 2000 | 7hr | 26s | [30.7, 30.7, 32.7] | Variance is handled, agent learns to avoid collision | 


## Conclusions:

After training for 2000 episodes, the simulation results shows that DQN with Dueling network architecture performs better than DQN. In future, we can try Noisy DQN model and DQN with Prioritized Experience Replay to see if we can improve the current model performance. 

## References

[1] Liao, Jiangdong., Liu, Teng., Tang, Xiaolin., Mu, Xingyu., Huang, Bing., & Cao, Dongpu, "Decision-making strategy on Highway for Autonomous Vehicles using Deep Reinforcement Learning" 
[2] Li, Xin., Xu, Xin., Zuo, Lei, "Reinforcement Learning based overtaking decision-making for highway autonomous driving" in 2015 Sixth International Conference on Intelligent Control and Information Processing (ICICIP) 
[3] L. Edouard, “An environment for autonomous driving decisionmaking,” https://github.com/ eleurent/highway-env, GitHub, 2018. 
[4] M. Zhou, X. Qu, and S. Jin, “On the impact of cooperative autonomous vehicles in improving freeway merging: a modified intelligent driver model-based approach,” IEEE Trans. Intell. Transport. Syst., vol. 18, no. 6, pp. 1422-1428, June 2017. 
[5] C. J. Hoel, K. Driggs-Campbell, K. Wolff, L. Laine, and M. J. Kochenderfer, “Combining planning and deep reinforcement learning in tactical decision making for autonomous driving,” IEEE Transactions on Intelligent Vehicles, vol. 5, no. 2, pp. 294-305, 2019. 
[6] C. J. Hoel, K. Wolff, and L. Laine, “Tactical decision-making in autonomous driving by reinforcement learning with uncertainty estimation,” arXiv preprint arXiv:2004.10439, 2020. 
[7] P. Hart, and A. Knoll, “Using counterfactual reasoning and reinforcement learning for decision-making in autonomous driving,” arXiv preprint arXiv:2003.11919, 2020. 
[8] A. Furda, and L. Vlacic, “Enabling safe autonomous driving in real-world city traffic using multiple criteria decisions making,” IEEE Intelli. Trans. Sys. Magaz., vol. 3, no. 1, pp. 4-17, 2011. 
[9] S. Nageshrao, H. E. Tseng, and D. Filev, “Autonomous highway driving using deep reinforcement learning,” In 2019 IEEE International Conference on Systems, Man and Cybernetics (SMC), pp. 2326-2331, 2019. 
[10] S. Han, and F. Miao, “Behavior Planning For Connected Autonomous Vehicles Using Feedback Deep Reinforcement Learning,” arXiv preprint arXiv:2003.04371, 2020. 

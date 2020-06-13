# Learning Algorithm
Agent uses deep Q-network algorythm (DQN) for learning how to behave and maximize it's score in a provided environmet.

The project is split into three main parts:
1. scripts/main.py - runs the interaction loop between an agent and an envitonment over many episodes and time steps.
At the beginnig of each episod the environment state is reset which produces initial state for the agent.
Agent observes the state and selects an action for interaction. After executing previously selected action environment produces the next state, reward and boolean value which notifies about the end of the episode.
Agent continues the loop of selecting an action and interacting with the environment untill it reaches the terminal state or exceeds the maximum amount of timesteps.
The procees mentioned above repeats until maximum amount of episodes is reached or the agent reaches the average score greater than 13 which is considered as the environment being solved.
Apart of the trainning loop the main.py script tracks and plots the agent's average score and saves agent's network weights in case when the enviroment is solved.
"train" function contains the following set of hyperparameters:  
    n_episodes (int): maximum number of training episodes
    max_t (int): maximum number of timesteps per episode
    eps_start (float): starting value of epsilon, for epsilon-greedy action selection
    eps_end (float): minimum value of epsilon
    eps_decay (float): multiplicative factor (per episode) for decreasing epsilon

2. scripts/dqn_agent - definens the Agent class which implements DQN algorythm with two extensions (Target Networks and Double DQN). https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf

The Agent class has two main functions:
"act" - selects an action for a given state using epsilon-greedy action selection. Epsilon-greedy action selection helps the agent to balance between exploration and exploitantion.
The are two possibilities of how action can be selected. 
Either the agent selects action randomly (exploration) or uses function aproximation algorythm for selectin an action with a highest value for a given state.
One of the ideas of DQN is to use supervised learning such as deep neural networks as a function aproximator, which has a state as an input parameters of the DNN and 

"learn" - observes a new state and a reward after selecting an action which gives the agent a possibility to learn and improve the action selection function from his expirience. 
DQN  


Agent tries to maximize it's commulative reward over an episode by selecting an actions which gives him the best e
The general idea of the DQN algorythm is maximizing the agent's reward by selecting and action A given a state S selecting the most appropriate action  to keep track of the agent's previous expirience (state, action, next state, reward) and select the most appropriate action when the agents observe



Runs training loop for the agent which allows the agent to interact with the environment by executing actions and receiving the next state and a reward form the environment.
Agent 


and tracks agent's score.
There is a closer look on how 

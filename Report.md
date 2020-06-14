## Learning Algorithm
Agent uses deep Q-network algorithm (DQN) for learning how to behave and maximize its score in a provided environment.

The project is split into three main parts:
# 1. Main trainig loop (scripts/main.py)

Script runs the interaction loop between an agent and an environment over many episodes and time steps.
At the beginning of each episode the environment state is reset, which produces initial state for the agent.
Agent observes the state and selects an action for interaction. After executing the previously selected action, environment produces the next state, reward and boolean value that notifies about the end of an episode.
The agent continues the loop of selecting an action and interacting with the environment until it reaches the terminal state or exceeds the maximum amount of timesteps.
The process mentioned above repeats until the maximum amount of episodes is reached, or the agent reaches the average score greater than 13, which is considered as the environment being solved.
Apart from the training loop, the main.py script tracks and plots the agent's average score and saves the agent's network weights in the case when the environment is solved.
"train" function contains the following set of hyperparameters:  
    * n_episodes (int): maximum number of training episodes.
    * max_t (int): maximum number of timesteps per episode.
    * eps_start (float): starting value of epsilon, for epsilon-greedy action selection.
    * eps_end (float): minimum value of epsilon.
    * eps_decay (float): multiplicative factor (per episode) for decreasing epsilon.

# 2. DQN Agent (scripts/dqn_agent)
It defines the Agent class that implements [DQN](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf) algorithm with two extensions (Target Networks and Double DQN). 

 * The Agent class has two main functions:

 * 2.1 **"act"** - selects an action for a given state using epsilon-greedy action selection. Epsilon-greedy action selection helps the agent balance between exploration and exploitation.
There are two possibilities of how action can be selected: 
The agent selects action either randomly (exploration) or uses a function approximation algorithm for selecting an action with a highest value for a given state (exploitation, Q function).
One of the ideas of DQN is to use supervised learning algorithms such as deep neural networks as a function approximator, which has a state as an input parameters of the DNN and action values as an output.

 * 2.2 **"learn"** - observes a new state and a reward after selecting an action which gives the agent a possibility to learn and improve the action selection function/network from its experience. Agent keeps track of its previous experience by storing the last k (state, action, next state, reward) tuples in its replay buffer. Later the minibatches selected randomly-uniformly from the replay buffer are used for training DNN to map states to actions values (Q function).

 * 2.3. There are two extensions to the original DQN algorithm implemented in the project:
 * 2.3.1. **Target network.** This technique helps stabilise training by the fact that the optimal Q value function learned by the neural network is constantly changing and depends on Q value functions itself. The main idea of the target network approach is to introduce a second, target network, which is a lagged copy of the original network for stabilizing the target Q value function.

 * 2.3.2 **Double DQN.** Due to the noises in the environment and errors in function approximation using neural networks, the agent may not fully explore the environment, what can lead to Q values being overestimated. The Double DQN algorithm reduces the overestimation of Q-values by selecting the best action for a state using one network and estimating the Q-value by using a second network. Local and target networks can be used correspondingly for action selection and target Q-value estimation.
 * the agent and replay buffer contains the following set of hyperparameters:
   * BUFFER_SIZE = int(1e5)  # replay buffer size
   * BATCH_SIZE = 64  # minibatch size
   * GAMMA = 0.99  # discount factor
   * TAU = 1e-3  # for soft update of target parameters
   * LR = 5e-4  # learning rate
   * UPDATE_EVERY = 4  # how often to update the network

# 3. Neural network model (scripts/model.py)
The network model contains three linear layes, input layer with size (state_size, fc1_units=64), hidden layer with size (fc1_units=64, fc2_units=64) and output layer with size (fc2_units, action_size). ReLU activation function is used for the input and the hidden layer.

# Plot of Rewards
Environment is usually solved in less than 600 episodes:

![Scores:](/images/scores_1.png)

![Scores:](/images/scores_2.png)
# Ideas for Future Work
Implement prioritized experience replay. The intuition behind this technique is that some of the experiences are more informative for the agent and, as a result, the agent can learn faster from such experiences. Main idea is to determine how valuable (informative) a given experience  record is (it can be measured with absolute difference between expected and actual Q-value) and increase the probability of sampling of such experiences.


# UdacityRL-Navigation


todo: add video/gif/image

# Project Details

The project shows an example of an agent learning to navigate and collect bananas by interacting with an environment.

Agent can navigate in the environment using a set of discrete actions:

0 - move forward.
1 - move backward.
2 - turn left.
3 - turn right.

Agent receives +1 reward for collecting a yellow banana.
Agent receives -1 reward for collecting a blue banana.

The agent's goal is to collect as many yellow bananas as possible while avoiding blue bananas.

The environment is represented by a state space which has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around the agent's forward direction. 

The task is episodic and considered as solved when the agent gets an average score of +13 over 100 consecutive episodes.


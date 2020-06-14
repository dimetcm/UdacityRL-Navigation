# UdacityRL-Navigation

![Banana agent](/images/banana.gif)

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

# Getting Started

* create (and activate) a new Python environment. I'd recommend using python version 3.6 since it's compatible with all other project's dependencies.

* install unityagents with:
`pip install unityagents`

* install [pytorch](https://pytorch.org/)

* Download the Unity Environment that matches your operating system:

Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)

* in case if you're getting troubles wiht the dependencies setup please take a look at the dependencies section from the [Udacity DRL course repository](https://github.com/udacity/deep-reinforcement-learning/blob/master/README.md)

# Instructions

For running agent training algorithm please run scripts/main.py script.
Please note that you might need to modify scripts/main.py script and set a proper path to the unity environment (by default env_path = "../data/Banana_Windows_x86_64/Banana.exe").



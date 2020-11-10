---
title: Reinforcement learning
keywords: reinforcement learning
tags: [reinforcement_learning]
last_updated: November 10, 2020
toc: false
sidebar: reinforcement_learning_sidebar
permalink: reinforcement_elements.html
folder: 
author_profile: true
authors:
 - Olivier Sheik Amamuddy,
---
## Additional elements of reinforcement learning
### Reward
A reward defines the goal of an RL problem, and specifies the immediate benefit (positive and negative events) of being in a specific state.
It is the feedback sent by the environment to the RL agent, which the latter tries to maximise over time. 
In a biological system, we might think of rewards as analogous to the experiences of pleasure or pain. 
<a href=”http://incompleteideas.net/book/bookdraft2018mar21.pdf”></a> 

### Value function
The value function specifies what is rewarding over time by accumulating all the rewards obtained by the agent.
<a href=”http://incompleteideas.net/book/bookdraft2018mar21.pdf”></a>

### Value
The value is the total expected reward from a state and onwards into the future.
It assists the agent in predicting future rewards by allowing the exploration of states that may otherwise withhold higher rewards.
Based on the value assessment, actions are then taken by the RL agent. 
<a href=”http://incompleteideas.net/book/bookdraft2018mar21.pdf”></a>

### RL model
RL agents systems can make decisions using either a model-based or model-free approaches, even though the boundary between 
the two may not be as clear-cut in practice. The model is a set of rules that the agent is provided with in order to have some
understanding of its environment. In this way, the learner can explore its environment more efficiently. 
Alternatively, in model-free approaches no such information is provided, and the learner evaluates the environment solely by 
trial-and-error. <a href=”https://bair.berkeley.edu/blog/2019/12/12/mbpo/”></a> 
<a href=”https://www.mathworks.com/support/search.html/videos/reinforcement-learning-part-2-understanding-the-environment-and-rewards-1551976590603.html?category=getting-started-with-reinforcement-learning-toolbox&fq=asset_type_name:video%20category:reinforcement-learning/index&page=1”></a>.

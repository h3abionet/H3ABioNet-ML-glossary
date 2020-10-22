---
title: Reinforcement learning
keywords: reinforcement learning
tags: [reinforcement_learning]
last_updated: October 22, 2020
toc: false
sidebar: reinforcement_learning_sidebar
permalink: reinforcement_agent.html
folder: 
author_profile: true
authors:
 - Olivier Sheik Amamuddy,
---
## The learning agent
The agent comprises a policy and a learning algorithm, i.e. anything that doesn’t belong to the environment.
The policy is a function approximator (eg. deep neural network, polynomials or lookup tables 
<a href="https://www.mathworks.com/solutions/deep-learning/reinforcement-learning.html?s_eid=PEP_22452"><a/>) 
that maps given actions to observations. Learning iteratively updates the policy, using as inputs the agent’s 
actions, observations and rewards, with the objective of finding a policy that maximizes the cumulative reward,
over a large number of iterations <a href="https://www.mathworks.com/help/reinforcement-learning/ug/create-agents-for-reinforcement-learning.html"><a/>. 

RL agents can be implemented by a variety of algorithms [e.g. 
State-action-reward-state-action (SARSA), Policy gradient (PG), 
Deep Q-network, Deep deterministic policy gradient (DDPG), 
Twin-delayed deep deterministic policy gradient (TD3), 
Proximal policy optimization, Asynchronous Actor-Critic Agents (A3C), 
Soft actor-critic (SAC), Q-Learning, 
deep Q-learning network (DQN) and custom agents]

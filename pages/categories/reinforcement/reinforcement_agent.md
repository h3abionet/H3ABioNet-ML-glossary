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
The agent comprises (1) a policy and (2) a learning algorithm, i.e. anything that doesn’t belong to the environment. The policy is a function approximator (eg. deep neural network, polynomials or lookup tables <a href="https://www.mathworks.com/solutions/deep-learning/reinforcement-learning.html?s_eid=PEP_22452"><a/>) that maps given actions to observations. Learning iteratively updates the policy, using as inputs the agent’s actions, observations and rewards, with the objective of finding a policy that maximizes the cumulative reward, over a large number of iterations <a href="https://www.mathworks.com/help/reinforcement-learning/ug/create-agents-for-reinforcement-learning.html"><a/>. Policies can be learned via methods termed as critics and actors. The actor selects actions, while the critic criticizes them ref. RL agents can use critics only (<strong>value-based agents</strong>), actors only (<strong>policy-based agents</strong>), or both of the methods (<strong>actor-critic agents</strong>) to inform the agent’s policy. More generally, value-based agents work more optimally with discrete actions, and can be more computationally expensive for continuous actions; policy-based agents are simpler and are more suited for sets of continuous actions; actor-critic agents can be used with both discrete and continuous sets of actions.

RL agents can be implemented by a variety of algorithms, some examples being:
* State-action-reward-state-action (SARSA)
* Policy gradient (PG), 
* Deep Q-network, Deep deterministic policy gradient (DDPG)
* Twin-delayed deep deterministic policy gradient (TD3), 
* Proximal policy optimization
* Asynchronous Actor-Critic Agents (A3C)
* Soft actor-critic (SAC)
* Q-Learning
* Deep Q-learning network (DQN)
* Custom agents

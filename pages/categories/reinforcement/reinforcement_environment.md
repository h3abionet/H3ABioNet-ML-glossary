---
title: Reinforcement learning
keywords: reinforcement learning
tags: [reinforcement_learning]
last_updated: October 22, 2020
toc: false
sidebar: reinforcement_learning_sidebar
permalink: reinforcement_environment.html
folder: categories/reinforcement
author_profile: true
authors:
 - Olivier Sheik Amamuddy,
---
## The learning environment
The RL environment is dynamic, and is defined by a set of states <a href="http://ijcta.com/documents/volumes/vol2issue1/ijcta2011020115.pdf"><a/>, 
which the agent can observe <a href="https://www.cs.toronto.edu/~zemel/documents/411/rltutorial.pdf"><a/> and interact with. 
It is often represented as a simulation, but can also be a real physical system 
<a href="https://www.kdnuggets.com/2019/10/mathworks-reinforcement-learning.html"><a/>. 
In essence, the environment is typically defined as a Markov decision process (MDP) for which an exact mathematical model 
is unknown and can be potentially complex <a href="https://en.wikipedia.org/wiki/Reinforcement_learning"><a/>. The Markovian 
property in RL is related to the fact that, given a current state and set of actions, the next state is oblivious to all 
previous states and actions <a href="https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-825-techniques-in-artificial-intelligence-sma-5504-fall-2002/lecture-notes/Lecture20FinalPart1.pdf"><a/>.

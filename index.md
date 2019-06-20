---
layout: post
title: Contents
---

<span class="newthought">These notes</span> 
{% include sidenote.html id="sdid" note="These notes and the general content of the first half of the course were primarily inspired by the following course:<br>- Stanford [CS228](https://cs228.stanford.edu/). Those notes were originally written by [Volodymyr Kuleshov](http://www.stanford.edu/~kuleshov) and [Stefano Ermon](http://cs.stanford.edu/~ermon/), with the [help](https://github.com/ermongroup/cs228-notes/commits/master) of many students and course staff. Once we switch to Decision Making you can check out their course and the related textbook to go even further on the topic of PGMs.<br><br>
You can find other relevant resources for our course on the [Resources Gingko Page](https://gingkoapp.com/4yf7qa). This list be update as needed throughout the course.
<br><br>
Finally, these notes are still **under construction**! Although we have written up a lot of the material, you will probably find several and errors. If you do, please let us know." %} provide a resource for an introductory course on probabilistic reasoning and decision making.

The field of *Artificial Intelligence* intersects many areas of knowledge which engineers can utilize for building robust, dynamic systems in a world filled with large amounts of data yet also containing uncertainty and hidden information.
In this course we focus from the ground up on the concepts and skills needed to build systems that can reason, learn and make decisions using probabilistic reasoning.
This begins with reviewing concepts from Bayesian probability and learning how to perform probabilistic inference with exact and more efficient approximate methods such as **MCMC**.

In the first half of the course we will explore two practical approaches to utilizing these concepts for reasoning : **Probabilistic Programming and Probabilistic Graphical Models (PGMs)**.
These methods can also be used to reason about decisions, for example using **Influence Diagrams**.
In the second half of the course we will look at how to use a probabilistic model to optimize decisions based on data collected through experimentation or interaction with the environment.
A basic form of this often used for **A/B testing** is **Thompson Sampling** for solving **Multi-Armed Bandit (MAB)** problems where probability distributions and decision making are combined in the simplest way.


**Reinforcement Learning (RL)** is a much more general framework for decision making where we agents learn how to act from their environment without any prior knowledge of how the world works or possible outcomes.
We will explore the classic definitions and algorithms for RL and see how it has been revolutionized in recent years through the use of **Deep Learning**.
Recently, impressive AI algorithms have been demonstrated which combine all of these concepts along with **Monte-Carlo Tree Search** to learn to play video games (such as Star Craft) and board games (such as Go and chess) from scratch.
More practical applications of these methods are used regularly in areas such as customer behaviour modelling, traffic control, automatic server configuration, autonomous driving and robotics.

## Preliminaries

1. [Introduction](preliminaries/introduction/): What is probabilistic graphical modeling? Overview of the course.

2. [Review of probability theory](preliminaries/probabilityreview): Probability distributions. Conditional probability. Random variables.

3. [Examples of real-world applications](preliminaries/applications): Image denoising. RNA structure prediction. Syntactic analysis of sentences. Optical character recognition (*under construction*).

## Representation

1. [Bayesian networks](representation/directed/): Definitions. Representations via directed graphs. Independencies in directed models. 

2. [Markov random fields](representation/undirected/): Undirected vs directed models. Independencies in undirected models. Conditional random fields.

1. [PGM Examples](representation/examples/) 


## Inference

1. [Variable elimination](inference/ve/) The inference problem. Variable elimination. Complexity of inference.

2. (optional) [Belief propagation](inference/jt/): The junction tree algorithm. Exact inference in arbitrary graphs. Loopy Belief Propagation.

3. [MAP inference](inference/map/): Max-sum message passing. Graphcuts. Linear programming relaxations. Dual decomposition. 

4. [Sampling-based inference](inference/sampling/): Monte-Carlo sampling. Forward Sampling. Rejection Sampling. Importance sampling. Markov Chain Monte-Carlo. Applications in inference.

5. [Probabilistic Programming](probprog/basic/): Alternative approach to modelling probability distributions and performing inference. A/B Testing introduction and using MCMC to solve it.

5. (optional) [Variational inference](inference/variational/): Variational lower bounds. Mean Field. Marginal polytope and its relaxations. 

## Learning

1. [Learning in directed models](learning/directed/): Maximum likelihood estimation. Learning theory basics. Maximum likelihood estimators for Bayesian networks.

4. [Bayesian learning](learning/bayesian/): Bayesian paradigm. Conjugate priors. The basics, enough to understand Multi-Armed Bandits (MABs). 

## Decision Making Under Uncertainty
1. [Multi-armed bandits (MAB)](decision/MultiArmedBandits/) : The simplest model of Reinforcement Learning. Example: A/B Testing.
1. Causation vs Correlation: how to model probabilistic causal relationships, relation to decision making   
1. Influence Diagrams: a simple way to add decisions to PGMs
1. **Bayesian Optimization:** Upper Confidence Bounds, Thompson Sampling
1. **Markov Decision Processes (MDPs)**
1. **Monte-Carlo Tree Search:** a way of solving MABs, also useful later for the latest Deep RL solutions

## Deep Reinforcement Learning
1. Basics of Neural Networks: training, back-propagation, gradient descent, regularization methods
1. Deep Learning (training methods, relevant architectures for Reinforcement Learning, fully connected feed forward networks)
1. **Reinforcement Learning (RL):** theory, Bellman equations, Value/Policy Iteration
1. RL Solution Methods: [TD methods](reinforcementlearning/tdlearning), [Q-learning](reinforcementlearning/qlearning), SARSA, policy gradients, [Actor-Critic methods](reinforcementlearning/actorcritic)
1. Function approximation for RL (classic methods, Deep Learning)
1. Deep RL : Deep Q- Networks (DQN), A3C, A2C, …





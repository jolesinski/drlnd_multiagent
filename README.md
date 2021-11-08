Project 3: Collaboration and Competition
=====================

## Introduction
A solution to Tennis Unity Environment - third project in Udacity's [Deep Reinforcement Learning Nanodegree](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893).

## Project details
The task is to train two agents in a collaborative environment, where the agents control rackets to bounce a ball over a net in a game of tennis.

If an agent hits the ball over the net, it receives a reward of +0.1.  If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01.  Thus, the goal of each agent is to keep the ball in play.

The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation.  Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping.

The task is episodic, and in order to solve the environment, your agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents). Specifically,

- After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 2 (potentially different) scores. We then take the maximum of these 2 scores.
- This yields a single **score** for each episode.

The environment is considered solved, when the average (over 100 episodes) of those **scores** is at least +0.5.

```
Number of agents: 20
Size of each action: 4
There are 20 agents. Each observes a state with length: 33
The state for the first agent looks like: [ 0.00000000e+00 -4.00000000e+00  0.00000000e+00  1.00000000e+00
 -0.00000000e+00 -0.00000000e+00 -4.37113883e-08  0.00000000e+00
  0.00000000e+00  0.00000000e+00  0.00000000e+00  0.00000000e+00
  0.00000000e+00  0.00000000e+00 -1.00000000e+01  0.00000000e+00
  1.00000000e+00 -0.00000000e+00 -0.00000000e+00 -4.37113883e-08
  0.00000000e+00  0.00000000e+00  0.00000000e+00  0.00000000e+00
  0.00000000e+00  0.00000000e+00  3.25389481e+00 -1.00000000e+00
  7.30836487e+00  0.00000000e+00  1.00000000e+00  0.00000000e+00
  1.23100638e-01]
```

## Getting Started
In order to setup your Python environment, follow the instructions in the [DRLND GitHub repository](https://github.com/udacity/deep-reinforcement-learning/blob/master/README.md#dependencies). This solution was prepared under Ubuntu 20.04 so take the path for Linux setup.

Apart from Python dependencies, Reacher Unity Environment is automatically fetched by the training notebook.

## Instructions
After dependencies and conda environment setup, start jupyter notebook
```
conda activate drlnd
jupyter notebook
```

In jupyter open [Tennis.ipynb](Tennis.ipynb) and select `drlnd` as active kernel.
Run cells up to "4. Train the agent" section if you want to perform training and save model parameters.
Skip section "4. Train the agent" if you want to load pretrained model and evaluate the agent.
:q!

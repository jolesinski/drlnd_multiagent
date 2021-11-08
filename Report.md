Report for Project 1: Navigation
=====================

A description of solution implementation.

## Learning Algorithm

At first try, A2C [[2]](https://arxiv.org/abs/1602.01783) algorithm with Gaussian policy was used to train the agent but without any success in learning. After that, *Deep Deterministic Policy Gradient (DDPG)* [[1]](https://arxiv.org/abs/1509.02971) learning algorithm, adapted for the multi-agent environment, was used to succesfully train the agent. Both implementations are contained in Continuous_Control.ipynb.

### Hyperparameters used (DDPG):

These set of hyperparamethers and model architecture was used, following suggestions from Udacity's forum:

- `n_episodes = 1000` - max number of episodes during training
- `max_t = 1000` - max number of timesteps in an episode
- `BUFFER_SIZE = 1e5` - size of replay buffer
- `BATCH_SIZE = 128` - minibatch size
- `GAMMA = 0.99` - TD discount factor
- `TAU = 1e-3` - for soft update of target parameters (to have fixed q-targets)
- `LR_ACTOR = 1e-4` - learning rate
- `LR_CRITIC = 1e-3` - learning rate

### Neural network architecture:
#### Actor
 - Linear layer with 33 input features, 100 output features and bias
 - ReLU
 - Batch Normalization
 - Linear layer with 100 input features, 100 output features and bias
 - ReLU
 - Linear layer with 100 input features, 4 output features and bias
 - Tanh

 Trained model weights are stored in `checkpoint_actor.pth` file.

#### Crititc
 - Linear layer with 33 input features, 100 output features and bias
 - ReLU
 - Batch Normalization
 - Linear layer with 100 input features + 4 action features, 100 output features and bias
 - ReLU
 - Linear layer with 100 input features, 1 output feature

 Trained model weights are stored in `checkpoint_critic.pth` file.

## Plot of Rewards

![Plot of rewards of DDPG](ddpg_score.png)

The plot above illustrates that the agent was able able to receive an average reward (over 100 episodes) of at least +30 after the first 136 episodes.

## Ideas for Future Work

Main ideas for fixing the A2C implementation, is to tune model parameter initialization in a way that the state space is truly explored in a monte carlo fashion at the start of learnig. If this helps and the agent starts learnign, further Generalized Advantage Estimation (GAE) [[3]](https://arxiv.org/abs/1506.02438) and Kronecker-Factored Trust Region (ACKTR) [[4]](https://arxiv.org/abs/1708.05144) could be used to improve the algorithm further. Otherwise, a simpler environment with a smaller, easier to learn model could be used to track down any issue with implementation.

For the DDPG implementation, a shared actor-critic model could be used to optimize the model size. Also the three tricks from the Twin Delayed DDPG (TD3) [[5]](https://spinningup.openai.com/en/latest/algorithms/td3.html) could be used to further improve the learing process:
- reduce Q-value overestimation by learning two Q-functions and using the smaller Q-values to form targets
- update policy less frequently than the Q-function
- smooth Q-values by adding clipped noise to the target action
The implementation details can be found in OpenAI blog [post](https://spinningup.openai.com/en/latest/algorithms/td3.html).

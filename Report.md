# Report

[//]: # (Image References)

[image1]: https://githhub.com/Apunti/RL-Udacity-Navigation/blob/master/images/plot.png "Plot"
[image2]: https://githhub.com/Apunti/RL-Udacity-Navigation/blob/master/images/log.png "Log"

# Learning algorithm

The algorithm implemented in this project is the DQN presented in [this paper](https://arxiv.org/pdf/1312.5602.pdf). The model consists of 4 connected layers. The first three have Relu activation while the output layer has no activation layer applied. I have also added a three Dropout layers with a probability of 0.25. The weights of the network are updated with the method soft_update, that gradually brings closer the target network to the local.

The main idea behind Q-learning is that if we had a function Q∗:State×Action→R, that could tell us what our return would be, if we were to take an action in a given state, then we could easily construct a policy that maximizes our rewards. The DQN overcomes unstable learning by mainly 2 techniques:

- Experience Replay.
- Target Network.

For further information on DQN refer to [this page](https://towardsdatascience.com/welcome-to-deep-reinforcement-learning-part-1-dqn-c3cab4d41b6b).

The model architecture consists of 4 fully connected layers, the output layer without an activation function and the others with leaky relu activation. I added three dropout layers with probability 0.25. The hidden size for all the layers is 64.

The hyperparameters used to train the agent are the following.

- BUFFER_SIZE = 1e
- BATCH_SIZE = 64
- GAMMA = 0.99
- TAU = 0.001
- LR = 5e-4
- UPDATE_EVERY = 10

# Plot of rewards

![Plot][image1]
![Log][image2]

We can see that the environment is solved around the episode 1800.

# Ideas for Future Work

Firstly, we could try changing the hyperparameters to make the model converge faster. By increasing tau we can get a model that converges faster, but it doesn't has the same performance. Moreover, we could try to add prioritized experience replay. For now, the model takes a random sample from the buffer, but by using prioritized experience replay, the model should converge faster. Another thing to consider is reducing the number of hidden layers from four to three. Maybe it is not needed too many parameters for this environment.

On the other hand, we could implement other enhancements:

- Dueling DQN
- Double DQN

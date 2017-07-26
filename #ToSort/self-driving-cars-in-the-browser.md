# Self-driving cars in the browser

_Captured: 2017-03-21 at 01:44 from [janhuenermann.com](http://janhuenermann.com/projects/learning-to-drive)_

The goal of this project was to create a fully self-learning agent, that would be able to control a car in a 2D bottom-down environment. Written solely in JavaScript.

The demo is loading and is ready in one second...

_Note: this works only in modern browsers, so make sure you are on the newest version_ 🤘

This is a project I have been working on for quite some time now. These cars learned how to drive by themselves. They got feedback on what good and what bad actions are based on their current speed as a form of reward. Powered by a neural network.

You can drag the mouse to draw obstacles, which the cars must avoid. Play around with this demo and get excited about machine learning!

The following is a more detailed description of how this works. You may stop reading here and just play with the demo if you're not interested in the technical background!

### Concepts

A short introduction to a few reinforcement learning concepts.

**Agent**: The agent, in this case, is the driver of the car.  
**Action**: At each timestep the agent has to take an action. This may for example be steering left, going faster or braking.  
**State**: The state is a collection of numbers that describe the environment the agent is currently in. It contains the information the agent uses to make a reasonable decision on what to do. After each action the state is updated to reflect the changes in the environment.  
**Reward**: After taking an action in a state, the agent receives a reward, which describes how good the action he took was. The goal of the agent is to maximise this reward.  
**Reinforcement learning**: Learning what actions to take in order to maximise a given reward function.

### Neural networks

The agents learn by adjusting the weights of their neural network (function approximators). In this case, this involves two neural networks: one state to action net (3-layer, 150 neurons), one state + action to q-value net (2-layer, 200 neurons). The q-value describes how good an action is. By learning the second network, "the value network", you can obtain policy gradients, which you can then use to learn the first network. The first network, "the actor network", is now your decision maker. This algorithm is called "Deep Deterministic Policy gradient" or in short DDPG. Combining this with state-of-the-art techniques, such as prioritised experience replay buffers, ReLU non-linearites and the Adam learner, results in the cars you can see above. Even though this, at first, might seem reasonable, a lot of trouble with neural networks these days is the hyper-parameter search. There are at least a dozen of parameters you need to tune in order to achieve optimal results, which is kind of a drawback. In the future this might be overcome by automatic hyper-parameter search, which iterates over a set of hyper-parameters and finds the best.

Note however, that the demo you see above doesn't train the neural networks, therefore they are not learning (this is done offline).

### Sensors

The state (or the input to the neural nets) of the agent consists of two time-steps, the current time-step and the previous time-step. This helps the agent make decisions based on how things moved over time. For each time-step the agent receives information about its environment. This includes 19-distance sensors, which are arranged in different angles. You can think of these sensors as beams, that stop when they hit an object. The shorter the beam, the higher the input to the agent (0 - for no hit, 1 - for a very short beam). In addition, a time-step contains the current speed of the agent. In total, the input to the neural networks is 158-dimensional.

Imagine sitting in a room with a computer, looking at 158-numbers on the screen and having to press left or right in order to increase some kind of number, namely the reward. That is what this agent is doing. Isn't that crazy?

### Exploration

A major issue with DDPG is exploration. In regular DQN (deep Q-networks) you have discrete actions from which you can choose from. So you can easily mix up your action-state-space by epsilon-greedily randomising actions. In continuous spaces (as the case with DDPG) this is not as easy. In this project I used dropout as a way to explore. This means dropping some neurons of the last layer of the actor network randomly and therefore obtaining some kind of variation in actions.

### Multi-agent learning

In addition to applying dropout to the actor network, I put 4 agents into the virtual environment at the same time. All these agents share the same value network, but have different actors and therefore have different approaches to different states, thus every agent explores different areas of the state-action space. All in all this resulted in better and faster convergence.

The code for the demo above along with the JavaScript library I made is available on [GitHub](https://github.com/janhuenermann/neurojs). If you want to hear more on the progress of the project as I add new features, I encourage you to follow me on Twitter [@janhuenermann](https://twitter.com/janhuenermann)! Additionally feel free to share the project in social media, so more people can get excited about AI!

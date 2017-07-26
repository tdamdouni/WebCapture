# How AI Differs From ML

_Captured: 2017-07-07 at 06:51 from [dzone.com](https://dzone.com/articles/how-ai-differs-from-ml?edition=306234&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-06)_

AI is not a new term. It is multiple decades old, starting around the early 80s when computer scientists designed algorithms that could learn and mimic human behavior.

On the learning side, the most significant algorithm is the neural network, which is not very successful due to overfitting (the model is too powerful and there's not enough data). Nevertheless, in some more specific tasks, the idea of using data to fit a function has gained significant success and this form the foundation of machine learning today.

On the mimicking side, AI has focused a lot on image recognition, speech recognition, and natural language processing. Experts have been spending a tremendous amount of time creating features like edge detection, color profiles, N-grams, syntax trees, etc. Nevertheless, the success has been moderate.

## Traditional Machine Learning

Machine learning (ML) techniques have played a significant role in prediction, and ML has undergone multiple generations to have a rich set of model structures such as:

  * Linear regression.
  * Logistic regression.
  * Decision tree.
  * Support vector machine.
  * Bayesian model.
  * Regularization model.
  * Ensemble model.
  * Neural network.

Each of these predictive models is based on certain algorithmic structure, with parameters as tunable knobs. Training a predictive model involves the following steps:

  1. **Choose a model structure** (for example, logistic regression, random forest, etc.).
  2. **Feed the model with training data** (both input and output).
  3. **The learning algorithm will output the optimal model** (i.e. a model with specific parameters that minimize the training errors).

Each model has its own characteristics and will perform well in some tasks and badly in others. But generally, we can group them into the low-power (simple) model and the high-power (complex) model. Choose between different models is a very tricky question.

Traditionally, using a low power/simple model is preferred over the use of a high power/complex model for the following reasons

  * Until we have a massive processing power, training the high power model will take too long.
  * Until we have a massive amount of data, training the high power model will cause the overfitting problem (since the high power model has rich parameters and can fit into a wide range of data shape, we may end up train a model that fits too specific to the current training data and not generalized enough to do good prediction on future data).

However, choosing a low power model suffers from the so-called "under-fit" problem where the model structure is too simple and unable to fit the training data in case it is more complex. (Imagine the underlying data has a quadratic relationship: y = 5 * x^2; there is no way you can fit a linear regression: y = a*x + b, no matter what a and b we pick.)

To mitigate the "under-fit problem," data scientists will typically apply their "domain knowledge" to come up with "input features," which has a more direct relationship with the output. (For example, going back to the quadratic relationship y = 5 * square(x), if you create a feature z = x^2, then you can fit a linear regression: y = a*z + b, by picking a = 5 and b = 0.)

A major obstacle to machine learning is this feature engineering step, which requires domain experts to identify important signals before feeding into the training process. The feature engineering step is very manual and demands a lot of scarce domain expertise and therefore becomes a major bottleneck of most machine learning tasks today.

In other words, if we don't have enough processing power and enough data, then we have to use the low-power/simpler model, which requires us to spend significant time and effort to create appropriate input features. This is where most data scientists spending their time doing today.

## Return of the Neural Network

In the early 2000s, machine processing power has increased tremendously, with the advancement of cloud computing and massively parallel processing infrastructure together in the big data era where a massive amount of fine-grained event data being collected. We are no longer restricted to the low-power/simple model. For example, the two most popular mainstream machine learning models today are the random forest and gradient boosting trees. Nevertheless, although both of them are very powerful and provide non-linear model fitting to training data, data scientists still need to carefully create features in order to achieve good performance.

At the same time, computer scientists have revisited using many layers of the neural network in doing these human mimicking tasks. This gives new birth to the DNN (deep neural network) and provides a significant breakthrough in image classification and speech recognition tasks. The major difference in DNN is that you can feed the raw signals (for example, the RGB pixel value) directly into DNN without creating any domain specific input features. Through many layers of neurons (which is why it is called a "deep" neural network), DNN can "automatically" generate the appropriate features through each layer and finally provide a very good prediction. This saves significantly the "feature engineering" effort, a major bottleneck done by the data scientists.

DNN also evolves into many different network topology structure, so we have CNN (Convolutional Neural Network), RNN (Recurrent Neural Network), LSTM (Long Short Term Memory), GAN (Generative Adversarial Network), Transfer Learning, Attention Model... etc. The whole spectrum is called Deep Learning, which is catching the whole machine learning community's attention today.

## Reinforcement Learning

Another key component is about how to mimic a person (or animal) learn. Imagine the very natural animal behavior of perceive/act/reward cycle. A person or animal will first understand the environment by sensing what "state" he or she is in. Based on that, he or she will pick an "action" that brings him or her to another "state." Then he or she will receive a "reward." The cycle repeats until he or she dies. This way of learning (called reinforcement learning) is quite different from the curve-fitting approaches of traditional supervised machine learning. In particular, reinforced learning happens very quickly because each new feedback (such as perform an action and receive a reward) is sent immediately to influence subsequent decisions. Reinforcement learning has gained tremendous success in self-driving cars as well as AlphaGO (a chess-playing robot).

Reinforcement Learning also provides a smooth integration of prediction and optimization because it maintains a belief of current state and possible transition probabilities when taking different actions, and then make decisions which action can lead to the best outcome.

## Deep Learning + Reinforcement Learning = AI

Compared to the classic ML technique, DL provides a more powerful prediction model that usually produces good predictions. Compared to the classic optimization model, reinforcement learning provides a much faster learning mechanism and is also more adaptive to changes in the environment.

Topics:

ai ,deep learning ,machine learning ,neural networks ,predictive modeling

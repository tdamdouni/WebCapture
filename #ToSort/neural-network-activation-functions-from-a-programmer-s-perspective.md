# Neural Network Activation Functions From a Programmer's Perspective

_Captured: 2017-08-08 at 20:23 from [dzone.com](https://dzone.com/articles/designing-a-neural-network-in-java-activation-func?edition=310395&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-23)_

This post is the second part of series of articles discussing an approach to programming a neural network using Java in a simple and understandable way.

In the [previous post](https://dzone.com/articles/designing-a-neural-network-in-java), we defined the main components of a neural network and designed them using Java as a programming language. In this post, we will dive deeper into the activation function (also called transfer function) as part of the neural networks.

To recall from the [first part](https://dzone.com/articles/designing-a-neural-network-in-java) of this series, an artificial neuron is a signal collector in the inputs and an activation unit in the output triggering a signal that will be forwarded to other neurons as shown in the following picture:

![Image title](https://dzone.com/storage/temp/5953103-artificialneuron.jpg)

The artificial neuron receives one or more inputs and sums them to produce an output or activation. Usually, the sums of each node are weighted and the sum is passed through an activation function. In most cases, it is the _nonlinear_ activation function that allows such networks to compute nontrivial problems using only a small number of nodes.

In biologically inspired neural networks, the activation function is usually an abstraction representing the rate of action potential firing in the cell. Using Java as a programming language, this abstraction can be designed using an activation function interface:

The implementations of this interface will provide a way to easily experiment with and replace various types of activation functions. Let's start implementing them!

## **Step Function**

The simplest form of activation function is binary -- the neuron is either firing or not. The output _y_ of this activation function is binary, depending on whether the input meets a specified threshold, _θ_. The "signal" is sent, i.e. the output is set to one if the activation meets the threshold.

This function is used in [perceptrons](https://en.wikipedia.org/wiki/Perceptron). It performs a division of the space of inputs by a hyperplane. It is especially useful in the last layer of a network intended to perform binary classification of the inputs.

## **Linear Combination**

A linear combination is where the weighted sum input of the neuron is summed up with a linearly dependent bias to build the neuron's output. A number of such linear neurons performs a linear transformation of the input vector. This is usually more useful in the first layers of a network.

## **Sigmoid Function**

The Sigmoid function (also a logistic function) is calculated using the following formula:

In this formula, the weighted input is multiplied by a slope parameter.

## **Sinusoid Function**

The Sinusoid activation function is based on calculating the sinus of the weighted input.

## **Rectified Linear Unit**

This function is also known as a ramp function. According [Wikipedia](https://en.wikipedia.org/wiki/Rectifier_\(neural_networks\)):

> It has been used in convolutional networks more effectively than the widely used logistic sigmoid and its more practical counterpart, the hyperbolic tangent (not covered in this article). The rectifier is, as of 2015, the most popular activation function for deep neural networks. 

[Wikipedia](https://en.wikipedia.org/wiki/Activation_function) also states that there are various activation functions that might be applied in neural networks, this article presented some of them implemented in Java. Their number will be further extended in next articles presenting applications of various types, as well as the learning process in neural networks.

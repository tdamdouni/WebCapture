# 5 Things You Should Know About Deep Learning

_Captured: 2017-05-17 at 20:52 from [dzone.com](https://dzone.com/articles/5-things-you-should-know-about-deep-learning?oid=twitter&utm_content=buffer636b9&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Need to build an application around your data? [Learn more](https://dzone.com/go?i=200129&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) about dataflow programming for rapid development and greater creativity.

The field Deep Learning is only going to continue to grow. Read on for five of the most important things you should know about Deep Learning.

## **1\. Deep Learning Is Not Magic**

DL (Deep Learning) covers a very large area and is very complex to understand. DL is often compared to the process of learning that occurs in the human brain. Similarly, DL is also based on the use of neural networks. Artificial neural networks actually try to imitate the brain's activity.  
A baby only a few months old learns to identify visual content by viewing samples and from the labeling she is exposed to from the human beings around her. For example, as time passes, she understands that a man usually has short hair as opposed to a woman whose hair is usually longer and whose facial features tend to be more delicate. With exposure to a growing number of examples, she learns to recognize even more refined details that differentiate between males and females.

Eventually, an adult is able to understand visual content according to the training process they've undergone during childhood and life. For example, if they've has seen many different types of birds, they'll be able to name them properly as opposed to someone who has seen a smaller sample who will be limited in their ability to classify birds.

A major problem in teaching a network using Deep Learning is providing a high-quality, extensive-as-possible sample collection. This is actually one of the major challenges in the training of neural networks. Another difficulty lies at the basic level of deciding what the model should understand.  
There are many visual examples that are similar. A few simple examples are:

  * A labrador is very similar to a golden retriever. Do we have to differentiate between them or is it enough to just identify both as hounds?
  * There are many different types of drinking glasses that are very different from each other in look and color. It will be difficult to teach the model what a glass is. We will have to split the categories into wine glasses, beer glasses, etc.

It is very important to decide this at the beginning stages, as each such decision affects what is being taught and what training set is used. This will have extensive implications on the model's behavior and accuracy.

## **2\. Use Existing Frameworks**

The DL world is evolving meteorically and there is a wide range of platforms and infrastructures used for training models. Most tools are free and the documentation is relatively comprehensive. Some central frameworks are Caffe, Theano, and Google's TensorFlow. Another positive point is that both the academic world and the industry use the same tools, so it's relatively easy to use tools from the academic world.

## **3\. GPU Is Better Than CPU**

Training a neural model for Deep Learning requires many hardware resources, including serious processing power to perform repetitive iterations to update the model in accordance with the samples it's working on. The mathematical calculations that take place during training are relatively simple but there is a huge number of such calculations going on at the same time.

The difference between CPU and GPU is mainly the number and strength of the processors. CPU usually has a few (a few dozen at best) strong processors as opposed to GPU, which has many (thousands) of relatively weak processors. For this reason, it is better to do parallel training on the GPU. To illustrate this point, training that takes only five days on the GPU could take months on the CPU.

The bad news is that GPUs are expensive. A GPU with thousands of processing units could cost thousands of dollars just for the graphics card. And there may also be a need for dedicated servers for the graphics card, which would involve additional expenditure.

## **4\. Using Existing Models**

One of the burning questions in the field of DL is: _Is it possible to use a certain model to train another model?_ The answer is that it depends.

In certain situations, a model that specializes in a specific field can be adapted to understanding a different field. The closer the fields are, the easier it is to train a model to understand another field. For example, a model that specializes in facial recognition can serve as a basis for a model that recognizes gender. This is called transfer learning. Similarly, in the human brain, areas that are near each other understand similar visual content.

The field of transfer learning is very important and interesting as it can assist in decreasing the number of samples needed train similar/close models.

## **5\. The Challenge: Preparing the Training Set**

The most challenging part in training a model is the collection of the large amounts of data necessary to teach the model how to understand a certain picture. For example, if we want to teach the concept of basketball to a model, the first problem would be defining "basketball," as there are many kinds of basketball -- professional, children's, women, men, street ball, etc. It's necessary to see what is it takes to understand a specific category.

Then, we have to collect as many pictures as possible that represent the category we want to teach. This leads us to the question, _which picture represents the category and which does not?_ The answer is not always clear.

Thanks to Lior Cohen.

[Check out](https://dzone.com/go?i=200130&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) the Exaptive data application Studio. Technology agnostic. No glue code. Use what you know and rely on the community for what you don't. [Try the community version](https://dzone.com/go?i=200130&u=https%3A%2F%2Fexaptive.city%2F%23%2Flanding%3Freferrer%3DGeneral).

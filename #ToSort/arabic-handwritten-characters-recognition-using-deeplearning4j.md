# Arabic Handwritten Characters Recognition using Deeplearning4j

_Captured: 2017-10-25 at 18:38 from [www.emaraic.com](http://www.emaraic.com/blog/arabic-characters-recognition)_

### Introduction

Due to the variety of human handwritten styles, the handwritten character recognition system faces some challenges. The authors of the paper (Arabic Handwritten Characters Recognition using Convolutional Neural Network) I built my work on it, introduce a suggested model for the handwritten Arabic character recognition problem using Convolution Neural Network (CNN). They trained their network on a dataset contains 16800 examples of hand written Arabic characters and it gave them an accuracy of 94.9% on testing data.

###  Requirements

  1. Install Java Development Kit 8 (JDK 8).
  2. Install Netbeans.
  3. Source code from <https://github.com/emara-geek/arabic-characters-recognition>.

### Proposed Approach

The proposed CNN design consists of layers as shown in fig. 1 (INPUT -> CONV->RELU->POOL->CONV->RELU-> POOL -> FC -> RELU -> FC). "For one direction in a channel (feature map) of the convolutional layer C1, the output is ((32-5) +1) = 28. The max pooling layer S2 has non-overlapping regions, so it down-samples by 2 in each direction, the output is 28/2 = 14. For one direction in a channel (feature map) of the convolutional layer C3, the output is ((14-5) +1 = 10. The max pooling layer S4 has non-overlapping regions, so it down-samples by 2 in each direction, the output is 10/2 = 5 on fourth layer. The output image size of max pooling layer is 5 * 5 = 25. There are 64 channels in the convolutional layer and the same in pooling layer, so the total output of the max pooling layer is 25 * 128 = 1600. This is the size of the input to the fully connected layer FC5. Layer FC6 (Output), contain 28 units and is fully connected to FC5. Finally, the FC6 is composed of softmax classifier to produce 28 output class."See Reference

![](http://www.emaraic.com/assets/img/posts/machine-learning/arabic-char-recognition.png)

### Dataset

The dataset they used consists of 16,800 characters written by 60 participants, the age range is between 19 to 40 years, and 90% of participants are right-hand. The database is partitioned into two sets: a training set (13,440 characters to 480 images per class) and a test set (3,360 characters to 120 images per class). Their dataset is available from [here](https://github.com/mloey/Arabic-Handwritten-Characters-Dataset), I used their dataset but, I combine the data with its labels in the same file.

### Implementation

I implemented this proposed CNN using Deeplearning4j (Distributed deep-learning library written for Java) and trained it with dataset, this is done by class ModelGenerator.java which trains the dataset and serializes the generated model to file (model.data). This model give a 91.137% accuracy (last update of this model gives 92.29%). The class TestModel.java is provided to test the generated model and using samples in (test_images) folder. I also provide a GUI application (ArabicCharactersRecognition.jar) in recogniser_executable folder, developed in java to test the generated model and it gives the best three scores for the input character.

![](http://www.emaraic.com/assets/img/posts/machine-learning/alef.png)

![](http://www.emaraic.com/assets/img/posts/machine-learning/seen.png)

> _Testing character Seen "س" with app._

## Arabic Handwritten Characters Recognition using CNN

### References

  * El-Sawy, A., Loey, M., & Hazem, E. B. Arabic Handwritten Characters Recognition using Convolutional Neural Network.

> _Figure 1: The proposed CNN for Arabic handwritten character recognition ._

# Deep learning based Object Detection and Instance Segmentation using Mask R-CNN in OpenCV (Python / C++)

_Captured: 2018-12-09 at 16:47 from [www.learnopencv.com](https://www.learnopencv.com/deep-learning-based-object-detection-and-instance-segmentation-using-mask-r-cnn-in-opencv-python-c/)_

A few weeks back we wrote a post on [Object detection using YOLOv3](https://www.learnopencv.com/deep-learning-based-object-detection-using-yolov3-with-opencv-python-c/).

The output of an object detector is an array of bounding boxes around objects detected in the image or video frame, but we do not get any clue about the shape of the object inside the bounding box.

Wouldn't it be cool if we could find a binary mask containing the object instead of just the bounding box?

In this post, we will learn how to do just that. We will show how to use a Convolutional Neural Network (CNN) model called Mask-RCNN (Region based Convolutional Neural Network) for object detection and segmentation. Using Mask-RCNN we not only detect the object, we also obtain a greyscale or binary mask containing the object.

The results in this tutorial are obtained using a Mac OS **2.5 GHz Intel Core i7 CPU**. The inference time is from **350 ms to 2 seconds per frame** on the CPU, depending on the complexity and number of objects in the frame.

[Mask-RCNN](https://arxiv.org/pdf/1703.06870.pdf) was initially introduced in Nov 2017 by Facebook's AI Research team using [Python and Caffe2](https://github.com/facebookresearch/Detectron).

It was later ported to Tensorflow and several pre-trained models with different backbone architectures like InceptionV2, ResNet50, ResNet101, and Inception-ResnetV2 were shared in the [Object Detection Model Zoo](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/detection_model_zoo.md). They also provide you tools to [train your own models](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/instance_segmentation.md).

The **Inception** backbone is the fastest of the four. You can even try it on a **CPU** in a reasonable time and therefore we have chosen it for this tutorial. This model was trained on **MSCOCO** dataset.

We will share OpenCV code to load and use the model in both C++ and Python.

Before we dive into the code, it is worth understanding a few terms especially if you are a beginner.

##  What is Image Segmentation?

In computer vision, the term "image segmentation" or simply "segmentation" means dividing the image into groups of pixels based on some criteria. You can do this grouping based on color, texture, or some other criteria that you have decided. These groups are sometimes also called _super-pixels_.

###  What is instance segmentation?

In **instance segmentation** the goal is to detect specific objects in an image and create a mask around the object of interest. Instance segmentation can also be thought as object detection where the output is a mask instead of just a bounding box. Unlike **semantic segmentation**, which tries to categorize each pixel in the image, instance segmentation does not aim to label every pixel in the image.

Below we see an example of instance segmentation of two sheep on a very similar colored background.

![](https://www.learnopencv.com/wp-content/uploads/2018/10/Mask-RCNN-results-1024x290.png)

_Figure 1 : Instance Segmentation Example_

## How Mask-RCNN works?

Mask-RCNN is a result of a series of improvements over the original R-CNN paper (by R. Girshick et. al., CVPR 2014) for object detection. [R-CNN](https://arxiv.org/abs/1311.2524) generated region proposals based on selective search and then processed each proposed region, one at time, using Convolutional Networks to output an object label and its bounding box.

[Fast R-CNN](https://arxiv.org/pdf/1504.08083.pdf) ( R. Girshik, ICCV 2015) made the R-CNN algorithm much faster by processing all the proposed regions together in their CNN using a ROIPool layer.

[Faster R-CNN](https://arxiv.org/pdf/1506.01497.pdf) (S. Run et al., PAMI, 2017 ) pushed it even further by performing the region proposal step too using a ConvNet called Region Proposal Network(RPN). Both the RPN, and the classification and bounding box prediction network worked on common feature maps, thus making inference faster. On a GPU, Faster R-CNN could run at 5 fps.

[Mask R-CNN](https://arxiv.org/pdf/1703.06870.pdf) (He et al., ICCV 2017) is an improvement over Faster RCNN by including a mask predicting branch parallel to the class label and bounding box prediction branch as shown in the image below. It adds only a small overhead to the Faster R-CNN network and hence can still run at 5 fps on a GPU. In this tutorial we show results by running on a Mac OS 2.5 GHz Intel Core i7 CPU and it takes around 2 seconds per frame on the CPU, even for the frames with more than 30 objects.

![Mask RCNN Framework](https://www.learnopencv.com/wp-content/uploads/2018/09/mask-rcnn-framework.png)

_Figure 2 : Architecture of Mask-RCNN ([Source](https://arxiv.org/pdf/1703.06870.pdf))_

The Mask-RCNN network has two major parts.

The first one is the Region Proposal Network which generates around 300 region proposals per image. During training, each of these proposals (ROIs) go through the second part which is the object detection and mask prediction network, as shown above. Note that since the mask prediction branch runs in parallel to the label and box prediction branch, for each given ROI, the network predicts masks belonging to all the classes.

During inference, the region proposals go through Non-Maximum Suppression and only the top scoring 100 detection boxes are processed by the mask prediction branch. So, with 100 ROIs and 90 object classes, the mask prediction part of the network outputs a 4D tensor of size 100x90x15x15, where each mask is of size 15×15.

For the sheep image shown above, the network detected two objects. For each object it outputs an array containing the predicted class score(indicating the probability that the object belongs to the predicted class), left, top, right and bottom locations of the bounding box of the detected object in the frame. The class id from this array is used to extract the corresponding mask from the output of the mask prediction branch. The masks for the two objects detected look like the following:

![sheep masks](https://www.learnopencv.com/wp-content/uploads/2018/09/sheep-masks.png)

_Figure 3 : Masks produced by Mask-RCNN_

These masks can then be thresholded to get a completely binary mask.

Like Faster-RCNN, the choice of the backbone architecture is flexible. We chose InceptionV2 because it is faster, but one could get better results with better architectures like ResNeXt-101, as pointed by the authors of the [Mask R-CNN](https://arxiv.org/pdf/1703.06870.pdf) paper.

Compared to other object detectors like YOLOv3, the network of Mask-RCNN runs on larger images. The network resizes the input images such that the smaller side is 800 pixels. Below we will go in detail the steps needed to get instance segmentation results. For simplicity and clarity of visualization, we use the same color to indicate objects of the same class in the above video, but we also show a minor code change to color different instances differently.

## Object Detection and Instance Segmentation using Mask-RCNN in OpenCV (C++/Python)

Let us now see how to run Mask-RCNN using OpenCV.

** Download Code**  
To easily follow along this tutorial, please download code by clicking on the button below. It's FREE!

### Step 1 : Download the models

We will start by downloading the tensorflow model to the current Mask-RCNN working directory. After the download is complete we extract the model files. We will be using the frozen graph file **frozen_inference_graph.pb** to get the model weights.

### Step 2 : Initialize the parameters

The Mask-RCNN algorithm produces the predicted detection outputs as the bounding boxes. Each bounding box is associated with a confidence score. All the boxes below the confidence threshold parameter are ignored for further processing.

The object mask output from the network is a greyscale image. One could use it directly for alpha blending purposes, if needed. Since we use binary masks in this tutorial, we use the maskThreshold parameter to threshold the grey mask image. Lowering its value would result in a larger mask. Sometimes this helps include the parts missed near the boundaries, but at the same time, it might also include the background pixels at the more pointy boundary regions.

##### Python

##### C++

### Step 3 : Load the model and classes

The file **mscoco_labels.names** contains all the objects for which the model was trained. We read class names. Then we read and load the **colors.txt** file containing all the colors used to mask objects of various classes.

Next, we load the network using these two files --

  1. **frozen_inference_graph.pb** : The pre-trained weights.
  2. **mask_rcnn_inception_v2_coco_2018_01_28.pbtxt** : The text graph file that has been tuned by the OpenCV's DNN support group, so that the network can be loaded using OpenCV.

We set the DNN backend to OpenCV here and the target to CPU. You could try setting the preferable target to **cv.dnn.DNN_TARGET_OPENCL** to run it on a GPU. But keep in mind that the DNN module in the current OpenCV version is tested only with Intel's GPUs.

##### Python

##### C++

### Step 4 : Read the input

In this step we read the image, video stream or the webcam. In addition, we also open the video writer to save the frames with detected output bounding boxes.

##### Python

##### C++

### Step 4 : Process each frame

The input image to a neural network needs to be in a certain format called a **blob**.

After a frame is read from the input image or video stream, it is passed through the **blobFromImage** function to convert it to an **input blob** for the neural network. In this process, it takes in the input image frame in its original size and sets the swapRGB parameter to true.

The blob is then passed in to the network as its input and a forward pass is run to get a list of predicted bounding boxes and the object masks from the output layers named as '**detection_out_final**' and '**detection_masks**' in the network. These boxes go through a post-processing step in order to filter out the ones with low confidence scores. We will go through the post-processing step in more detail in the next section. The inference time for each frame is printed out at the top left. The image with the final bounding boxes and the corresponding overlaid masks is then saved to the disk, either as an image for an image input or using a video writer for the input video stream or webcam.

##### C++

Now lets go into details of some of the postprocess function call used above.

#### Step 4a : Post-processing the network's output

The network's output masks object is a 4-dimensional object, where the first dimension represents the number of detected boxes in the frame, the second dimension represents the number of classes in the model and the third and fourth dimensions represent the mask shape(15×15) in our example.

If the confidence of a box is less than the given threshold, the bounding box is dropped and not considered for further processing.

##### Python

##### C++

#### Step 4c : Draw the predicted boxes

Finally, we draw the boxes that were filtered through the post-processing step, on the input frame with their assigned class label and confidence scores. We also overlay the colored masks along with their contours inside the boxes. In this code, we used the same color for all the objects belonging to the same class, but you could color the different instances differently too.

##### Python

##### C++

## Subscribe & Download Code

If you liked this article and would like to download code (C++ and Python) and example images used in this post, please [subscribe](https://bigvisionllc.lpages.co/leadbox/143948b73f72a2%3A173c9390c346dc/5649050225344512/) to our newsletter. You will also receive a free [Computer Vision Resource](https://bigvisionllc.lpages.co/leadbox/143948b73f72a2%3A173c9390c346dc/5649050225344512/) Guide. In our newsletter, we share OpenCV tutorials and examples written in C++/Python, and Computer Vision and Machine Learning algorithms and news.

## References:

We used the images and video clips from the following sources:  
Pixabay: [[1]](https://pixabay.com/en/sheep-meadow-pasture-water-sea-1674623/), [[4]](https://pixabay.com/en/videos/black-bear-bear-baby-yukon-canada-3330/),  
Pexels: [[1]](https://videos.pexels.com/videos/time-lapse-video-of-runners-855789), [[2]](https://videos.pexels.com/videos/airplane-take-off-855130), [[3]](https://videos.pexels.com/videos/cars-on-highway-854671)

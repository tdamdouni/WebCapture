# Internship at itemis: Robocar showcase of machine learning

_Captured: 2018-04-25 at 20:12 from [blogs.itemis.com](https://blogs.itemis.com/en/internship-at-itemis-robocar-showcase-of-machine-learning?utm_campaign=Software%20Development&utm_source=hs_email&utm_medium=email&utm_content=62369597&_hsenc=p2ANqtz-_NvMvcT85ZqZRCTUzXeAEKHJCpU7tMmDkDANAzZRZ3Iib4P1yvIhAq8l9eVstPw9JhbrFmORL6OPtRwpgTdDZYJ7Z_lA&_hsmi=62369597)_

At itemis, we are involved in automotive software projects in terms of modeling (domain specific languages for architecture and behavior), tooling (architecture, feature models, implementation, Machine Learning) and concepts/standards (AUTOSAR, Genivi, openADX).   
At our office in Stuttgart, we wanted to set up a tangible demonstrator - a robocar platform as a flexible base with an initial showcase of machine learning.

The [Sunfounder Smart Video Car Kit](https://www.sunfounder.com/rpi-car.html) was sitting on my desk for quite a while without even being unboxed. Fortunately, our intern Julian applied for an internship after finishing school. So we set some goals for the internship:

  * Assemble the Robocar Kit
  * Implement software to control the car remotely with an Xbox controller
  * Implement software to record the camera and associate it with the steering angle
  * Train a neural network with the recorded data
  * Implement software to feed the live image to the trained neuronal network and steer the car automatically.

## Assembly of the Sunfounder Smart Video Car

The Sunfounder Smart Video Car is quite easy to assemble. However, to be able to use it to drive automatically, we had to make some changes:

  * Replace the camera with a fish-eye camera. Otherwise not enough of the lane markings are visible in the vicinity of the car.
  * Put the camera much higher, so that it can point downwards and get a better view
  * Put the Raspberry Pi on stand-offs so that we can position the Xbox receiver.

The modified car looks like this:

![20180320_111555](https://blogs.itemis.com/hs-fs/hubfs/20180320_111555.jpg?t=1524666893193&width=12096&height=9072&name=20180320_111555.jpg)

##   
The software

The Raspberry PI that sits on top of the car runs Ubuntu Mate Linux. The software consists of a component that controls the car's steering angle and speed by reading the XBox controller. At the same time, pictures from the camera are being read with the OpenCV library and each image is stored with the angle and speed as part of its file name.

![capture_10_0.0_0.83](https://blogs.itemis.com/hs-fs/hubfs/capture_10_0.0_0.83.png?t=1524666893193&width=2172&height=1539&name=capture_10_0.0_0.83.png)

The autonomous driving approach was inspired by the [Udacity Behavioral Cloning project](https://medium.com/@ksakmann/behavioral-cloning-make-a-car-drive-like-yourself-dc6021152713). The idea is, that a neural network learns from the recordings, which steering angle to apply for images. Our training was done on a standard Notebook with Keras on a Nvidia GPU. The trained model was transferred to the Raspberry PI, where the Python-based controller software was executed.

## Next Steps

The current software is quite simple and consists of a few Python scripts. Next steps would be to apply state-of-the art technologies, such as adaptive AUTOSAR, ROS, DDS etc. Perfect tasks for potential new working students. And Julian, our intern, got so interested in automotive software engineering, that he plans to study that so he can try all this on real cars.

# Using Apple's Machine Learning for License Plate Recognition

_Captured: 2018-03-10 at 19:42 from [dzone.com](https://dzone.com/articles/using-apples-machine-learning-for-license-plate-re?edition=365236&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-10)_

Insight for I&O leaders on deploying AIOps platforms to enhance performance monitoring today. [Read the Guide](https://dzone.com/go?i=260321&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2Fgartner-market-guide-for-aiops-platforms-2017.html%3Fcid%3Dpt-PA_STA_All_FC_PT_Gartner_AIOps_Market_Guide_Dzone_Analyst_Report-AB-03-f-08232017%26cc%3Dpt%26elqcid%3D4114%26sfcid%3D7011O0000027wFd).

Apple's Machine Learning framework, released a few months ago, is inspiring leading businesses to build more intelligent applications that can perform complex functions with ease. License Plate Recognition is one such application that can be built using this framework. In this post, we will guide you on building an application that can effectively recognize license plates and prove significant for use across industries such as security, transport, and insurance.

Before we delve into the specifics of this application, let's look into understanding the concept of License Plate Recognition and Apple's Machine Learning framework.

## **Understanding License Plate Recognition**

It is a process of recognizing number plates using Optical Character Recognition (or OCR) on images. Here, the OCR undertakes recognition of the printed text or images using a three-step process called DCR: Detect, Capture, and Recognize.

Machine learning (ML) essentially implies a phenomenon in which the machine has the capability to learn and deliver relevant yet better experiences. It is a branch of artificial intelligence involving data analysis and automatic analytical model building. Core ML is a framework built by Apple and was launched a couple of months ago. It supports features such as face tracking, face detection, landmarks, text detection, rectangle detection, bar code detection, object tracking, and image recognition.

## **Core ML Model**

Core ML supports a variety of machine learning models and this includes neural networks, tree ensembles, support vector machines, and generalized linear models. Core ML requires the Core ML model format (models with a _.mlmodel_ file extension). Apple and Google provide many Core ML models that can be downloaded easily and be used in applications. Additionally, various research groups and universities publish their models and training data, which may not be in the Core ML model format. To use these models, you need to convert them into Core ML format (through Keras and Caffe).

Let's now look into how the application is built.

### **Building the Application for LPR**

Now that you are aware of the key concepts used for bringing about this application, let's now delve into how this all began. We started by looking at various frameworks that use neural networks for image recognition in iOS. The prominent ones we found were Tesseract and SwiftOCR.

We used both the frameworks one by one. While the Tesseract framework consumed considerable time for the setup, the SwiftOCR was relatively faster; however, the latter lacked in terms of accuracy. We then realized the need for a framework that could offer better accuracy without consuming too much memory. We then identified Apple's recently launched Vision framework for face recognition, text, barcodes, QR codes, etc.

### **About Vision Framework**

It gives you easy access to Apple's models for detecting faces, face landmarks, text, rectangles, barcodes, and objects:

![](https://www.netsolutions.com/insights/wp-content/uploads/2018/03/image-1.png)

Its key features include the following:

  1. Detects face rectangles and face landmarks.
  2. Finds projected rectangular region surfaces.
  3. Finds and recognizes barcodes.
  4. Finds regions of visible text.
  5. Determines the horizon angle in an image.
  6. Detects transforms needed to align the content of two images.
  7. Processes images with Core ML model.
  8. Track movements of a previously identified arbitrary object across multiple images or video frames.

### **Using Vision Framework**

We performed two functions using the vision framework -- finding regions of visible text to split the word image into characters and process images with core ML model. So, let's learn how to cut the images with vision `VNDetectTextRectanglesRequest`.

Here, through vision, we detected the characters but could not recognize them. For recognition, we need the core ML trained model as shown below:

### ![](https://www.netsolutions.com/insights/wp-content/uploads/2018/03/image-2.png)

**Creating the Core ML Model**

We first looked for the Core ML model, which could recognize the license plate. However, we ended up with a model that could only recognize the text and not the entire license plate. We then decided to train the model through Keras, which is an open-source neural network library written in Python. It is designed to enable fast experimentation with deep neural networks.

We decided to build the model in Python and added the following frameworks:

![](https://www.netsolutions.com/insights/wp-content/uploads/2018/03/image-4.png)

> _Keras to create the model from the dataset._

  1. Image to fetch the pixels of the character image.
  2. Numpy for a high-performance multidimensional array object.
  3. Core ML tools to convert into ML model.
  4. sklearn for splitting the dataset for training and testing.

### **The Process**

Now, we needed the data (images of characters 28*28), which had to be trained. We collected the data from the web and clicked 40-50 images of number plates. We sliced the characters and then converted it to 28*28 resolution from one number plate image. Hence, we decided to make this automated by creating an app in iOS and generated thousands of character images with the help of vision framework.

Some takeaways for the conversion flow:

  1. Train model in your favorite framework.
  2. Convert the model to _.mlmodel_ using the coremltools Python package.
  3. Use the model in your app.

## ![](https://www.netsolutions.com/insights/wp-content/uploads/2018/03/image-5.png)

**Some Critical Use Cases for License Plate Recognition**

### **Check on Authenticity of Abandoned Vehicles**

This feature can be leveraged for law enforcement purposes. Here, the application can enable police to quickly check the authenticity of number plates installed on abandoned vehicles via mobile devices. Hence, this can curb illegal acts/anti-social elements. An additional camera can focus on the driver's face and save the image for future security tests. Additionally, this technology does not need separate installations for each vehicle, unlike other technologies that install a transmitter for each vehicle.

### **Automation of Electronic Toll Collection**

LPR can be used for automating the regulated entry of vehicles through toll barriers. It couples with access control system to recognize number plates listed in the toll collection database. The barrier would open only for those vehicles that are recognized at the electronic toll collection point as shown in the below image:

The blue rays read the license number plate and match it with the database of registered number plates.

### ![](https://www.netsolutions.com/insights/wp-content/uploads/2018/03/image-6.jpg)

> _LPR Devices That Are Available as Hardware_

There are different types of devices available in the market to recognize the number plate. For instance, CARMEN Parking is a cost-effective solution used for vehicle entry. CARMEN FreeFlow is a device used for recognition of fast-moving vehicles. Some other examples include:

  * Dongles for various SW versions: USB, PCIe, FXVD4 card, single or multi-license, the FXVD4mc_s video capture card.
  * Connecting any analog camera to the system, the FXCAMd 102 digital ANPR camera with motorized optics for easy installation and ideal image quality, the FXCAM IBW_2000 ANPR camera.
  * A plug-and-play pre-set solution for the optimal image and the smart ANPR camera, the all-in-one unit, integrated ANPR in the camera.

On the downside, the above hardware devices come with a hefty price, as they require setup. Another limitation is the size and portability of the devices as the setup consumes a considerable amount of time.

### **Mobile Can Help Overcome the Limitation of LPR Devices**

Machine learning brings a set of advantages that surpasses all its limitations. This solution is not only cost-effective but also quick and needs no installation. Since this application runs on your mobile phone, it comes in handy, too. Our first account with ML and mobile yielded tremendous responses and we are in a process to add some more use cases of machine learning to our list. Stay tuned for more on this.

[TrueSight is an AIOps platform](https://dzone.com/go?i=247359&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html), powered by machine learning and analytics, that elevates IT operations to address multi-cloud complexity and the speed of digital transformation.
